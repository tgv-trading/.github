# Security Policy

Terminal Gravity contains broker-connected trading infrastructure. Treat vulnerabilities involving credentials, account data, execution authority, Risk Gate decisions, release admission, or evidence integrity as sensitive.

## Reporting a vulnerability

Use GitHub's **Report a vulnerability** / private security advisory feature on the affected repository. Do not open a public issue containing:

- API keys, tokens, cookies, SSH material, broker credentials, or account identifiers;
- order, fill, position, or private market-data exports;
- exploitable release, webhook, gateway, or network details;
- instructions that could bypass the Risk Gate, account boundaries, or kill switches.

Include the affected repository and revision, impact, safe reproduction steps, and a proposed mitigation if known. Use synthetic data and redacted logs.

## Response expectations

Maintainers will first contain credential, capital, and execution risk; then reproduce, patch, test, and document the issue. Reports may require coordinated disclosure until affected services and credentials are secured.

## Supported versions

The default branch and explicitly deployed revisions are supported. Historical branches, archived repositories, and unmerged review worktrees are not supported unless a maintainer states otherwise.

## Safety boundary

Security testing must not place orders, connect to unauthorized accounts, mutate production data, weaken fail-closed controls, or probe third-party systems without authorization.
