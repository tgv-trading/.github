<div align="center">

```text
████████╗███████╗██████╗ ███╗   ███╗██╗███╗   ██╗ █████╗ ██╗
╚══██╔══╝██╔════╝██╔══██╗████╗ ████║██║████╗  ██║██╔══██╗██║
   ██║   █████╗  ██████╔╝██╔████╔██║██║██╔██╗ ██║███████║██║
   ██║   ██╔══╝  ██╔══██╗██║╚██╔╝██║██║██║╚██╗██║██╔══██║██║
   ██║   ███████╗██║  ██║██║ ╚═╝ ██║██║██║ ╚████║██║  ██║███████╗
   ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚══════╝

       ██████╗ ██████╗  █████╗ ██╗   ██╗██╗████████╗██╗   ██╗
      ██╔════╝ ██╔══██╗██╔══██╗██║   ██║██║╚══██╔══╝╚██╗ ██╔╝
      ██║  ███╗██████╔╝███████║██║   ██║██║   ██║    ╚████╔╝
      ██║   ██║██╔══██╗██╔══██║╚██╗ ██╔╝██║   ██║     ╚██╔╝
      ╚██████╔╝██║  ██║██║  ██║ ╚████╔╝ ██║   ██║      ██║
       ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝  ╚═══╝  ╚═╝   ╚═╝      ╚═╝
```

**Broker-truth trading infrastructure for 0DTE research, Risk Gate execution, and evidence-led learning.**

[![Platform](https://img.shields.io/badge/platform-Terminal%20Gravity-7c3aed?style=for-the-badge)](https://github.com/tgv-trading)
[![Safety](https://img.shields.io/badge/safety-Risk%20Gate%20first-0f766e?style=for-the-badge)](#operating-law)
[![Truth](https://img.shields.io/badge/truth-broker--confirmed%20fills-f59e0b?style=for-the-badge)](#operating-law)

</div>

---

```text
terminalgravity@tgv-trading
──────────────────────────────────────────────────────────────────────────────
Mission .......... Build a simple, testable 0DTE profit engine for SPX/SPY/QQQ
Loop ............. data → signal → same-contract replay → score → Risk Gate →
                   approved execution path → broker-confirmed reconciliation → learn
Venues ........... IBKR Paper | IBKR Live | Simulator
Execution truth .. broker-confirmed fills only
Safety kernel .... Risk Gate, kill switches, freshness checks, account boundaries
Operator UI ...... Market Terminal, Strategy Runner, Manual Trade Briefs
Primary runtime .. IBKR Trading System + Terminal Gravity service spine
```

## Build spine

Terminal Gravity is being split into focused service lines so each part of the trading loop can be tested, audited, and deployed without blurring broker authority or evidence provenance.

| Service line | Responsibility |
| --- | --- |
| [`ibkr-trading-system`](https://github.com/tgv-trading/ibkr-trading-system) | Current IBKR runtime shell, operator dashboard, backend integration, deployment glue |
| [`tg-service-spine`](https://github.com/tgv-trading/tg-service-spine) | Cross-service readiness, shared contracts, migration control plane |
| [`tg-market-data`](https://github.com/tgv-trading/tg-market-data) | Market data capture, option chains, quote/candle contracts, same-contract replay seeds |
| [`tg-strategy-research`](https://github.com/tgv-trading/tg-strategy-research) | Signals, replay/backtest, scoring, Manual Trade Brief draft logic, learning candidates |
| [`tg-risk-execution`](https://github.com/tgv-trading/tg-risk-execution) | Risk Gate contracts, sizing policy, approval/block explanations, execution-path interfaces |
| [`tg-journal-ledger`](https://github.com/tgv-trading/tg-journal-ledger) | Broker-confirmed fills, reconciliation, evidence ledgers, P&L truth projection |
| [`tg-api-gateway`](https://github.com/tgv-trading/tg-api-gateway) | Read-only operator fan-in, readiness aggregation, product/API composition |

## Operating law

- Protect capital and broker access first.
- IBKR Paper, IBKR Live, and Simulator evidence stay separate.
- Broker-confirmed fills are execution truth.
- Synthetic, demo, pending, accepted-only, dirty, audit-only, or reconciled-only rows are not performance truth.
- Strategy logic proposes; the Risk Gate approves or blocks; broker execution must reconcile back to evidence.
- No live trading behavior changes, broker routing changes, credential changes, or Risk Gate weakening without explicit approval.

## Product surfaces

```text
Market Terminal      read-only market, signal, levels, and readiness surface
Strategy Runner      governed automation controller with Risk Gate boundaries
Manual Trade Brief   human-reviewed trade thesis/action-plan artifact
Account Model        product/model layer for simulated or governed strategies
Execution Journal    broker-confirmed lifecycle records and reconciliation truth
Evidence Ledger      source-labeled evidence with freshness and provenance
Readiness Monitor    paper/live operational status, blockers, and deployment evidence
```

## Near-term focus

1. Capture clean SPX/SPY/QQQ same-contract 0DTE data.
2. Replay candidate signals against the exact contract that would have been traded.
3. Score only with source-labeled, freshness-aware evidence.
4. Keep the Risk Gate fail-closed until sizing, duplicate checks, session limits, and kill switches prove safe.
5. Reconcile every approved execution path against broker-confirmed fills before learning from it.

---

<div align="center">

**Terminal Gravity is not a signal chatroom. It is the system that proves what can safely trade.**

</div>
