# Security

This is a development prototype. Do not submit real passenger details, payment information, credentials, database exports or private logs to public issues or pull requests.

- Keep credentials in local environment files or the deployment platform's secret store.
- Use dedicated sandbox/test provider accounts for development.
- Never commit `.env` files, private keys, local databases or personal data.
- Revoke or rotate exposed credentials at their provider. File deletion and Git history rewriting do not revoke a key.
- Review automation source and permissions before enabling it. External uploads from CI need a documented purpose and destination.

Use GitHub's private vulnerability reporting feature if enabled. Otherwise contact the repository owner privately through an existing trusted channel. Public reports should contain no credentials, personal data or exploitable production details.

No production security audit or compliance certification is claimed.
