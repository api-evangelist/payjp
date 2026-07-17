---
name: Create a customer, plan, and subscription
description: Store a card on a customer and start recurring billing (定期課金) on a plan with PAY.JP.
api: openapi/payjp-openapi.yml
operations: [createToken, createCustomer, createCustomerCard, createPlan, createSubscription, cancelSubscription]
---

# Create a customer, plan, and subscription (PAY.JP)

Use this to bill a customer on a recurring interval (定期課金 / teiki kakin).

## Auth
HTTP Basic with the **secret key** (`sk_test_` / `sk_live_`) as username, empty password. JPY only.

## Steps
1. Tokenize the card client-side (`createToken`) to get a `tok_...`.
2. `createCustomer` (`POST /customers`) with `card=<token id>` and optional `email`, `description`. The token is consumed and stored as the customer's default card. (Add more cards later with `createCustomerCard`, `POST /customers/{id}/cards`.)
3. `createPlan` (`POST /plans`) with `amount`, `currency=jpy`, `interval` (e.g. `month`), optional `trial_days`, `billing_day`. Reuse an existing plan id if you already have one.
4. `createSubscription` (`POST /subscriptions`) with `customer=<cus_ id>` and `plan=<pln_ id>`. Billing starts (or after the trial).
5. To stop billing, `cancelSubscription` (`POST /subscriptions/{id}/cancel`) — or `pauseSubscription` / `resumeSubscription` to hold and restart.

## Rules
- One customer + one plan → `already_subscribed` if you re-subscribe the same pair.
- Deleting a plan with active subscribers returns `exist_subscribers`.
- Renewals emit the `subscription.renewed` webhook event (see `asyncapi/payjp-webhooks.yml`) — reconcile against it rather than polling.
- No Idempotency-Key header; metadata is capped at 20 keys / 500 chars per value.
