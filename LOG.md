# Research log

Newest first. Figures are percentages of position size. No trades are being placed.

## 21 November 2026 (update) - Track A follow-up study closed: nothing to take forward

Rules for a follow-up study were written and committed before any test ran: pass bar, a budget of 20 rules, a date split and a locked final check. Design data only (6-14 November, 15,363 checked pools). The locked data was never opened.

- Six rules tested: take-profit at 2x on the most volatile pools; the same after surviving 30 minutes; take-profit on pump.fun pools; holding Raydium LaunchLab pools for 2 hours; buying any pool still alive at 30 minutes; buying our gate-passers at 30 minutes.
- All six lost money after costs, from -8.5% to -51.2% average per trade. Best: gate-passers bought at 30 minutes. Worst: the volatile pools, where 2x was hit 7-17% of the time and most of the rest went to zero.
- Filters cut losses: the calmer rules beat random picks by 20-30 points. But calm pools barely move, so they lose roughly the trading cost.
- The pattern: the pools most likely to double were also the most likely to collapse (94% on the most volatile flag). No feature in our data separated them.
- Two mistakes caught and logged on the way: a measure that skipped early-checked tokens, and a valuation bug where price glitches (single readings millions of times entry) made one rule look like a winner. Fixed conservatively before re-scoring.
- 14 of the 20 allowed rules left unused on purpose: more tries mostly raise the chance of a lucky fluke.

**Decision:** Track A is closed. The logger keeps running as a dataset.

## 21 November 2026 - Track A retired by its own stop rule

**Track A (new launches): retired.**
The stop rule fixed on 7 November was reached and judged on 10 November at 19:17 UTC. Verdict: retire.
The logger keeps recording as a dataset, but nothing built on this filter will go to paper or live trading.

What two weeks of clean data show (a typical 24 hours, to 20 November):
- About 18,300 new Solana pools, of which about 4,200 were safety-checked within minutes of launch.
- Tokens that passed our filter: 42.5% collapsed within 2 hours, against 78.7% of rejected tokens. The filter avoids disasters.
- But the median passing token was worth 0.61x after 2 hours, against 1.00x for rejected tokens. Rejected tokens
  touched 2x about twice as often (20.2% against 10.0%). That is peak price, which may not have been sellable.
- 108 passing tokens followed for 2 hours using real sell quotes: 10% reached 1.5x, 7% reached 2x.
  The simulated exit (half at 2x, 30% trailing stop) averaged -12.8% (median -6.2%, 9% winners), before network fees.
- Round-trip quote costs on passing tokens: £10 3.3%, £20 4.0%, £50 6.2%. Network fees were about 0.03% at £20.
  Costs rise with size, so trading bigger makes it worse.

**The lesson:** a good rug filter is not an entry signal. Ours removed the worst tokens, and the best ones with them.

**Base paused since 7 November** after about 3,600 pools. Solana only since then.

**Next:** an offline study on the data already collected: what separates rejected tokens that ran from those that
collapsed, entering 30-60 minutes after launch only if the pool survived, and simpler exits. Rules will be written
before the study runs, with the newest data held back for a single final check.

**Track B (stablecoins): no edge in the gap trade. The depeg watch stays on.**
- Order-book gaps: 2,028 readings at $1,000 and $10,000 between Kraken, Binance, OKX, Bybit and Coinbase since
  7 November. Not one showed a profit after taker fees, even with money already on both exchanges. Median best gap
  after fees -0.10%, best ever -0.083%. The buy-here, sell-there trade is closed.
- Peg watch, 17 days (about 4,850 readings per coin and source): USDC, USDT and USDe stayed within 0.25% of $1 on
  every source. DAI on Kraken moved more than 1% off 10 times while the wider DAI price never moved more than 0.2%:
  a thin market, not a depeg. This is why an alert needs two sources to agree. No alert fired.
- USDC traded at a steady premium over USDT of up to about 0.23%, the same on every venue, so nothing to arbitrage.
- Three single Jupiter round-trip quotes (USDC to USDT and back) came back above what went in, up to +0.84%. Each was
  one reading, back to normal five minutes later. Treated as quote glitches: a quote is not a fill, and nothing
  checking every five minutes could act on it.
- Jupiter rate-limited us about 60 times a day until 13 November, so it has about 540 fewer readings than other sources.

**Track C (established meme coins):** no change in this entry.

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

## 4 Nov 2026

- **Plan signed off.** Three tracks (new-launch meme coins, stablecoins, established meme coins), rules written before testing, go-live bar fixed in advance.
- **Audit of the 2026 bots published:** [audit/2026-11-old-bots.md](audit/2026-11-old-bots.md).
- **Track A shadow logger started.** Records every new pool on Solana and Base, runs safety checks, takes live buy-and-sell quotes, and tracks each token for two hours. It never trades.
- **First cost readings** on brand-new Solana pools (quote-only round trips, before network fees, first 11 tokens): £10 about 3.1%, £20 about 3.7%, £50 about 5.4%. Small sample; costs on new pools are higher than expected.
- **Track B stablecoin watch started.** First reading: all major stablecoins within 0.15% of $1, and the same small USDC/USDT difference on every venue, so no gap worth trading.
- **Track C test harness built and checked.** On random price data it found nothing; on data with a deliberately planted pattern it found the pattern; it refused to credit an idea that only rode a rising market. Real history is downloading.
