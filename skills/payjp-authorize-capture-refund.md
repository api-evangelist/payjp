---
name: Authorize, capture, and refund a charge
description: Run a two-step (auth then capture) payment and issue full or partial refunds with PAY.JP.
api: openapi/payjp-openapi.yml
operations: [createCharge, captureCharge, reauthCharge, retrieveCharge, refundCharge]
---

# Authorize, capture, and refund a charge (PAY.JP)

Use this for delayed capture (auth now, capture on fulfilment) and refunds.

## Auth
HTTP Basic with the **secret key** as username, empty password. JPY only.

## Authorize then capture
1. `createCharge` (`POST /charges`) with `card=<token>` (or `customer=<cus_ id>`), `amount`, `currency=jpy`, and **`capture=false`** to authorize only.
2. Fulfil the order, then `captureCharge` (`POST /charges/{id}/capture`) — optionally with a smaller `amount` to capture partially.
3. If the authorization hold is about to expire, `reauthCharge` (`POST /charges/{id}/reauth`) re-authorizes it. An expired hold returns `charge_expired`.

## Refund
1. `retrieveCharge` (`GET /charges/{id}`) to confirm it is `captured` and how much is refundable.
2. `refundCharge` (`POST /charges/{id}/refund`) with optional `amount` (partial) and `refund_reason`.

## Rules
- Refunds after 180 days return `refund_limit_exceeded`.
- `already_refunded` / `already_captured` guard duplicate operations — check state first.
- You cannot capture or re-auth a refunded charge (`cant_capture_refunded_charge`, `cant_reauth_refunded_charge`).
- Refunds emit `charge.refunded`; captures emit `charge.captured` (see `asyncapi/payjp-webhooks.yml`).
