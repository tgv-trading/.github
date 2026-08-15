# Contributing to Terminal Gravity

Terminal Gravity repositories are small, safety-conscious services. Keep changes scoped, reviewable, and backed by executable evidence.

## Before changing code

1. Read the repository's `AGENTS.md`, `README.md`, and build manifests.
2. Confirm the repository owns the capability being changed; do not add new service-spine logic to the legacy IBKR shell by default.
3. Identify the narrowest test or characterization check that protects existing behavior.
4. Keep credentials, account identifiers, broker exports, mutable databases, market-data archives, and machine-local configuration out of Git.

## Engineering standard

- Prefer clear domain names and cohesive modules over generic helpers or speculative abstractions.
- Preserve typed service contracts, source timestamps, provenance, venue boundaries, and broker-confirmed evidence semantics.
- Keep deterministic code authoritative for prices, signals, sizing, risk, orders, fills, limits, and reconciliation.
- Separate behavior changes from structural cleanup when practical.
- Add or update tests for behavior changes and consequential boundaries.
- Use repository-native formatters, linters, type checkers, tests, and builds.
- Document operational changes, migrations, compatibility constraints, and rollback requirements.

## Trading safety

- Paper, live, and simulator data must remain explicitly separated.
- Risk Gate and broker authority remain fail-closed.
- Never weaken freshness checks, duplicate protection, limits, kill switches, account boundaries, or reconciliation to make a test pass.
- Do not place orders or connect to a live broker as part of a development or CI check.
- Changes to live behavior, broker routing, credentials, permissions, or production deployment require explicit operator approval.

## Pull requests

Keep each pull request focused on one coherent outcome. Include:

- the problem and ownership boundary;
- the behavior before and after;
- safety and data-integrity impact;
- exact verification commands and results;
- migration, deployment, and rollback notes when applicable;
- screenshots for operator-facing UI changes.

A cleanup is complete only when relevant checks pass and the diff is easier for the next engineer to understand.
