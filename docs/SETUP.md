# Connection Guide

## 1. Generate the User-Agent

Open the [Allegro User-Agent generator](https://apps.developer.allegro.pl/user-agent) and enter:

| Field | Value |
| --- | --- |
| Application (`Wybierz aplikację`) | Allegro Daily Analytics |
| Application version (`Wersja aplikacji`) | `1.0.0` |
| Documentation URL (`URL dokumentacji`) | The public URL below |

[https://github.com/trs0793/allegro-daily-analytics/blob/main/docs/allegro-daily-analytics.md](https://github.com/trs0793/allegro-daily-analytics/blob/main/docs/allegro-daily-analytics.md)

Click **GENERUJ USER-AGENT** and retain the complete result. Configure API requests to use the generated value as the `User-Agent` header. Do not invent or manually rewrite the generated identifier.

Use this canonical URL when generating the identifier for the first time. If a User-Agent was already generated with the earlier documentation URL, retain it until any required change is confirmed with Allegro. The earlier page remains available and points to this documentation.

## 2. Authorize the Seller Account

The application is registered for **OAuth 2.0 Device Flow** (`device_code`).

During implementation, the account owner will approve access using Allegro's verification page and a device authorization code. The integration must follow the polling interval returned by Allegro and handle approval, denial and expiry. A redirect callback is not needed for this flow.

Client credentials must be configured outside this public repository. Access and refresh tokens must remain in restricted runtime storage and must not be printed in public logs.

The first connection check will use `GET /me`, followed by checks for the specific order and billing resources. Profile access alone does not verify access to every planned data source.

### Planned Access

The selected or planned scopes from the project specification are:

```text
allegro:api:sale:offers:read
allegro:api:orders:read
allegro:api:billing:read
allegro:api:payments:read
allegro:api:profile:read
allegro:api:fulfillment:read
allegro:api:shipments:read
allegro:api:messaging
allegro:api:disputes
```

Verify the actual app configuration and each endpoint's current requirements before implementation. This list does not certify that all scopes have been granted or that every endpoint is available to the account.

Messaging and dispute permissions may combine read and write operations. The initial application must use them only for reading and preparing drafts. Advertising access is optional and must be verified separately; the reporting design does not depend on the `allegro:api:ads` scope.

## 3. Verify the First Data Import

Before scheduling collection:

1. Confirm the authorized seller account and effective permissions.
2. Retrieve a limited period of orders, billing and payments, processing all response pages.
3. Record stable identifiers and update timestamps.
4. Repeat the import to verify that it does not create duplicates and captures changes.
5. Reconcile results with the seller account, including refunds and corrections.
6. Apply a defined reporting date and currency policy.

The planned reporting timezone is `Europe/Warsaw`. Keep sales, payments and fees separate until reconciled. Product costs and tax inputs must be configured before reporting estimated profitability.

## 4. Connect Internal Reporting

After the first import is verified, select the runtime and private data storage, connect the internal product cost reference and authorize the intended Google Sheets destination. Define token renewal, update scheduling and error notifications.

No production data import, Google Sheets connection or recurring job is configured by this documentation.

## References

- [User-Agent requirements](https://developer.allegro.pl/tutorials/informacje-podstawowe-b21569boAI1)
- [OAuth Device Flow and scopes](https://developer.allegro.pl/tutorials/uwierzytelnianie-i-autoryzacja-zlq9e75GdIR)
- [REST API reference](https://developer.allegro.pl/documentation)
