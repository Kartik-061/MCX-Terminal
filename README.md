# MCX Terminal

Forward paper-trading incubation of an intraday opening-range breakout on MCX Crude Oil and Natural Gas.

> **Status:** paper trading only; no real capital is connected. The edge is **unproven**: the backtest (108 trades over 128 sessions) has t = 1.42, and its parameters were tuned on the same sample. Not investment advice.

## Forward record

Incubation started 2026-11-09 with Rs 9,00,000 nominal capital. As of 2026-11-12: 5 trades, all stop-outs, NAV -2.09%. The pre-defined review point is 100 forward trades.

## Open issues (not yet resolved)

1. On 2026-11-12 the five-consecutive-loss threshold in the stop rules was reached. The manual review is not yet documented.
2. On 2026-11-12 a loop-variable leakage bug was patched while the system was running. The earlier days' records have not yet been re-checked against the fix.
3. On 2026-11-16 the runner started at 23:31 IST, after the session cutoff, so that day produced no trades. The cause is under investigation.

## Contents

- `MCX_TERMINAL_REPORT.md`: strategy rules, cost model, audit of the backtest, and the forward trade ledger. Live broker code is not published.