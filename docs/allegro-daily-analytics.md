# Allegro Daily Analytics

**Version:** 1.0.0  
**Owner:** Salvexis OÜ  
**Platform:** Allegro REST API

## Purpose

Allegro Daily Analytics is an internal application for Salvexis OÜ's own Allegro seller account. It is being developed to automate daily sales and profitability reporting by combining Allegro data with internal product cost information. It is not a SaaS product or a service for other sellers.

## Data Sources

The planned integration covers the following categories, subject to API availability and granted access:

- **Orders:** orders, line items, quantities, statuses and sales values.
- **Offers:** Offer IDs, seller SKUs where available, and offer information.
- **Billing and fees:** billing entries, Allegro commissions, fees and adjustments.
- **Payments:** payment records and refunds where available.
- **Shipments:** shipment information and available delivery cost data.
- **One Fulfillment:** available fulfillment information and inventory balances.
- **Messages and disputes:** buyer messages, Discussions and related support cases.
- **Advertising:** advertising-related information and spend when accessible through eligible APIs; this is an optional source.

An internal product cost reference will provide cost of goods sold (COGS).

## Reporting Workflow

1. Retrieve new and updated orders and their line items.
2. Retrieve billing, payment, refund and available fulfillment information.
3. Match transactions with offers, SKUs and internal product cost data.
4. Calculate sales, fees, costs and estimated profitability.
5. Export daily reporting data to internal tools such as Google Sheets.
6. Track profitability over time and reconcile later adjustments.

Planned metrics include orders, units sold, revenue, VAT, Allegro fees, fulfillment and shipping costs, advertising spend, refunds, product COGS, estimated profit and profit margin.

Calculations depend on available source data and configured cost and tax inputs. Sales, payments and fee entries represent different events and must be reconciled without double counting. Currency conversion and reporting dates must be defined explicitly.

## Customer Service Automation

A future AI-assisted workflow may analyze buyer messages, retrieve order context, prepare suggested responses and support internal customer service work. Responses are intended for human review; autonomous sending is not part of the initial implementation.

## Authentication

The registered application uses OAuth 2.0 through Allegro's **Device Flow** (`device_code`). The account owner authorizes access through Allegro, and the application can access only resources allowed by its effective scopes.

The initial design focuses on read operations. Dedicated write scopes are not prerequisites for the core reporting workflow. Some messaging and dispute scopes cover both reading and modifying data; the initial workflow is limited to reading and drafting.

API requests will include the User-Agent generated in Allegro Developer Apps, using this page as the documentation URL.

## Security

- Client credentials, including Client Secret, are not stored in this public repository.
- Access tokens and refresh tokens are never published.
- No real buyer data, order identifiers, customer contact details, banking data or internal financial records are published on GitHub.
- This repository contains only public application documentation. Runtime credentials and operational data must be stored separately with restricted access.

## Status

**Internal application under active development.**

The capabilities above describe the planned integration. Production authorization, collection, reporting and customer service automation are not yet operational.

## References

- [Allegro API basics and User-Agent requirements](https://developer.allegro.pl/tutorials/informacje-podstawowe-b21569boAI1)
- [Allegro OAuth and API scopes](https://developer.allegro.pl/tutorials/uwierzytelnianie-i-autoryzacja-zlq9e75GdIR)
- [Allegro REST API reference](https://developer.allegro.pl/documentation)
