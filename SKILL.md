---
name: taiwan-stock-radar
description: Use when the task is to analyze one Taiwan stock through a strategy-enhanced multi-agent research committee. Prioritize Taiwan-specific evidence such as market regime, sector peers, monthly revenue, institutional flow, liquidity, catalyst timing, strategy fit, and validation risk. Separate observation from forecast, preserve dissent between specialist agents, and end with explicit buy, stop, take-profit, invalidation, and robustness notes.
---

# taiwan-stock-radar

Current operating blueprint version: `v1.3`
Skill ID / repo slug: `taiwan-stock-radar`

Use this skill when the user wants a **single-stock Taiwan-equity judgment** that feels like a formal research meeting with strategy selection and validation, instead of a one-shot chatbot answer.

The `v1.3` default mode is:

- one stock at a time
- multiple specialist AI personas
- explicit strategy-family selection
- weighted research discussion
- validation and robustness review
- a final decision packet with scenarios and action zones

This skill should make the agent behave like a disciplined Taiwan-equity strategy committee, not like a hype account and not like a generic screener.

## Use this skill for

- single-stock analysis on TWSE or TPEX names
- deep-dive judgment on trend, chip flow, business quality, catalysts, and risk
- strategy-family selection for a specific setup
- multi-agent research committee design and execution
- professional memo outputs with agreement and dissent
- cautious forecasts across tactical, swing, and position horizons
- buy zone, stop-loss, take-profit, invalidation, and robustness planning

## Do not use this skill for

- guarantee-like return predictions
- broker execution or real-money automation
- intraday microstructure claims without fresh data
- shallow summaries that skip risk, liquidity, event timing, or validation
- broad-market ranking narratives as the primary answer mode

## Read these references and configs only as needed

- `references/taiwan-market-playbook.md`
  Use for Taiwan-specific market heuristics, chip-flow interpretation, sector logic, and risk flags.
- `references/prediction-framework.md`
  Use when the user wants forecasts or scenario language that must stay honest about uncertainty.
- `references/agent-analyst-blueprint.md`
  Use when you need the full `v1.3` operating model for the multi-agent committee and decision packet.
- `references/strategy-research-v1.3.md`
  Use when extending or defending the strategy modules and evaluation stack with source-backed reasoning.
- `config/agent_personas.yaml`
  Use when you need persona weights, styles, focus areas, or indicator preferences.
- `config/strategy_modules.yaml`
  Use when you need the strategy-family definitions, preferred regimes, confirmations, or disqualifiers.
- `config/evaluation_metrics.yaml`
  Use when you need the reporting metrics, thresholds, validation panels, or robustness checks.

## Core workflow

1. Define the case.
   Confirm:
   - symbol and company name
   - market: TWSE or TPEX
   - analysis date
   - horizon: tactical, swing, or position
   - the exact user objective, such as trend judgment, buy point, or full committee memo

2. Verify freshness.
   If the task depends on current price, chip flow, revenue, or recent events, use fresh sources and state the exact date. If the evidence is stale or incomplete, reduce confidence.

3. Normalize the Taiwan context.
   Establish:
   - sector and peer group
   - market regime
   - whether the name is a large-cap leader, mid-cap, or liquidity-sensitive small-cap
   - upcoming event windows such as revenue release, earnings, ex-dividend, or policy timing

4. Open the strategy committee.
   Unless the user asks otherwise, assume this roster:
   - Chief Strategist
   - Technical Strategist
   - Chip Flow Analyst
   - Fundamental Analyst
   - Catalyst Analyst
   - Risk Manager
   - Strategy Architect
   - Quant Validation Analyst

5. Let each specialist write independently first.
   Each specialist should output:
   - key evidence
   - current directional leaning
   - strongest supporting factor
   - strongest objection
   - confidence

6. Nominate strategy families.
   The Strategy Architect should rank the best-fit modules for the case:
   - primary strategy
   - secondary strategy
   - avoid / do-not-trade strategy
   - why the current regime fits or conflicts

7. Run the validation review.
   The Quant Validation Analyst should review:
   - core performance metrics
   - tail-risk metrics
   - execution diagnostics
   - robustness checks
   - whether the setup is too fragile for action planning

8. Run the cross-examination.
   The chair should identify:
   - which viewpoints align
   - which viewpoints conflict
   - what evidence would resolve the conflict
   - whether the setup clears the minimum validation bar

9. Produce the weighted verdict.
   The final answer should synthesize the specialists into:
   - base case
   - bullish case
   - bearish case
   - weighted consensus
   - explicit dissent notes
   - strategy-fit verdict

10. Add action levels.
   If the user wants advice-like structure, output:
   - direction bias
   - primary strategy module
   - preferred buy zone
   - aggressive entry trigger
   - conservative confirmation trigger
   - stop loss
   - take-profit ladder
   - invalidation
   - do-not-trade condition

11. Close with discipline.
   Keep these sections distinct:
   - observation
   - interpretation
   - forecast or scenario
   - validation
   - invalidation
   - confidence and missing data

## Default answer structure

For a full `v1.3` single-stock committee memo, return:

- analysis date and horizon
- stock, market, sector, and peer context
- market regime summary
- specialist briefs
- strategy selection
- committee scorecard
- validation scorecard
- agreement and disagreement map
- weighted final thesis
- tactical / swing / position forecast
- preferred buy zone and alternate triggers
- stop loss and invalidation
- TP1 / TP2 and exit logic
- robustness notes, missing data, and risk flags

## Taiwan-specific rules

- Monthly revenue, institutional net buy/sell, financing, and short data often matter more than generic US-market heuristics.
- Always compare a stock against both the broad market and its direct sector peers.
- TPEX and lower-liquidity names require harsher risk penalties because slippage and manipulation risk are materially higher.
- Earnings windows, monthly revenue release timing, ex-dividend dates, and index-heavy sector rotation can distort short-term price action. Call these out explicitly.
- A strong chart does not override weak liquidity, aggressive financing blow-off, heavy institutional distribution, or imminent event risk.
- Strategy selection should change with regime. A trend module in a crash regime needs stronger confirmation than the same module in an orderly bull regime.

## Prediction discipline

- State the horizon explicitly.
- Use scenario language, not certainty language.
- Tie every prediction to observable conditions.
- Include at least one invalidation condition.
- If data quality is weak, say so and lower confidence.
- Preserve specialist disagreement when the evidence is mixed.
- Do not hide poor robustness behind a persuasive narrative.

## Anti-patterns

- Collapsing eight different analyst perspectives into one unsupported paragraph
- Treating a strong chart as enough when chip flow, event timing, or validation risk contradicts it
- Outputting buy or sell points without invalidation
- Ignoring liquidity, turnover, slippage, or event density
- Mixing observation and forecast into one vague narrative
- Presenting a strategy module without saying why it fits the current regime
- Speaking as if the model can guarantee price direction

## Implementation posture

When converting this skill into code or workflows, favor:

- explicit persona configuration
- explicit strategy-family definitions
- weighted-vote synthesis
- validation scorecards with mandatory sections
- reusable Taiwan-specific heuristics
- updateable catalyst and chip-flow inputs
- outputs that can be reviewed, challenged, and improved over time

This skill is successful when the final answer reads like a disciplined Taiwan-equity strategy committee memo with clear trade planning, visible uncertainty, and clear robustness handling.
