# Prediction Framework

Use this reference when the user wants forecasts, directional judgment, ranking logic, or strategy proposals.

## 1. Separate what is known from what is inferred

Every answer should distinguish:

- Observation
  Facts from data or clearly described chart structure
- Interpretation
  What those facts imply under a factor framework
- Forecast
  Conditional next-step scenarios

Do not collapse all three into a single paragraph.

## 2. Use time horizons before forecasting

Choose one:

| Horizon | Typical use |
|---|---|
| 1 to 5 trading days | tactical continuation / pullback |
| 2 to 6 weeks | swing setup or failed breakout risk |
| 1 to 2 quarters | theme or business-cycle thesis |

If the user gives no horizon, default to swing.

## 3. Preferred forecast format

### Single stock

Use this structure:

1. Analysis date
2. Current regime and sector context
3. Factor summary
4. Base case
5. Bullish case
6. Bearish case
7. Invalidation
8. Confidence

Example phrasing:

- Base case: if price holds above MA20 and sector strength stays intact, consolidation-to-uptrend continuation remains the most likely path over the next 2 to 4 weeks.
- Bullish case: if breakout volume expands and institutional flow improves, the stock can re-enter price discovery.
- Bearish case: if volume fades and price loses MA20 while peers weaken, the setup shifts from constructive pullback to failed breakout.

## 4. Confidence rubric

Use a simple confidence label:

| Confidence | Meaning |
|---|---|
| Low | stale or missing data, mixed factors, high noise |
| Medium | several factors align, but not enough confirmation |
| High | regime, trend, sector, and risk profile align cleanly |

High confidence still does not mean certainty.

## 5. Ranking or watchlist output

When the user asks for a list, return:

| Field | Required |
|---|---|
| Symbol | yes |
| Name | yes |
| Sector | yes |
| Score | yes |
| Direction Bias | yes |
| Buy Zone | yes |
| Stop Loss | yes |
| Take Profit | yes |
| Main driver | yes |
| Main risk | yes |
| Next trigger | yes |

Avoid ranking without a visible scoring basis.

## 6. Strategy and backtest proposals

When proposing a strategy, define:

- universe
- rebalancing frequency
- entry rule
- exit rule
- position sizing
- fees and slippage
- lookback window
- no-lookahead data assumptions

If any of these are missing, say the proposal is incomplete.

## 7. Action-level output

When the user asks "can I buy this?" or wants a professional-style stock plan, add:

- setup type: breakout / trend pullback / early base
- buy zone
- aggressive trigger
- conservative trigger
- stop loss
- TP1 / TP2
- invalidation

The buy/sell plan must match the horizon. Do not give a swing target with an intraday-style stop.

## 8. Deep-dive stock memo

For a single-stock deep dive, include:

- market regime
- sector and peer map
- business / revenue support
- chip flow
- multi-timeframe structure
- catalyst calendar
- scenario tree
- action plan

This is the step that makes the agent feel like an analyst instead of a screener.

## 9. Anti-patterns

Avoid:

- "This stock will definitely rise"
- pure narrative prediction with no factor support
- using monthly revenue or earnings before their publication date
- using today's sector winners to explain a historical signal that did not have that information yet
- comparing illiquid OTC names to mega-cap trend behavior without penalty

## 10. Backtest hygiene

Always be alert to:

- lookahead bias
- survivorship bias
- stale fundamentals
- unrealistic fills
- ignored trading halts or liquidity issues
- cherry-picked date ranges

## 11. When not to predict

Downgrade or refuse a strong prediction if:

- price data is stale
- the requested horizon does not match available data
- the stock is too illiquid for confident chart claims
- the user asks for certainty rather than scenarios

## 12. Minimal good answer

Even a short answer should include:

- date
- horizon
- key setup summary
- risk
- invalidation
- confidence
