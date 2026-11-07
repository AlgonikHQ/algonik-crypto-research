# Research log

Newest first. Figures are percentages of position size. No trades are being placed.

## 4 Nov 2026

- **Plan signed off.** Three tracks (new-launch meme coins, stablecoins, established meme coins), rules written before testing, go-live bar fixed in advance.
- **Audit of the 2026 bots published:** [audit/2026-11-old-bots.md](audit/2026-11-old-bots.md).
- **Track A shadow logger started.** Records every new pool on Solana and Base, runs safety checks, takes live buy-and-sell quotes, and tracks each token for two hours. It never trades.
- **First cost readings** on brand-new Solana pools (quote-only round trips, before network fees, first 11 tokens): £10 about 3.1%, £20 about 3.7%, £50 about 5.4%. Small sample; costs on new pools are higher than expected.
- **Track B stablecoin watch started.** First reading: all major stablecoins within 0.15% of $1, and the same small USDC/USDT difference on every venue, so no gap worth trading.
- **Track C test harness built and checked.** On random price data it found nothing; on data with a deliberately planted pattern it found the pattern; it refused to credit an idea that only rode a rising market. Real history is downloading.

## 7 November 2026 - We caught a flaw in our own process, and the first honest results

**Track A (new launches): a flaw found and fixed before any numbers were published.**
Our safety checker had been falling behind. By 6 November it was checking tokens a median of 31 hours after
launch. Tokens that had already collapsed failed the check, which made our filter look far better than it was.
None of those numbers were published here. That data is set aside and labelled. Reporting restarted on
6 November at 21:30 UTC, with checks made within minutes of launch and an automatic guard that refuses any
result where a check came too late or used information from after the moment a bot could have bought.

First clean results (about 5 hours of data, to 02:55 UTC on 7 November):
- Tokens that passed our safety filter: 27.5% collapsed within 2 hours, against 61.7% of rejected tokens. None doubled.
- 19 passing tokens followed for 2 hours using real sell quotes: none reached 1.5x. A simulated exit
  lost 30% of the position on average (median -11.6%), before network fees. Small sample.

**Stop rule, fixed today before any more data:** at 300 followed tokens, this idea is retired if the
average simulated result after costs is 0% or worse, or if fewer than 5% of tokens reach 1.5x.

**Track C (established meme coins): closed.**
Buying sharp dips was the only one of 24 ideas to survive the first backtest. After correcting for having
tried 24 ideas (a Deflated Sharpe test), the best version scored 61% against a 95% pass mark set before the
test ran. Its 73 trades fell on only 39 separate days, because crashes hit many coins at once. That is too few
to tell skill from luck. The locked final slice of data was never opened.

**Track B (stablecoins): no edge so far.**
The coins held their pegs. On the first reading of five exchanges' order books, the best buy-here, sell-there
gap was -0.10% after fees. One reading proves nothing. A week of 10-minute readings will.
