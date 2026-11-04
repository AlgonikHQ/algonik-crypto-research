# Research log

Newest first. Figures are percentages of position size. No trades are being placed.

## 4 Nov 2026

- **Plan signed off.** Three tracks (new-launch meme coins, stablecoins, established meme coins), rules written before testing, go-live bar fixed in advance.
- **Audit of the 2026 bots published:** [audit/2026-11-old-bots.md](audit/2026-11-old-bots.md).
- **Track A shadow logger started.** Records every new pool on Solana and Base, runs safety checks, takes live buy-and-sell quotes, and tracks each token for two hours. It never trades.
- **First cost readings** on brand-new Solana pools (quote-only round trips, before network fees, first 11 tokens): £10 about 3.1%, £20 about 3.7%, £50 about 5.4%. Small sample; costs on new pools are higher than expected.
- **Track B stablecoin watch started.** First reading: all major stablecoins within 0.15% of $1, and the same small USDC/USDT difference on every venue, so no gap worth trading.
- **Track C test harness built and checked.** On random price data it found nothing; on data with a deliberately planted pattern it found the pattern; it refused to credit an idea that only rode a rising market. Real history is downloading.
