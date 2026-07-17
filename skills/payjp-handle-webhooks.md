---
name: Receive and verify PAY.JP webhooks
description: Register a webhook endpoint, verify the token, and reconcile events via the Events API.
api: openapi/payjp-openapi.yml
operations: [listEvents, retrieveEvent]
---

# Receive and verify PAY.JP webhooks

Use this to react asynchronously to charge, customer, subscription, and transfer changes.

## Setup
- Register your HTTPS endpoint URL in the PAY.JP dashboard (console.pay.jp).
- PAY.JP POSTs a JSON **Event object** (`{id, object:"event", type, created, livemode, pending_webhooks, data}`).

## Verify every request
1. Read the **`X-Payjp-Webhook-Token`** header and confirm it equals the webhook token configured for your account. Reject if it does not match.
2. Optionally re-fetch the event server-side with `retrieveEvent` (`GET /events/{id}`) to confirm authenticity and get the canonical payload before acting.
3. Respond **HTTP 200** (empty body is fine). Non-2xx responses are retried every 3 minutes, up to 3 times.

## Reconcile / backfill
- List missed events with `listEvents` (`GET /events`) using offset pagination (`limit`, `offset`, `since`, `until`; reverse-chronological).

## Event types (see asyncapi/payjp-webhooks.yml)
`charge.succeeded|failed|updated|refunded|captured`, `token.create`,
`customer.created|updated|deleted`, `customer.card.created|updated|deleted`,
`plan.created|updated|deleted`,
`subscription.created|updated|deleted|paused|resumed|canceled|renewed`,
`transfer.succeeded`.

## Rules
- Check `livemode` to route test vs. production events.
- Webhook delivery is at-least-once — dedup on the event `id`.
