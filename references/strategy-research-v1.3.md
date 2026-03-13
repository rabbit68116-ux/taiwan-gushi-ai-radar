# Strategy Research Notes v1.3

Version: `v1.3`

這份文件整理 `Taiwan Stock Radar v1.3` 在策略模組與評估指標上的外部研究依據。  
This document records the external research basis behind the strategy modules and evaluation stack in `Taiwan Stock Radar v1.3`.

## 1. 使用方式

這不是一份逐字照抄論文的摘要。  
它的目的是把論文與官方技術文件轉成 **可落地的 skill 規格**，讓單股台股分析不只停在敘事，而是能進入策略選擇、驗證與風險管理。

This is not a literal summary of the cited papers.  
Its purpose is to translate research and official technical documentation into an **implementable skill specification** for single-stock Taiwan-equity analysis.

## 2. 核心研究來源與落地意義

| 來源 | 主要結論 | 對 repo 的落地影響 |
|---|---|---|
| [Jegadeesh & Titman, *Returns to Buying Winners and Selling Losers*](https://afajof.org/issue/volume-48-issue-1/) | 中期贏家持續與輸家持續現象支持動能與相對強勢存在。 | 建立 `relative_strength_leadership` 與 `time_series_momentum` 兩個核心策略模組。 |
| [Moskowitz, Ooi, Pedersen, *Time Series Momentum*](https://www.aqr.com/Insights/Research/Journal-Article/Time-Series-Momentum) | 資產的自身過去報酬能對未來短中期方向提供資訊，但並非無條件有效。 | 強化 `trend_following` 模組，並要求 regime 與波動檢查。 |
| [Daniel & Moskowitz, *Momentum Crashes*](https://www.nber.org/papers/w20439) | 動能策略會在市場壓力反轉時出現 crash 風險。 | 新增 crash guard、high-volatility veto、事件密集時段降權規則。 |
| [TA-Lib Function List](https://ta-lib.org/functions/) | 提供可實作、可重複的技術指標集合。 | 指定 `ADX`、`ATR/NATR`、`BBANDS`、`MACD`、`MFI`、`OBV`、`RSI` 為核心技術指標族群。 |
| [vectorbt Returns Accessors](https://vectorbt.dev/api/returns/accessors/) | 風險評估不應只停在 Sharpe；還可納入 `Omega`、`Tail Ratio`、`Calmar`、`Deflated Sharpe Ratio`。 | 擴大評估層，讓 tail risk 與 overfitting 風險可見。 |
| [Freqtrade Backtesting](https://www.freqtrade.io/en/stable/backtesting/) | 交易系統評估需同時看 CAGR、Sortino、Profit Factor、Expectancy、Drawdown 等。 | 建立 `performance + trade_quality` 雙層報告。 |
| [skfolio documentation](https://skfolio.org/) | `CVaR`、`Walk-Forward`、`Combinatorial Purged CV` 可用於尾部風險與穩健度驗證。 | 建立 `tail_risk + robustness` 驗證面板。 |

## 3. v1.3 納入的策略家族

### A. 趨勢跟隨 / Time-Series Momentum

納入理由：

- 研究支持「資產自己的過去趨勢」對未來短中期延續具有解釋力。
- 對台股單股來說，這最適合用於大型領導股或機構偏好的中大型股。

工程化規則：

- 需要市場與個股同向，不宜在混亂的高波動 regime 中單獨使用。
- 需要 `ADX` 或結構延續條件做確認，不能只靠單一報酬窗口。

### B. 相對強勢領導 / Relative-Strength Leadership

納入理由：

- 中期贏家相對強勢效應對單股選擇很有用，尤其在族群輪動明確時。
- 對台股來說，這種策略要搭配同業比較與機構籌碼，否則容易把「題材輪動尾聲」誤判成領導。

工程化規則：

- 必須同時看 peer ranking、成交值、外資 / 投信買賣超。
- 若領導地位弱化，應從 primary strategy 降為 secondary strategy 或直接退出。

### C. 突破確認 / Breakout Confirmation

納入理由：

- 突破是常見交易語言，但沒有量能與波動結構確認時，假突破非常常見。

工程化規則：

- 使用 `range breakout + volume expansion + ADX/OBV/MFI` 做多層確認。
- 若 breakout 發生在事件前高風險窗口，需明顯降權。

### D. 趨勢拉回 / Pullback Continuation

納入理由：

- 很多優質趨勢股的較佳風險報酬點，不在第一次擴張，而在健康拉回之後。

工程化規則：

- 檢查 `MA20/MA50`、`ATR pullback depth`、`RSI reset`。
- 拉回若演變成結構破壞，不可繼續把它稱為「健康回檔」。

### E. 波動收縮轉擴張 / Volatility Contraction Expansion

納入理由：

- 單股在重大方向選擇前，常先出現成交量乾涸與波動收斂。

工程化規則：

- 檢查 `BBANDS width`、`ATR compression`、`volume dry-up`。
- 若即將進入法說、月營收、政策事件密集區，壓縮不一定代表健康，可能只是市場等待。

### F. 戰術型均值回歸 / Tactical Mean Reversion

納入理由：

- 在高品質股票、短期偏離過度時，戰術反彈有時有用，但這不應是預設主策略。

工程化規則：

- 僅在高品質結構中作為 secondary module。
- 在持續下跌、流動性惡化、事件壓力升高時，應直接禁用。

## 4. v1.3 評估指標架構

### 核心績效 Performance

必要指標：

- `CAGR`
- `Annualized Volatility`
- `Sharpe Ratio`
- `Sortino Ratio`
- `Calmar Ratio`

原因：

- 只看單純報酬很容易高估高波動或低穩定度策略。

### 交易品質 Trade Quality

必要指標：

- `Profit Factor`
- `Expectancy`
- `Win Rate`
- `Exposure`
- `Turnover`
- `Trade Count`

原因：

- 很多策略靠極低交易數或極端單筆盈虧撐住表面績效，這在實盤很脆弱。

### 尾部風險 Tail Risk

必要指標：

- `Max Drawdown`
- `VaR`
- `CVaR`
- `CDaR`
- `Ulcer Index`
- `Omega Ratio`
- `Tail Ratio`

原因：

- 單股交易在台股特別容易受到跳空、事件風險與流動性折價影響。

### 穩健度 Robustness

必要指標：

- `Walk-Forward`
- `Purged CV`
- `Combinatorial Purged CV`
- `Deflated Sharpe Ratio`
- `Parameter Stability`
- `Cost Sensitivity`
- `Regime-Split Performance`

原因：

- 若策略只在一段特定行情或一組參數下好看，委員會不應把它當成高品質結論。

## 5. v1.3 的工程化設計原則

1. 先分開「看對方向」與「適合怎麼做」。
   同一個 bullish thesis，可能對應 `breakout`、`pullback`、`relative strength` 三種完全不同的執行方式。

2. 先做策略分類，再做買賣點。
   沒有 strategy-family 選擇，買點與停損很容易寫成模板化句子。

3. 不讓風險與驗證變成附註。
   `v1.3` 把 Validation Analyst 獨立成角色，就是為了避免風險檢查永遠排在最後一段。

4. 對研究做工程化轉譯，不假裝論文等於即時交易規則。
   repo 中的權重、門檻、必填欄位，都是根據單股台股場景設計的治理規則。

## 6. 對 repo 的直接改動方向

`v1.3` 需要至少具備以下結構：

- `config/strategy_modules.yaml`
- `config/evaluation_metrics.yaml`
- `config/agent_personas.yaml` 增加 `Strategy Architect` 與 `Quant Validation Analyst`
- `config/action_rules.yaml` 加入 `strategy_selection`、`validation_scorecard`、`robustness_checks`
- `SKILL.md` 與 `README.md` 改成 strategy-enhanced 版本

## 7. 注意事項

- 上述研究支持的是 **策略家族與評估方法的合理性**，不是保證未來獲利。
- 對單股分析而言，資料新鮮度、事件時點、流動性品質，會顯著影響策略有效性。
- 因此 `v1.3` 的真正目的不是讓 agent 更會「喊方向」，而是讓 agent 更會 **解釋為何採用這個策略，以及為何此刻不該輕率採用另一個策略**。
