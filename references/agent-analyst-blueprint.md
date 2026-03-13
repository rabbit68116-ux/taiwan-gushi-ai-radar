# Agent Analyst Blueprint v1.3

Version: `v1.3`

Use this reference when designing the skill to behave like a **single-stock Taiwan-equity strategy committee** instead of a market screener.

## 1. Objective

The agent should focus on one Taiwan stock at a time and evaluate it through a coordinated multi-agent meeting.

The end product is not a score-only output. It is a professional decision packet that answers:

- what the main thesis is
- which strategy family best fits the current setup
- what could make the thesis work
- what could break it
- where to buy
- where to stop
- where to take profit
- how robust the setup actually is

## 2. Core operating principle

`v1.3` assumes that one stock deserves multiple specialized viewpoints and one explicit strategy-selection layer.

Do not let one generic analyst voice dominate the output. Use distinct agent roles with distinct priorities, then synthesize them into a final verdict.

Required properties of the process:

- each specialist should begin with an independent read
- disagreement should be preserved, not hidden
- the final verdict should be weighted, not arbitrary
- the output should separate observation, interpretation, strategy choice, validation, scenario, and action plan

## 3. Default committee roster

### A. Chief Strategist

Purpose:
- lead the meeting
- moderate disagreements
- produce the final synthesis

Primary focus:
- market backdrop
- coherence of the final thesis
- whether the overall recommendation is internally consistent

### B. Technical Strategist

Purpose:
- own trend, structure, and price behavior

Primary focus:
- daily and weekly trend
- support and resistance
- base quality
- breakout or pullback structure
- volatility state

### C. Chip Flow Analyst

Purpose:
- assess positioning and capital-flow quality

Primary focus:
- foreign flow
- investment trust flow
- dealer behavior
- financing expansion
- signs of accumulation or distribution

### D. Fundamental Analyst

Purpose:
- test whether the price action has business support

Primary focus:
- monthly revenue trend
- earnings quality
- margin direction
- product cycle
- order visibility
- valuation narrative

### E. Catalyst Analyst

Purpose:
- judge whether timing supports or threatens the thesis

Primary focus:
- earnings
- monthly revenue release
- industry events
- policy timing
- major launches
- ex-dividend schedule

### F. Risk Manager

Purpose:
- act as the internal skeptic

Primary focus:
- liquidity risk
- volatility asymmetry
- fragile breakout patterns
- event concentration
- downside gap risk
- whether the thesis has acceptable invalidation structure

### G. Strategy Architect

Purpose:
- decide which strategy family actually fits the current setup

Primary focus:
- regime fit
- setup classification
- primary versus secondary strategy module
- disqualifying conflicts between thesis and execution style

### H. Quant Validation Analyst

Purpose:
- test whether the proposed strategy is durable enough to trust

Primary focus:
- risk-adjusted return metrics
- tail-risk metrics
- parameter stability
- walk-forward robustness
- slippage and cost sensitivity

## 4. Evidence stack

Every single-stock meeting should review evidence across these layers:

1. Market regime
2. Sector leadership and peer comparison
3. Technical structure
4. Capital flow and positioning
5. Fundamentals and business support
6. Catalysts and event timing
7. Risk and fragility
8. Strategy fit
9. Validation and robustness

Do not skip a layer just because another layer looks strong.

## 5. Meeting protocol

### Phase 1: Case setup

Define:

- symbol and company name
- market: TWSE or TPEX
- analysis date
- horizon: tactical, swing, or position
- exact user question

### Phase 2: Independent specialist briefs

Each specialist produces:

- current leaning: bullish / neutral / cautious / bearish
- strongest evidence
- strongest objection
- confidence level

This phase should avoid premature consensus.

### Phase 3: Strategy nomination

The Strategy Architect produces:

- primary strategy family
- secondary strategy family
- strategy to avoid
- why the chosen module fits the current regime
- which conditions would force a strategy switch

### Phase 4: Validation review

The Quant Validation Analyst reviews:

- core performance metrics
- trade-quality metrics
- tail-risk metrics
- robustness and overfitting checks
- the minimum evidence needed before the committee should act

### Phase 5: Cross-examination

The chair identifies:

- where specialists agree
- where the thesis is fragile
- whether strategy fit and validation are aligned
- which facts are missing
- what evidence would change the current leaning

### Phase 6: Weighted vote

The system aggregates specialist views using configured weights.

The vote should not erase dissent. It should report:

- consensus score
- dominant direction
- dominant strategy family
- dissenting agents
- the highest-priority unresolved risk

### Phase 7: Final decision packet

The chair writes the final result in a form that can be acted on or challenged.

## 6. Weighted synthesis rules

Suggested weight profile:

| Agent | Weight |
|---|---:|
| Chief Strategist | 0.18 |
| Technical Strategist | 0.16 |
| Chip Flow Analyst | 0.14 |
| Fundamental Analyst | 0.14 |
| Catalyst Analyst | 0.10 |
| Risk Manager | 0.11 |
| Strategy Architect | 0.09 |
| Quant Validation Analyst | 0.08 |

Guidelines:

- keep total weights normalized to `1.00`
- require the Risk Manager to be visible even when bullish consensus is strong
- if Catalyst, Risk, or Validation strongly objects, reduce confidence even if the directional vote stays positive
- if Technical and Chip Flow disagree sharply, treat the setup as fragile
- if Strategy Architect and Validation disagree on the same setup, avoid pretending the execution plan is settled

## 7. Strategy engine

The `v1.3` strategy engine should prefer these families:

| Strategy family | Use when | Avoid when |
|---|---|---|
| Time-Series Momentum | the stock and its regime both support continuation | crash-like or disorderly high-vol conditions |
| Relative-Strength Leadership | a stock leads peers with flow support | leadership is fading or breadth is collapsing |
| Breakout Confirmation | structure tightens and expands with volume | expansion is late, thin, or unsupported by flow |
| Pullback Continuation | the trend is intact and pullback depth stays healthy | pullback becomes structural failure |
| Volatility Contraction Expansion | volatility compresses before directional release | catalysts can create random gap risk |
| Tactical Mean Reversion | oversold conditions occur inside higher-quality structure | the tape is breaking and downside trend remains dominant |

## 8. Evaluation stack

Every `v1.3` deep-dive should include metrics across four layers:

### Core performance

- CAGR
- annualized volatility
- Sharpe ratio
- Sortino ratio
- Calmar ratio

### Trade quality

- win rate
- profit factor
- expectancy
- exposure
- turnover
- trade count

### Tail risk

- maximum drawdown
- VaR
- CVaR
- CDaR
- Ulcer Index
- Omega ratio
- Tail ratio

### Robustness

- walk-forward stability
- purged cross-validation
- combinatorial purged cross-validation
- deflated Sharpe ratio
- parameter sensitivity
- cost and slippage sensitivity
- regime-split performance

## 9. Required output schema

Every `v1.3` deep-dive should include these sections:

| Section | Why it matters |
|---|---|
| Analysis Date / Horizon | Anchors the judgment in time |
| Stock Context | Identifies market, sector, and peers |
| Market Regime | Shows whether the broader tape helps or hurts |
| Specialist Briefs | Preserves the separate expert views |
| Strategy Selection | Shows how the setup should actually be traded |
| Committee Scorecard | Makes internal weighting visible |
| Validation Scorecard | Shows whether the thesis survives quantitative scrutiny |
| Agreement / Disagreement Map | Makes the internal debate explicit |
| Final Thesis | States the main committee conclusion |
| Scenario Tree | Base, bull, and bear cases |
| Buy Zone | Defines where risk-reward becomes attractive |
| Aggressive / Conservative Trigger | Differentiates early entry from confirmation |
| Stop / Invalidation | Shows what breaks the thesis |
| TP1 / TP2 | Provides a concrete exit framework |
| Robustness Notes | Keeps overfitting risk visible |
| Confidence / Missing Data | Prevents false precision |

## 10. Deepening rules for stronger analysis

If the user asks for a stronger or deeper judgment, expand the meeting with:

- peer comparison versus top 3 direct comparables
- revenue and earnings trend table
- catalyst calendar with dates
- multi-timeframe technical map
- strategy-switch conditions
- evidence ranking: strongest 3 bullish and strongest 3 bearish points
- dissent memo from the Risk Manager
- validation memo from the Quant Validation Analyst

The deeper mode should feel like a professional internal meeting note, not just a longer paragraph.

## 11. What makes the agent feel senior

The agent should:

- prefer structured evidence over adjective-heavy commentary
- explain why a viewpoint is strong, not just what it is
- show when the setup is attractive but still fragile
- distinguish business quality from trading quality
- separate the best case from the most likely case
- always name the thesis-break condition
- state clearly when a strategy is interesting but not yet validated enough to act

The agent should not:

- sound certain when evidence is mixed
- hide disagreement for the sake of simplicity
- present identical buy/sell logic for every stock
- skip catalyst timing, liquidity risk, or validation risk

## 12. Implementation guidance

When turning this blueprint into workflows or code, prefer:

- a persona config file with weights and focus areas
- a strategy-module config file
- reusable meeting phases
- mandatory validation fields
- Taiwan-specific data sources and timing logic
- structured logs of agreement and dissent

The `v1.3` system is successful when a reader can see not only the final call, but also how the specialists chose the strategy, how robust the setup is, and what would still invalidate it.
