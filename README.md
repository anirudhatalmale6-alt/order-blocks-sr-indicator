# Order Blocks + Swing S/R

A Pine Script v5 indicator that marks order blocks and swing support/resistance levels.

## Install

1. Open TradingView, bottom panel, **Pine Editor**.
2. Delete whatever is in there.
3. Paste the contents of `order_blocks_sr.pine`.
4. **Save**, then **Add to chart**.

## What it does

**Order blocks.** A bullish zone is the last down candle before an up-move that runs
for at least `OB Confirmation Length` consecutive up candles *and* closes above that
candle's high. Bearish is the mirror. The zone extends right until price trades back
through it, at which point it is removed (or greyed out, your choice).

**Swing S/R.** Confirmed pivot highs and lows using `Swing Lookback` bars either side.
A level is dropped once price closes through it, so the chart stays clean.

## Settings

| Setting | Default | Effect |
|---|---|---|
| OB Confirmation Length | 3 | Follow-through candles required. Higher = fewer, stronger zones. |
| Zone from candle body only | off | Off = wick to wick. On = open to close (tighter zones). |
| Max zones kept per side | 5 | Older zones are dropped. |
| Zone is mitigated on | Wick | Wick = any trade back through kills it. Close = survives until a close through. |
| Keep mitigated zones | off | Greys them out instead of deleting. |
| Swing Lookback | 10 | Bars either side of a pivot. Higher = fewer, more significant levels. |
| Max levels kept per side | 3 | |
| Show price on levels | on | |

## Alerts

Six conditions are exposed to the alert dialog: new bullish OB, new bearish OB,
price inside a bullish zone, price inside a bearish zone, resistance broken,
support broken.

## Note on pivots

Swing levels are confirmed, not predictive. A level only appears once `Swing Lookback`
bars have printed to its right, so it is drawn back at the pivot but plotted late by
that many bars. That is inherent to pivot detection, not a bug — an indicator that
plotted them instantly would be repainting.
