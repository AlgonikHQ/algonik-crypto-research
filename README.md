# AlgonikHQ — Crypto Research (public log)

Building in public: what we test, how we test it, and honest results, losses included.
Code, exact rules and thresholds stay private. Nothing here is advice or a signal.
Read the [terms and disclaimer](DISCLAIMER.md) first.

## What is being researched

| Track | What | Stage |
|---|---|---|
| A | New-launch meme coins (Solana; Base paused 7 Nov) | **Retired 10 Nov 2026 by its pre-set stop rule** (see log). Follow-up study (6 rules, set in advance) closed 21 Nov: all lost money after costs. The logger keeps recording Solana as a dataset. No trades. |
| B | Stablecoins | Depeg watch stays on (an alert needs two sources to agree). Order-book gap trade **closed 21 Nov 2026**: 0 of 2,028 readings profitable after fees. No trades. |
| C | Established meme coins | Backtest with real costs done: the one surviving idea (buying sharp dips) failed the robustness check. Closed; the locked final data was never used. No trades. |
| D | BTC/ETH trend-following | 10 rules + 1 volatility-sized; one survived design, failed validation on 2023-2024. **Closed 21 Nov 2026.** No trades. |
| E | Funding rate as a spot signal (BTC/ETH) | 6 rules, none passed design (closest: BTC hold-while-funding-negative, failed Deflated Sharpe). **Closed 21 Nov 2026**; near-miss watched forward, recording only. |
| F | Solana meme coin momentum | 10 rules (momentum, breakout, rotation); all lost money, none beat random timing. **Closed 21 Nov 2026.** No trades. |

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
