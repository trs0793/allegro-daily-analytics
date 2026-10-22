# Allegro Daily Analytics

Public documentation for Salvexis OÜ's internal Allegro analytics application.

| | |
| --- | --- |
| Version | 1.0.0 |
| Owner | Salvexis OÜ |
| Platform | Allegro REST API |
| Authentication | OAuth 2.0 Device Flow |
| Status | Internal application under active development |

## Documentation

- [Application documentation](docs/allegro-daily-analytics.md) — purpose, data sources, reporting workflow and security.
- [Connection guide](docs/SETUP.md) — User-Agent configuration and the next integration steps.

Use the following public page in Allegro Developer Apps as **URL dokumentacji**:

[https://github.com/trs0793/allegro-daily-analytics/blob/main/docs/allegro-daily-analytics.md](https://github.com/trs0793/allegro-daily-analytics/blob/main/docs/allegro-daily-analytics.md)

## Project Scope

The planned integration will combine orders, offers, billing, payments and available fulfillment data with internal product costs to support daily profitability reporting in Google Sheets. A later customer service workflow may analyze buyer messages and prepare suggested responses for human review.

The first implementation is intended for read operations. Advertising information is an optional source, subject to API availability and access.

## Current State

This repository contains public documentation only. OAuth authorization, production data collection, calculations and scheduled reporting still require implementation and verification.

Credentials, tokens, customer records and internal financial data must remain outside this public repository.
