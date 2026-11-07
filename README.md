# AlgonikHQ — Crypto Research (public log)

Building in public: what we test, how we test it, and honest results, losses included.
Code, exact rules and thresholds stay private. Nothing here is advice or a signal.
Read the [terms and disclaimer](DISCLAIMER.md) first.

## What is being researched

| Track | What | Stage |
|---|---|---|
| A | New-launch meme coins (Solana; Base paused) | Shadow logging only: safety checks within minutes of launch, live cost quotes, 2-hour outcomes valued by real sell quotes. Stop rule set in advance (see log). No trades. |
| B | Stablecoins | Depeg watch (an alert needs two venues to agree) and real order-book gaps between 5 exchanges after fees, every 10 minutes. No trades. |
| C | Established meme coins | Backtest with real costs done: the one surviving idea (buying sharp dips) failed the robustness check. Closed; the locked final data was never used. No trades. |

## Standards (same as the AlgonikHQ forex research)

1. Rules are written down before any test runs, and do not change once a test starts.
2. Every result is net of real costs: exchange and pool fees, priority fees, slippage, failed transactions.
3. Every idea must beat random entries, its own opposite, and simply holding.
4. The newest data is locked away and only opened once, at the end.
5. Forward paper testing comes before any real money.
6. Results are published as a percentage of position size. Losses are published too.

## Contents

- [DISCLAIMER.md](DISCLAIMER.md) — terms, risks and what this repository is not
- [LOG.md](LOG.md) — dated research log
- [audit/2026-11-old-bots.md](audit/2026-11-old-bots.md) — honest review of the retired 2026 bots

Follow along: [@AlgonikHQ on X](https://x.com/AlgonikHQ) · alerts channel: [t.me/SloanaSniper_Alerts](https://t.me/SloanaSniper_Alerts)
