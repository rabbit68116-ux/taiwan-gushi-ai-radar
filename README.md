# Taiwan Stock Radar

[![GitHub repo](https://img.shields.io/badge/GitHub-rabbit68116--ux%2Ftaiwan--stock--radar-181717?logo=github)](https://github.com/rabbit68116-ux/taiwan-stock-radar)
![Status](https://img.shields.io/badge/status-architecture%20v1.0-blue)
![Skill](https://img.shields.io/badge/skill-v1.3-orange)
![Market](https://img.shields.io/badge/market-Taiwan%20Stocks-red)
![Mode](https://img.shields.io/badge/mode-single--stock%20strategy%20committee-green)

Taiwan Stock Radar v1.3 是一個面向台灣股票單股研判的研究型 AI skill，目標不是給出一句鬆散的看多或看空，而是讓 AI agent 用更接近專業投資研究委員會的方式，針對一檔股票完成策略判斷、驗證、風險盤點與操作規劃。

> 一檔股票。八位 specialist AI analysts。一次正式研究會議。六大策略模組。一份可執行的決策文件。<br>
> One stock. Eight specialist AI analysts. One formal research meeting. Six strategy modules. One executable decision packet.

[官方網站 Official Website](https://rabbit68116-ux.github.io/taiwan-stock-radar/) | [案例頁 Featured Case Study](https://rabbit68116-ux.github.io/taiwan-stock-radar/case-study.html) | [GitHub Repo](https://github.com/rabbit68116-ux/taiwan-stock-radar)

---

## 繁體中文

### 封面定位

**Taiwan Stock Radar** 是一個專注於台灣股票單股深度研判的 AI skill。
它不是只做市場掃描的 watchlist 工具，也不是只輸出一句方向判斷的聊天式助理，而是把一檔股票交給多位不同專長、不同性格、不同權重的 AI analyst 分身，模擬一場正式的投資研究會議。

`v1.3` 的重心是 **策略加強版本**：

- 不只問「這檔股票偏多還是偏空」
- 還要回答「這檔股票目前最適合哪一種交易策略」
- 以及「這個策略在什麼條件下成立、失效、需要降評或不該做」

### v1.3 策略加強重點

- 新增 `6` 大策略模組：趨勢跟隨、相對強勢領導、突破確認、趨勢拉回、波動收縮轉擴張、戰術型均值回歸。
- 多加入 `Strategy Architect` 與 `Quant Validation Analyst`，把「策略選擇」和「回測驗證」從原本的委員會中獨立出來。
- 新增策略驗證面板：不只看 thesis，也看 `Sharpe`、`Sortino`、`Calmar`、`Profit Factor`、`CVaR`、`Deflated Sharpe Ratio`、`Walk-Forward`、`Purged CV` 等指標。
- 把 `momentum crash`、高波動 regime、事件密集期、流動性不足等情況納入 veto 或降權條件。
- 把論文與官方技術文件轉成可落地的 repo 規格，而不是停留在概念層。

### 展品摘要 Exhibit Snapshot

| 項目 | 說明 |
|---|---|
| 產品模式 Product mode | `v1.3` strategy-enhanced single-stock committee |
| 主要市場 Coverage | `TWSE / TPEX` 單股深度研判 |
| Agent 數量 Agent count | `8` 位 specialist personas |
| 策略家族 Strategy families | `6` 大策略模組 |
| 驗證層 Evaluation layers | `Performance / Tail Risk / Execution / Robustness` |
| 最終交付 Final deliverable | 趨勢預測、策略選擇、驗證面板、買入區、停損區、停利區、失效條件 |
| 公開展示 Public surface | GitHub repo + GitHub Pages product site |

### 六大策略模組 Strategy Modules

| 策略模組 | 用途 | 主要指標 |
|---|---|---|
| 趨勢跟隨 / Time-Series Momentum | 當個股與市場方向同向延續時，捕捉順勢續航 | `6M/12M return`、`SMA50>SMA200`、`ADX`、`MACD`、`ATR/NATR` |
| 相對強勢領導 / Relative-Strength Leadership | 找出同族群中最強、且仍有資金支持的領導股 | `relative strength`、同業排名、機構買超、成交值 |
| 突破確認 / Breakout Confirmation | 避免假突破，只在結構與量能都通過時採取行動 | `Donchian range`、`volume expansion`、`ADX`、`OBV`、`MFI` |
| 趨勢拉回 / Pullback Continuation | 在上升趨勢中的合理回檔區尋找風險報酬比 | `MA20/MA50 support`、`ATR pullback depth`、`RSI reset` |
| 波動收縮轉擴張 / Volatility Contraction Expansion | 尋找收縮整理後可能出現的方向選擇 | `Bollinger Band width`、`ATR compression`、`volume dry-up` |
| 戰術型均值回歸 / Tactical Mean Reversion | 僅在高品質個股、短期過度偏離時做戰術性反彈 | `RSI`、`MFI`、`distance from VWAP/MA20`、`gap exhaustion` |

### 評估與驗證面板 Evaluation Stack

| 層級 | 目的 | 代表指標 |
|---|---|---|
| 核心績效 Performance | 檢查策略是否真的有風險調整後報酬 | `CAGR`、`Annualized Volatility`、`Sharpe`、`Sortino`、`Calmar` |
| 交易品質 Trade Quality | 檢查勝率以外的盈虧結構 | `Profit Factor`、`Expectancy`、`Win Rate`、`Exposure`、`Turnover` |
| 尾部風險 Tail Risk | 避免只看平均值卻忽略大回撤與左尾 | `Max Drawdown`、`VaR`、`CVaR`、`CDaR`、`Ulcer Index`、`Omega`、`Tail Ratio` |
| 穩健度 Robustness | 檢查結果是不是只在一組參數或一段行情下成立 | `Walk-Forward`、`Purged CV`、`Combinatorial Purged CV`、`Deflated Sharpe Ratio`、`Cost Sensitivity` |

### 多重 AI Agent 研討會

在 `v1.3` 中，單一股票會進入一個策略加強版 multi-agent committee。每位 agent 有不同性格、專業、指標權重與責任。

| AI Agent | 角色定位 | 核心觀察 | 權重 |
|---|---|---|---:|
| Chief Strategist | 主持研究會議，整合最終結論 | 市場背景、衝突裁決、資本配置語言 | 0.18 |
| Technical Strategist | 技術面與結構分析 | 趨勢、支撐壓力、突破品質、波動結構 | 0.16 |
| Chip Flow Analyst | 籌碼與資金流向分析 | 外資、投信、融資、分配跡象 | 0.14 |
| Fundamental Analyst | 基本面與品質分析 | 月營收、獲利品質、產品週期、估值敘事 | 0.14 |
| Catalyst Analyst | 事件與催化因子分析 | 法說、月營收、政策、產業事件、時點風險 | 0.10 |
| Risk Manager | 反方與風控代表 | 流動性、跳空風險、事件聚集、失效條件 | 0.11 |
| Strategy Architect | 策略模組選擇與切換 | setup 類型、regime fit、策略衝突 | 0.09 |
| Quant Validation Analyst | 驗證與穩健度檢查 | 回測品質、尾部風險、參數穩定性、成本敏感度 | 0.08 |

### 單股研討會輸出範例

下面是 `v1.3` 希望 GitHub 首頁展示的輸出樣貌。它不是即時喊單，而是策略強化後的標準決策文件格式。

```text
Taiwan Stock Radar v1.3
Illustrative Single-Stock Strategy Committee Output
Case: 2330 台積電
Analysis Date: 2026-03-13
Horizon: Swing

Strategy Engine
- Primary module: Relative-Strength Leadership
- Secondary module: Pullback Continuation
- Do not use: Tactical Mean Reversion while event density remains elevated

Committee Thesis
- Base view remains constructive while sector leadership, institutional flow, and event order remain intact.

Validation Panel
- Sharpe / Sortino / Calmar: pass
- Profit Factor / Expectancy: pass
- CVaR / Max Drawdown: acceptable but not loose
- Deflated Sharpe Ratio: still requires caution, not a blind green light
- Cost sensitivity: reduce size if slippage worsens

Scenario Tree
- Base case: orderly pullback followed by trend resumption
- Bull case: leadership continuation with breakout confirmation
- Bear case: structure failure plus distribution and event disappointment

Action Plan
- Preferred buy zone: support retest area
- Aggressive trigger: breakout reclaim with volume and ADX confirmation
- Conservative trigger: weekly close above resistance with peer leadership intact
- Stop loss: structural break below support
- TP1 / TP2: staged scale-out under trend-extension logic
- Invalidation: thesis weakens if structure, flow, and event quality deteriorate together
```

### 研究依據 Research Basis

`v1.3` 的策略加強不是憑空加欄位，而是根據論文與官方技術文件做工程化轉譯。重要來源包括：

- [Jegadeesh & Titman, *Returns to Buying Winners and Selling Losers*](https://afajof.org/issue/volume-48-issue-1/)
  用來支持中期動能與相對強勢模組的存在。
- [Moskowitz, Ooi, Pedersen, *Time Series Momentum*](https://www.aqr.com/Insights/Research/Journal-Article/Time-Series-Momentum)
  用來支持趨勢跟隨與時間序列動能模組。
- [Daniel & Moskowitz, *Momentum Crashes*](https://www.nber.org/papers/w20439)
  用來建立高波動 / 壓力 regime 下的 crash guard 與降權規則。
- [TA-Lib Function List](https://ta-lib.org/functions/)
  用來規範實作層支援的技術指標群，如 `ADX`、`ATR`、`BBANDS`、`MACD`、`MFI`、`OBV`、`RSI`。
- [vectorbt Returns Accessors](https://vectorbt.dev/api/returns/accessors/)
  用來擴充 `Omega`、`Tail Ratio`、`Calmar`、`Deflated Sharpe Ratio` 等評估指標。
- [Freqtrade Backtesting Metrics](https://www.freqtrade.io/en/stable/backtesting/)
  用來補強實務交易報告常用的 `CAGR`、`Sortino`、`Profit Factor`、`Expectancy`。
- [skfolio Model Selection / Walk-Forward](https://skfolio.org/)
  用來導入 `Walk-Forward`、`Purged CV`、`Combinatorial Purged CV` 與 `CVaR` 等穩健度與尾部風險概念。

> 這些來源提供的是研究方向與可驗證的指標集合；repo 內的策略模組、權重與門檻，是依台股單股研判場景做的工程化設計，不是逐字複製論文。

### 專案內容 Repo Contents

| 路徑 | 作用 |
|---|---|
| [`SKILL.md`](./SKILL.md) | `v1.3` 核心 skill 定義，說明策略加強版單股分析流程 |
| [`references/agent-analyst-blueprint.md`](./references/agent-analyst-blueprint.md) | 多 agent 研討會與策略驗證藍圖 |
| [`references/strategy-research-v1.3.md`](./references/strategy-research-v1.3.md) | `v1.3` 外部研究來源與工程化落地原則 |
| [`config/agent_personas.yaml`](./config/agent_personas.yaml) | 各 agent 的性格、專長、權重與指標責任 |
| [`config/strategy_modules.yaml`](./config/strategy_modules.yaml) | 六大策略模組、適用 regime、確認條件與禁用條件 |
| [`config/evaluation_metrics.yaml`](./config/evaluation_metrics.yaml) | 績效、尾部風險、執行品質與穩健度評估集合 |
| [`config/action_rules.yaml`](./config/action_rules.yaml) | 會議流程、必要輸出欄位與決策欄位規範 |
| [`docs/index.html`](./docs/index.html) | 公開產品首頁 |
| [`docs/case-study.html`](./docs/case-study.html) | 單股完整展示頁 |

### 公開入口 Public Links

- GitHub Repo: [https://github.com/rabbit68116-ux/taiwan-stock-radar](https://github.com/rabbit68116-ux/taiwan-stock-radar)
- Public Website: [https://rabbit68116-ux.github.io/taiwan-stock-radar/](https://rabbit68116-ux.github.io/taiwan-stock-radar/)
- Case Study: [https://rabbit68116-ux.github.io/taiwan-stock-radar/case-study.html](https://rabbit68116-ux.github.io/taiwan-stock-radar/case-study.html)

### 快速開始 Quick Start

```bash
python3 -m pip install -r requirements.txt
python3 scripts/run_daily_scan.py
streamlit run app/streamlit_app.py
```

目前的 scan 與 dashboard 仍保留為展示型資產。  
`v1.3` 的核心價值則集中在 skill、blueprint、strategy modules、evaluation metrics、case study 與公開展示頁。

---

## English

### Cover Statement

**Taiwan Stock Radar v1.3** is a Taiwan-equity research skill built around one stock at a time. It does not stop at a loose directional opinion. It stages a formal multi-agent research meeting, selects the most appropriate strategy family, evaluates the setup through validation metrics, and returns an execution-aware decision packet.

### What Changed in v1.3

- six strategy families now sit inside the committee workflow
- two new personas were added: `Strategy Architect` and `Quant Validation Analyst`
- the output now includes strategy selection and validation panels
- tail-risk and robustness metrics were expanded beyond basic Sharpe-style reporting
- momentum-crash, volatility, event-density, and liquidity conditions can now veto or downgrade a setup

### What the Product Returns

- a weighted committee thesis
- strategy-family selection with regime fit
- specialist viewpoints across structure, flow, fundamentals, catalysts, risk, and validation
- base, bull, and bear scenarios
- preferred buy zone and alternate entry triggers
- stop-loss, take-profit ladder, and invalidation
- a validation panel with performance, tail-risk, execution, and robustness diagnostics

### Public Surfaces

- Website: [https://rabbit68116-ux.github.io/taiwan-stock-radar/](https://rabbit68116-ux.github.io/taiwan-stock-radar/)
- Case Study: [https://rabbit68116-ux.github.io/taiwan-stock-radar/case-study.html](https://rabbit68116-ux.github.io/taiwan-stock-radar/case-study.html)
- GitHub: [https://github.com/rabbit68116-ux/taiwan-stock-radar](https://github.com/rabbit68116-ux/taiwan-stock-radar)
