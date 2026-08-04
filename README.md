# PAY.JP (payjp)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

PAY.JP is an online payment service operated by PAY, Inc. (PAY株式会社) in Japan. Its Stripe-style REST API lets merchants create charges, tokenize cards, manage customers, run subscriptions (定期課金), and settle transfers (入金) in Japanese yen, with a Platform API (beta) for marketplace/multi-tenant payouts.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/payjp/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/payjp/refs/heads/main/apis.yml)

## Tags

- Payments
- FinTech
- Japan
- Credit Cards
- Subscriptions
- Tokenization

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### PAY.JP Charges API

Create, retrieve, list, update, capture, re-authorize, and refund one-time and subscription charges in JPY, including two-step (auth/capture) and 3D Secure (tds_finish) flows.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Charges
- Payments
- Refunds

#### Properties

- [Documentation](https://pay.jp/docs/charge)
- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Customers API

Create, retrieve, list, update, and delete customer records that store tokenized cards for recurring and one-click billing.

- **Human URL:** [https://docs.pay.jp/v1/customer](https://docs.pay.jp/v1/customer)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Customers
- Billing

#### Properties

- [Documentation](https://docs.pay.jp/v1/customer)
- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Cards API

Attach, list, retrieve, update, and delete stored credit cards on a customer, keeping raw PANs out of the merchant environment.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Cards
- Vault

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Tokens API

Single-use card tokens created with the publishable key (typically via payjp.js / Checkout) and exchanged server-side for charges or customer cards, with a tds_finish step for 3D Secure.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Tokens
- Tokenization
- Client Side

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Plans API

Define recurring billing plans (amount, currency, interval, trial, billing day) that subscriptions attach to.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Plans
- Recurring

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Subscriptions API

Recurring billing (定期課金 / teiki kakin) that links a customer to a plan, with pause, resume, cancel, update, and delete lifecycle operations.

- **Human URL:** [https://docs.pay.jp/v1/subscription](https://docs.pay.jp/v1/subscription)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Subscriptions
- Teiki Kakin
- Recurring

#### Properties

- [Documentation](https://docs.pay.jp/v1/subscription)
- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Transfers API

Read-only access to payouts (入金 / nyukin) settled to the merchant bank account, including per-transfer charge details.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Transfers
- Nyukin
- Payouts

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Statements & Balances API

Transaction statements (取引明細), aggregation terms (集計区間), and account balances (残高), with signed CSV download URLs for reconciliation.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Statements
- Balances
- Reporting

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Events & Webhooks API

List and retrieve system Event objects that back the webhook system, letting merchants react asynchronously to charge, customer, and subscription changes.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Events
- Webhooks

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP 3D Secure API

Create and inspect 3D Secure requests to add cardholder authentication (EMV 3DS) to charges and stored cards.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- 3D Secure
- EMV 3DS
- Authentication

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Platform API (Tenants)

Beta marketplace API to onboard and manage sub-merchant tenants and their transfers, enabling split payouts on a PAY.JP platform account.

- **Human URL:** [https://pay.jp/docs/platform-payment](https://pay.jp/docs/platform-payment)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Platform
- Marketplace
- Multi Tenant

#### Properties

- [Documentation](https://pay.jp/docs/platform-payment)
- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### PAY.JP Account API

Retrieve the authenticated merchant account, including merchant and customer sub-objects and API key metadata.

- **Human URL:** [https://docs.pay.jp/v1/api/](https://docs.pay.jp/v1/api/)
- **Base URL:** `https://api.pay.jp/v1`

#### Tags

- Account
- Merchant

#### Properties

- [API Reference](https://docs.pay.jp/v1/api/)
- [OpenAPI](openapi/payjp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/payjp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

## Common Properties

- [Authentication](authentication/payjp-authentication.yml)
- [Domain Security](security/payjp-domain-security.yml)
- [Trust Center](security/payjp-trust-center.yml)
- [Vulnerability Disclosure](security/payjp-vulnerability-disclosure.yml)
- [Agentic Access](agentic-access/payjp-agentic-access.yml)
- [GitHub Organization](https://github.com/payjp)
- [Website](https://pay.jp/)
- [Documentation](https://docs.pay.jp/v1/)
- [Plans](plans/payjp-plans-pricing.yml)
- [Rate Limits](rate-limits/payjp-rate-limits.yml)
- [Fin Ops](finops/payjp-finops.yml)
- [Blog](https://pay.jp/info)

## Authentication

PAY.JP uses HTTP Basic authentication: send your **secret key** (`sk_test_…` / `sk_live_…`) as the Basic username with an empty password. Client-side card tokenization (payjp.js / Checkout) uses the **publishable key** (`pk_test_…` / `pk_live_…`), which can only create tokens. The API is HTTPS-only, JPY-only, and returns HTTP 429 with an `over_capacity` error when per-second rate limits are exceeded.

## Notes

- **Operator:** PAY, Inc. (PAY株式会社), Japan.
- **No official OpenAPI:** PAY.JP publishes language SDKs (Ruby, PHP, Node, Python, Go, iOS, Android, Flutter, React Native) but no first-party OpenAPI/Swagger file; the OpenAPI here is modeled from the public REST reference.
- **No WebSocket API:** asynchronous notifications are delivered via outbound HTTP webhooks (Event objects), not WebSocket or SSE — see [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
