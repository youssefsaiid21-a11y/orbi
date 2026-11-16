# Contributing

Start with the README, architecture notes and relevant product-quality item. Keep changes focused and explain the problem, behavior change and validation in a pull request.

For code changes, run lint, TypeScript checks and relevant Vitest tests. Run browser tests for affected journeys when a suitable test environment is available. Do not claim checks passed if they were not run.

Do not use live flight/payment credentials for routine tests. Review booking, money movement, authentication and personal-data changes separately from cosmetic work. Use synthetic fixtures without real users, secrets or external-account data.

Preserve existing attribution and licensing. Third-party services and assets retain their respective terms.
