---
name: Tokenize a card and create a charge
description: Collect a card client-side into a single-use token, then charge it server-side in JPY with PAY.JP.
api: openapi/payjp-openapi.yml
operations: [createToken, createCharge, retrieveCharge]
---

# Tokenize a card and create a charge (PAY.JP)

Use this to accept a one-time payment without raw card numbers touching your server.

## Auth
- Server calls: HTTP Basic, **secret key** (`sk_test_` / `sk_live_`) as the username, empty password.
- Client tokenization: **publishable key** (`pk_test_` / `pk_live_`) via payjp.js / Checkout. Never send the secret key to the browser.
- Currency is **JPY only**; `amount` is a whole-yen integer.

## Steps
1. **Client-side** — collect the card with payjp.js or Checkout and create a single-use token (`createToken`, `POST /tokens`) using the publishable key. Send the returned `tok_...` id to your server. (In test mode use a card from `sandbox/payjp-sandbox.yml`, e.g. `4242424242424242`.)
2. **Server-side** — `createCharge` (`POST /charges`) with `card=<token id>`, `amount`, `currency=jpy`. To authorize only, set `capture=false` and capture later.
3. Confirm with `retrieveCharge` (`GET /charges/{id}`) — check `paid=true` and `captured`.

## Rules
- Tokens are single-use — reusing one returns `token_already_used`. Re-tokenize per charge, or attach the card to a customer (see the subscription skill) for repeat billing.
- There is **no Idempotency-Key header** (see `conventions/payjp-conventions.yml`) — guard against double-submit client-side.
- Card failures come back as HTTP 402 `card_error` with `error.code` (`card_declined`, `expired_card`, ...); see `errors/payjp-decline-codes.yml`.
- Respect rate limits (HTTP 429 `over_capacity`); test mode is 2 req/sec.
