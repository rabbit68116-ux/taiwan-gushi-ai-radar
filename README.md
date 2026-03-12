# Taiwan Stock Radar

[![GitHub repo](https://img.shields.io/badge/GitHub-rabbit68116--ux%2Ftaiwan--stock--radar-181717?logo=github)](https://github.com/rabbit68116-ux/taiwan-stock-radar)
![Status](https://img.shields.io/badge/status-architecture%20v1.0-blue)
![Plan](https://img.shields.io/badge/plan-v1.1-orange)
![Market](https://img.shields.io/badge/market-Taiwan%20Stocks-red)
![Scope](https://img.shields.io/badge/scope-research%20%7C%20signals%20%7C%20backtest-green)

Open-source Taiwan equity analysis skill and research framework for AI agents, analysts, and developers.

> A professional Taiwan equity analysis skill that combines market surveillance, Top 20 opportunity ranking, single-stock deep dives, and risk-aware action planning.

[繁體中文](#繁體中文) | [English](#english)

---

## 繁體中文

### 展品定位

**Taiwan Stock Radar** 是一個以台灣股票市場為核心的專業分析 skill。  
它展示的不是單一選股結果，而是一套完整的方法論：如何讓 AI agent 先理解全市場，再形成研究優先順序，最後對指定股票提出更有結構的分析判斷。

這個專案的展示重點在於：

- 從約 1800 檔台股建立市場級掃描能力
- 用可解釋的排序邏輯整理 Top 20 研究候選股
- 將單股判斷擴充為 thesis、action zones、risk framing 的深度輸出
- 讓分析結果能被檢驗、討論、優化，而不是停留在模糊結論

對想做台股 AI、量化研究、回測驗證與研究工具開發的人來說，這是一個同時具備展示價值與工程延展性的專業骨架。

### 專案價值

Taiwan Stock Radar 的核心不是「預測市場一定會怎麼走」，而是展示一種更專業的分析方式：

- 先建立市場上下文，再談單一股票
- 先做研究排序，再做深度判斷
- 先定義風險，再定義機會
- 先給可執行區間，再給方向觀點

這讓它不只是選股工具，而更像一位能先觀察全市場、再對關鍵標的提出研究備忘錄的分析師。

### 核心能力

| 能力 | 說明 |
|---|---|
| Full-market scan | 掃描約 1800 檔台股，建立市場觀察起點 |
| Top 20 shortlist | 用排序邏輯整理最值得研究的候選標的 |
| Single-stock deep dive | 對指定股票輸出 thesis、context、action zones、risk framing |
| Explainable scoring | 以可拆解的因子與風險邏輯支撐排序結果 |
| Action planning | 以買入區、停損區、停利區與 invalidation structure 呈現分析 |

### GitHub 與網站

- GitHub Repo: [https://github.com/rabbit68116-ux/taiwan-stock-radar](https://github.com/rabbit68116-ux/taiwan-stock-radar)
- Public Website: [https://rabbit68116-ux.github.io/taiwan-stock-radar/](https://rabbit68116-ux.github.io/taiwan-stock-radar/)

公開網站以專業展品介紹方式呈現這個 skill，重點展示：

- 市場級掃描能力
- Top 20 候選股示意
- 單股 deep-dive 範例
- 方法論與知識庫入口

### Repo 內容

這個 repo 目前已經整理成一套可供 AI agent 直接使用與延伸的台股分析 skill：

| 路徑 | 作用 |
|---|---|
| [`SKILL.md`](./SKILL.md) | skill 的核心工作流與判斷規則 |
| [`references/taiwan-market-playbook.md`](./references/taiwan-market-playbook.md) | 台股市場特性、因子與風險規則 |
| [`references/prediction-framework.md`](./references/prediction-framework.md) | 預測輸出格式、情境推演與信心框架 |
| [`references/agent-analyst-blueprint.md`](./references/agent-analyst-blueprint.md) | 市場掃描、Top 20 與單股 deep-dive 的分析藍圖 |
| [`config/weights.yaml`](./config/weights.yaml) | 雷達評分權重設定 |
| [`config/universe.yaml`](./config/universe.yaml) | 台股掃描股票池 |
| [`config/action_rules.yaml`](./config/action_rules.yaml) | 買入區、停損、停利與 deep-dive 行動規則 |
| [`scripts/run_daily_scan.py`](./scripts/run_daily_scan.py) | daily scan demo script |
| [`app/streamlit_app.py`](./app/streamlit_app.py) | dashboard skeleton |

### 快速開始

安裝相依套件：

```bash
python3 -m pip install -r requirements.txt
```

執行 daily scan demo：

```bash
python3 scripts/run_daily_scan.py
```

啟動 Streamlit demo：

```bash
streamlit run app/streamlit_app.py
```

### 網站內容

官方網站：

- [https://rabbit68116-ux.github.io/taiwan-stock-radar/](https://rabbit68116-ux.github.io/taiwan-stock-radar/)

`taiwan-stock-radar` 的公開網站以專業展品介紹方式呈現這個台股分析 skill 的核心價值：

- 掃描約 1800 檔台股
- 排出 Top 20 候選股
- 給出方向判斷與觀察優先順序
- 定義買入區、停損區、停利區與風險框架
- 針對指定股票做更深度的單股研判

網站內容位於 `docs/`，目前主要頁面如下：

| 路徑 | 作用 |
|---|---|
| [`docs/index.html`](./docs/index.html) | 首頁，展示 skill 的定位、方法價值、Top 20 示意與單股 deep-dive 範例 |
| [`docs/faq.html`](./docs/faq.html) | FAQ 頁，附 FAQ schema |
| [`docs/methodology.html`](./docs/methodology.html) | 方法論頁，說明 1800 檔掃描、Top 20、單股 deep-dive 的流程 |
| [`docs/use-cases.html`](./docs/use-cases.html) | 使用情境頁，說明 agent 與研究者如何使用這個 skill |
| [`docs/docs.html`](./docs/docs.html) | 知識庫入口頁，整理 repo 內的重要規格、設定與腳本 |

若要更新公開網站內容，直接調整 `docs/` 下的頁面即可。

### 專案亮點

| 亮點 | 說明 |
|---|---|
| 專注台股 | 結構從第一天就以台股資料、上櫃市場、族群輪動、籌碼與市場 regime 為核心 |
| 可解釋 | 分數會拆出 Trend、Volume、Capital Flow、Quality、Sector、Market、Risk 等構面 |
| 可回測 | 所有規則預期都能落成程式化回測，而不是停留在概念描述 |
| 可展示 | 規劃包含 dashboard、heatmap、daily top 20、markdown summary 等展示層 |
| AI-ready | 預留 `model_score`、`probability`、`expected_return`、`ranking_model` 供未來 ML 擴充 |

### 使用者會得到什麼

- 一套可維護的台股研究專案結構
- 一個可逐步擴充的 feature engineering 與 scoring pipeline
- 一個可持續驗證策略的 backtest 基礎
- 一個能讓使用者快速理解市場狀態的 dashboard MVP
- 一份可每日自動輸出的 Top 20 觀測清單

### 視覺化架構圖

```mermaid
flowchart LR
    A["Market Data Sources"] --> B["Data Loader"]
    B --> C["Cleaner / Normalizer"]
    C --> D["Feature Engineering"]
    D --> E["Factor Calculation"]
    E --> F["Radar Scoring"]
    F --> G["Strategy Rules"]
    G --> H["Risk Adjustment"]
    H --> I["Signal Engine"]
    I --> J["Backtest Engine"]
    I --> K["Dashboard / Heatmap"]
    I --> L["Daily Top 20 Output"]
```

### 模組地圖

```mermaid
flowchart TB
    A["Data Layer"] --> B["Feature Layer"]
    B --> C["Factor / Scoring Layer"]
    C --> D["Strategy Layer"]
    D --> E["Signal Layer"]
    C --> F["Risk Layer"]
    E --> G["Backtest Layer"]
    E --> H["App / Visualization Layer"]
    E --> I["Output / Automation Layer"]
    F --> E
```

### 核心能力

| 模組 | 內容 |
|---|---|
| Data | 台股資料載入、來源切換、欄位標準化、驗證 |
| Features | 技術面、動能、量價、籌碼、基本面、族群、市場特徵 |
| Scoring | 100 分制雷達評分、正規化、排序與可信度處理 |
| Regime | Bull / Sideways / Bear / High Volatility 市場環境判斷 |
| Risk | 風險旗標、風險分數、停損停利、倉位過濾 |
| Signals | Strong Buy Watch / Buy Watch / Hold / Sell Watch / Risk Alert |
| Backtest | 日頻回測、交易成本、滑價、績效報表 |
| Visualization | Streamlit dashboard、sector heatmap、relative strength heatmap |
| Automation | 每日自動掃描、Top 20 匯出、GitHub Actions / cron job |

### 雷達評分概念

預設會以 100 分制處理，並保留可調權重：

| 構面 | 預設權重 |
|---|---:|
| Trend | 20 |
| Volume | 15 |
| Capital Flow | 20 |
| Quality | 10 |
| Momentum | 10 |
| Sector | 10 |
| Market | 5 |
| Risk Adjustment | -20 ~ 0 |

分數不是預測保證，而是觀測排序。  
高分代表更值得進一步研究，不代表一定上漲；低分代表風險或條件不足，不代表一定下跌。

### 預期輸出樣貌

每日掃描完成後，專案預期會輸出類似內容：

```text
Top 20 Radar Watchlist
Date: 2026-03-12

1. 2330 台積電   Radar Score: 86   Signal: Strong Buy Watch
2. 2454 聯發科   Radar Score: 83   Signal: Buy Watch
3. 2303 聯電     Radar Score: 81   Signal: Buy Watch
...
```

以及：

- `output/daily_top20.csv`
- `output/daily_top20.json`
- `output/daily_summary.md`

### 這個專案適合誰

- 想研究台股量化策略的開發者
- 想把選股流程做成資料化、規則化、可回測化的交易者
- 想建立公開作品集或金融研究 demo 的工程師
- 想把規則式框架進一步接上 LightGBM、XGBoost、ranking model 的研究者
- 想追蹤一個 AI 原生金融研究系統從架構到落地過程的使用者

### 為什麼現在值得追蹤

- 這個 repo 已經不是模糊想法，而是有完整工程藍圖與模組邊界
- 發展路線明確，後續每次更新都會是可見的實作里程碑
- 適合長期追蹤：從資料層到前端展示層都會逐步補齊
- 如果你對「AI 如何參與金融研究框架建設」有興趣，這會是一個值得觀察的公開案例

### Roadmap

**Phase 1**
- Data loader
- Feature pipeline
- Radar scoring
- Signal engine
- Basic backtest

**Phase 2**
- Streamlit dashboard MVP
- Daily auto scan
- Markdown / CSV / JSON export

**Phase 3**
- Market heatmap
- Sector rotation page
- Historical scan archive

### 發展路線圖

```mermaid
flowchart LR
    A["v1.0 Foundation"] --> B["v1.1 Visualization+"]
    B --> C["v1.2 ML Interface"]
    C --> D["v2.0 Ranking + Portfolio"]
```

### 目前狀態

目前 repo 同時包含兩個版本層：

- 架構文件：`v1.0`
- 資深分析師模式方案：`v1.1`

接下來會逐步完成：

1. repo 基礎結構
2. 資料載入與統一 schema
3. 特徵工程 pipeline
4. 因子與雷達評分
5. 訊號與回測引擎
6. dashboard、heatmap 與 daily scan

核心文件：
- [`taiwan-stock-radar-architecture-v1.0-final.md`](./taiwan-stock-radar-architecture-v1.0-final.md)
- [`references/agent-analyst-blueprint.md`](./references/agent-analyst-blueprint.md)

### 風險聲明

本專案僅供研究、教育與工程實作用途。  
所有分數、排序、訊號與回測結果均不構成投資建議或保證報酬。

---

## English

### Overview

**taiwan-stock-radar** is an open-source research framework built specifically for the Taiwan stock market.  
Its goal is not to produce opaque trading calls, but to create a research system that is explainable, backtestable, extensible, and publicly visible.

The project is designed as a full pipeline:

- ingest market data
- clean and normalize it into a unified schema
- compute technical, volume, capital-flow, fundamental, sector, and market features
- generate radar scores and ranked watchlists
- emit buy, sell, hold, and risk-alert signals
- validate rules through backtesting
- present results through dashboards, heatmaps, and daily scan outputs

For anyone building Taiwan-market AI, quant research tools, ranking systems, or public finance demos, this repository is meant to be a strong foundation rather than a loose collection of notes.

### What This Repo Now Includes

Beyond the architecture note, this repository is now being structured as a reusable skill for AI agents:

| Path | Purpose |
|---|---|
| [`SKILL.md`](./SKILL.md) | Core workflow and reasoning rules for the agent |
| [`references/taiwan-market-playbook.md`](./references/taiwan-market-playbook.md) | Taiwan-specific factor, regime, and risk logic |
| [`references/prediction-framework.md`](./references/prediction-framework.md) | Forecast formatting, scenario framing, and confidence discipline |
| [`references/agent-analyst-blueprint.md`](./references/agent-analyst-blueprint.md) | v1.1 senior-analyst blueprint for 1,800-stock scanning, Top 20 ranking, and deep-dive stock analysis |
| [`references/github-landscape.md`](./references/github-landscape.md) | Design patterns extracted from leading open-source quant repos |
| [`agents/openai.yaml`](./agents/openai.yaml) | Skill metadata for UI surfaces |
| [`config/weights.yaml`](./config/weights.yaml) | Radar scoring weights |
| [`config/universe.yaml`](./config/universe.yaml) | Scan universe configuration |
| [`config/action_rules.yaml`](./config/action_rules.yaml) | Buy zone, stop, take-profit, and deep-dive action rules |
| [`scripts/run_daily_scan.py`](./scripts/run_daily_scan.py) | First-pass daily scan demo script |
| [`app/streamlit_app.py`](./app/streamlit_app.py) | Streamlit dashboard skeleton |

This shifts the repo from a concept page into a real skill bundle that can teach an AI agent how to reason about Taiwan stocks.

### Senior Analyst Mode

The skill is being designed around a two-stage workflow:

1. Market-wide sweep
   Target roughly 1,800 Taiwan stocks, score them through regime, sector rotation, stock factors, and risk vetoes, then return a Top 20 shortlist.
2. Single-stock deep dive
   When a user names one stock, switch into memo mode with peer mapping, business support, chip flow, catalyst timing, scenario tree, and action plan.

This is the difference between a stock screener and an analyst-grade agent.

### Quick Start

Install dependencies:

```bash
python3 -m pip install -r requirements.txt
```

Run the demo daily scan:

```bash
python3 scripts/run_daily_scan.py
```

Launch the Streamlit demo:

```bash
streamlit run app/streamlit_app.py
```

### Why It Stands Out

| Highlight | Description |
|---|---|
| Taiwan-first | Built around Taiwan market structure, OTC behavior, sector rotation, capital flow, and market regimes |
| Explainable | Scores are decomposed into trend, volume, capital flow, quality, sector, market, and risk components |
| Backtest-first | Strategy logic is expected to become executable and measurable, not just conceptual |
| Demo-friendly | Planned outputs include dashboard views, heatmaps, Top 20 watchlists, and markdown summaries |
| AI-ready | Interfaces reserve room for `model_score`, `probability`, `expected_return`, and `ranking_model` |

### What Users Can Expect

- A maintainable project structure for Taiwan equity research
- A scalable feature engineering and scoring pipeline
- A backtesting foundation for validating strategy ideas
- A dashboard layer that makes market state easy to read
- A daily automated watchlist output for repeatable market scanning

### Visual Architecture

```mermaid
flowchart LR
    A["Market Data Sources"] --> B["Data Loader"]
    B --> C["Cleaner / Normalizer"]
    C --> D["Feature Engineering"]
    D --> E["Factor Calculation"]
    E --> F["Radar Scoring"]
    F --> G["Strategy Rules"]
    G --> H["Risk Adjustment"]
    H --> I["Signal Engine"]
    I --> J["Backtest Engine"]
    I --> K["Dashboard / Heatmap"]
    I --> L["Daily Top 20 Output"]
```

### Layer Map

```mermaid
flowchart TB
    A["Data Layer"] --> B["Feature Layer"]
    B --> C["Factor / Scoring Layer"]
    C --> D["Strategy Layer"]
    D --> E["Signal Layer"]
    C --> F["Risk Layer"]
    E --> G["Backtest Layer"]
    E --> H["App / Visualization Layer"]
    E --> I["Output / Automation Layer"]
    F --> E
```

### Core Capabilities

| Module | Scope |
|---|---|
| Data | Taiwan data ingestion, provider switching, schema normalization, validation |
| Features | Technical, momentum, volume, capital flow, fundamentals, sector, and market features |
| Scoring | 100-point radar scoring, normalization, ranking, and confidence handling |
| Regime | Bull, sideways, bear, and high-volatility detection |
| Risk | Risk flags, risk score, stop-loss / take-profit, position filters |
| Signals | Strong Buy Watch, Buy Watch, Hold, Sell Watch, Risk Alert |
| Backtest | Daily-frequency testing, fees, slippage, and performance reports |
| Visualization | Streamlit dashboard, sector heatmap, relative-strength heatmap |
| Automation | Daily scan, Top 20 export, GitHub Actions or cron-based scheduling |

### Radar Scoring Logic

The default scoring structure is designed around a 100-point framework:

| Component | Default Weight |
|---|---:|
| Trend | 20 |
| Volume | 15 |
| Capital Flow | 20 |
| Quality | 10 |
| Momentum | 10 |
| Sector | 10 |
| Market | 5 |
| Risk Adjustment | -20 ~ 0 |

A high score does not mean guaranteed upside.  
A low score does not mean guaranteed downside.  
The score is meant to rank research priority and market quality, not to promise returns.

### Expected Output Snapshot

```text
Top 20 Radar Watchlist
Date: 2026-03-12

1. 2330 TSMC       Radar Score: 86   Signal: Strong Buy Watch
2. 2454 MediaTek   Radar Score: 83   Signal: Buy Watch
3. 2303 UMC        Radar Score: 81   Signal: Buy Watch
...
```

Planned output files:

- `output/daily_top20.csv`
- `output/daily_top20.json`
- `output/daily_summary.md`

### Who Should Follow This

- Developers building Taiwan stock research infrastructure
- Traders who want systematic and backtestable selection logic
- Engineers building finance demos or public open-source portfolios
- Researchers who want to connect rule-based systems with LightGBM, XGBoost, or ranking models
- Anyone interested in watching an AI-native market research framework grow in public

### Why Follow or Star Now

- The project already has a concrete engineering blueprint
- The scope is broad but clearly segmented into modules and milestones
- Progress will be visible and incremental, which makes the repo easy to track
- It is an early-stage public build of a Taiwan-market AI research framework, which is still relatively rare

### Roadmap

**Phase 1**
- Data loader
- Feature pipeline
- Radar scoring
- Signal engine
- Basic backtest

**Phase 2**
- Streamlit dashboard MVP
- Daily auto scan
- Markdown / CSV / JSON export

**Phase 3**
- Market heatmap
- Sector rotation page
- Historical scan archive

### Development Timeline

```mermaid
flowchart LR
    A["v1.0 Foundation"] --> B["v1.1 Visualization+"]
    B --> C["v1.2 ML Interface"]
    C --> D["v2.0 Ranking + Portfolio"]
```

### Current Status

The repository now carries two version tracks:

- architecture document: `v1.0`
- senior-analyst operating blueprint: `v1.1`

The next implementation stages will focus on:

1. repository structure
2. data loading and unified schemas
3. feature pipelines
4. factor and radar scoring
5. signal and backtest engine
6. dashboard, heatmap, and daily scan outputs

Core documents:
- [`taiwan-stock-radar-architecture-v1.0-final.md`](./taiwan-stock-radar-architecture-v1.0-final.md)
- [`references/agent-analyst-blueprint.md`](./references/agent-analyst-blueprint.md)

### Disclaimer

This project is for research, education, and engineering purposes only.  
Scores, rankings, signals, and backtest results are not investment advice and do not guarantee returns.
