# Architecture

The conversational interface is separated from provider adapters and server-side booking/payment operations.

## Search

The browser collects a trip request. Parsing produces structured search parameters; the UI can request confirmation before flight search. Duffel responses are normalized into application offer types. Start with `src/app/page.tsx`, `src/lib/parser` and `src/lib/duffel`.

## Booking and payments

Passenger information, payment intent creation, payment webhooks and flight-order handling are separate steps. These require careful retry, expiry and state-transition handling. A successful payment is not proof of a completed flight booking. Review `src/app/api`, the Prisma booking schema and the product-quality backlog together.

## Accounts and data

Prisma represents users, profiles, bookings, chat sessions, tracked searches and supporting records. PostgreSQL is the active target. A developer's local database is runtime state, not source code or a distributable demo dataset.

## Optional services

Adapters support email, SMS and WhatsApp. Redis rate limiting and observability integrations are separately configured. Secret keys belong in environment configuration and must stay server-side.

This overview describes repository structure, not deployment certification. Outstanding correctness and safety issues must be resolved before handling real passengers, live payments or flight orders.
