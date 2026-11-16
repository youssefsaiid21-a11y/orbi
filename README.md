# Orbi · Conversational Flight Search

A full-stack travel application that turns natural-language trip requests into structured flight-search results, with accounts, saved searches and a sandbox checkout flow.

**Status: development prototype.** Intended for code review and local development; production readiness and completed real-world bookings are not claimed.

## What to review

- **Search:** conversational input, structured trip parameters, clarification, Duffel search and normalized offers.
- **Booking boundaries:** offer selection, passenger details, Stripe payment intents, webhooks and booking-state handling.
- **Accounts:** authentication, profiles, recovery and multi-factor authentication support.
- **Background features:** tracked searches, price-drop checks and notification adapters.
- **Tests:** unit/API tests under `src/__tests__` and browser scenarios under `e2e`.

The project contains incomplete flows. Read the [product-quality backlog](docs/product-quality/README.md) before treating any integration as production-ready.

## Technology

| Layer | Implementation |
| --- | --- |
| Application | Next.js 16, React 19, TypeScript |
| Data | PostgreSQL, Prisma |
| Authentication | Auth.js / NextAuth |
| Flight search | Duffel |
| Search interpretation | OpenAI-compatible client configured for Zhipu |
| Checkout | Stripe |
| Testing | Vitest, Testing Library, Playwright |
| Optional services | Upstash Redis, Resend, Twilio, Sentry |

## Local setup

Prerequisites: Node.js 22, npm, a dedicated PostgreSQL development database, and your own development provider accounts for external integrations.

```sh
git clone https://github.com/youssefsaiid21-a11y/orbi.git
cd orbi
cp .env.example .env
# Edit .env with your local database URL and development settings.
npm ci
npx prisma migrate deploy
npm run dev
```

Open <http://localhost:3000>. Generate an authentication secret with `openssl rand -base64 32`. See `.env.example` for other settings. Migrations affect the configured database; use a dedicated local database.

Use sandbox/test credentials for flight and payment development. A sandbox is an external service, not an offline mock. Do not use live booking credentials during a code review.

## Validation

```sh
npm run lint
npx tsc --noEmit
npm test
npm run build
```

For browser tests, configure an appropriate test environment, run `npx playwright install chromium`, then `npm run test:e2e`. Integration/smoke tests may contact external services when credentials are supplied; keep those separate from an offline review.

## Repository map

```text
src/app/          Pages and API routes
src/components/   Search, offers, checkout and account UI
src/lib/          Provider adapters and shared services
src/__tests__/    Unit and API tests
prisma/          PostgreSQL schema and migrations
e2e/             Browser scenarios
docs/            Architecture and product-quality notes
scripts/         Local administration and integration checks
```

## Further reading

- [Architecture](docs/ARCHITECTURE.md)
- [Security](SECURITY.md)
- [Contributing](CONTRIBUTING.md)
- [Known product-quality work](docs/product-quality/README.md)

Live credentials, personal data and local databases do not belong in Git. Third-party assets and services retain their respective licensing and terms.
