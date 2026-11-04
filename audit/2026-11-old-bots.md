# Audit of the retired 2026 bots (written 4 Nov 2026)

Two Solana bots ran live in spring 2026 with small stakes: a new-launch sniper and a scalper. Both are now retired. This is the honest record.

## Results

| Bot | Trades | Wins | Result before fees, as % of everything staked |
|---|---|---|---|
| New-launch sniper (27 Mar – 4 May 2026) | 799 | 43% | −2.7% |
| Scalper | 165 | 32% | negative |

The sniper's recorded P&L was calculated from price moves, not from what actually came back to the wallet. Once the network priority fees it paid are added (estimated from its own settings), the real loss was several times larger: roughly −12% of everything staked.

## Where the money went (sniper, % of stake per exit type)

| Exit type | Trades | Average result |
|---|---|---|
| Trailing stop on big runners | 88 | +73% |
| Final take-profit at +150% | 10 | +120% |
| Stop-loss | 257 | −12.5% |
| Rug pulls (liquidity fell by half or more) | 64 | about −75% |
| Smaller liquidity-drop exits | 300 | about −20% |

## Lessons carried into the new research

1. **Fixed fees must be small next to the position.** Small stakes paid fees on up to seven transactions per trade.
2. **Rugs must be filtered before entry.** A stop-loss cannot exit a rug; 8% of trades cost about half of all winnings.
3. **Exits after the first take-profit were too loose.** 176 trades reached the first target and still finished at a loss.
4. **Checks every 30 seconds are too slow** for thin pools; stops filled far below their level.
5. **Measure P&L from the wallet, not the chart.**
6. **Safety checks must fail closed.** The old honeypot check passed tokens when its data source was unavailable, and a coding error meant a confirmed honeypot was never treated as fatal.
7. **A high win rate means nothing on its own.** The old bot showed a high headline win rate while losing money.
