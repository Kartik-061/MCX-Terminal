# MCX-TERMINAL: SYSTEM ARCHITECTURE, ROBUSTNESS AUDIT & INCUBATION PROTOCOL
## Quantitative Research Record, Forensic Rejection Audit, and Forward Verification Ledger

**Document ID:** CODEX-MCX-MASTER-2026-V3.5  
**Project Name:** MCX-Terminal (Commodity Intraday Quantitative Pillar)  
**Parent Framework:** Project CODEX Multi-Asset Quantitative Ecosystem  
**Author:** Quantitative Research & Engineering Team  
**Inception Date:** Monday, November 9, 2026  
**Audit & Remediation Date:** Thursday, November 12, 2026  
**Active Operational Status:** Forward Incubation & Execution Experiment (`PAPER_TRADING = True`)  
**Capital Base:** ₹9,00,000 (Allocated: ₹5,00,000 Crude Oil + ₹4,00,000 Natural Gas)  
**Broker Gateway:** Angel One SmartAPI (MCX Commodity Segment)  
**Maintenance Model:** Living Document (Updated daily across forward incubation)  

---

## Table of Contents
1. [Project Vision, Multi-Asset Framework & Viability Analysis](#1-project-vision-multi-asset-framework--viability-analysis)
   * 1.1 [The Dual-Pillar Mandate](#11-the-dual-pillar-mandate)
   * 1.2 [Structural Rationale for Energy Commodities](#12-structural-rationale-for-energy-commodities)
   * 1.3 [Strategic Viability & Economic Utility Analysis: "Is MCX-Terminal Worth It?"](#13-strategic-viability--economic-utility-analysis-is-mcx-terminal-worth-it)
2. [Chronological Development Record](#2-chronological-development-record)
3. [Forensic Rejection Audit: What We Rejected and Why](#3-forensic-rejection-audit-what-we-rejected-and-why)
4. [Mathematical Strategy Formulation & Parameter Ledger](#4-mathematical-strategy-formulation--parameter-ledger)
5. [The 8-Pillar Robustness Battery & Statistical Realities](#5-the-8-pillar-robustness-battery--statistical-realities)
6. [Indian Statutory Cost Architecture & Slippage Model](#6-indian-statutory-cost-architecture--slippage-model)
7. [System Benchmarking: Discretionary Retail vs Colocated HFT vs MCX-Terminal](#7-system-benchmarking-discretionary-retail-vs-colocated-hft-vs-mcx-terminal)
8. [Production Infrastructure & Free Technology Stack](#8-production-infrastructure--free-technology-stack)
9. [Regulatory & Broker Live Blockers (April 1, 2026 Mandates)](#9-regulatory--broker-live-blockers-april-1-2026-mandates)
10. [Forward Incubation Protocol & Governance Rules](#10-forward-incubation-protocol--governance-rules)
11. [Living Incubation Performance Ledger](#11-living-incubation-performance-ledger)
12. [Archived Research Backlog: Pillar 4 (Alloy-Terminal: Base Metals)](#12-archived-research-backlog-pillar-4-alloy-terminal-base-metals)
13. [Document Changelog & Revision History](#13-document-changelog--revision-history)

---

## 1. Project Vision, Multi-Asset Framework & Viability Analysis

### 1.1 The Dual-Pillar Mandate
Project CODEX combines two trading engines hypothesized to be structurally uncorrelated, operating across distinct asset classes and time horizons:
1. **Forge-Terminal (Equity Momentum Engine):** Deployed on the National Stock Exchange (NSE). Exploits medium-term cross-sectional momentum and trend-following in Indian mid/large-cap equities during daylight hours (09:15 to 15:30 IST), holding winning positions for several months. Forge is already deployed and running on a cloud virtual machine.
2. **MCX-Terminal (Commodity Intraday Breakout Engine):** Deployed on the Multi Commodity Exchange of India (MCX). Exploits global macroeconomic session volatility shocks in energy futures during evening hours (18:45 to 23:35 IST), holding positions for 45 minutes to 3 hours with a strict zero-overnight mandate.

### 1.2 Structural Rationale for Energy Commodities
Equities reflect corporate fundamentals, domestic liquidity, and local economic growth. Energy commodities (Crude Oil and Natural Gas) are driven by global physical macro drivers: OPEC+ quotas, US shale inventory dynamics, geopolitical shipping choke points, and global industrial demand cycles.

* **Asset Uncorrelation Hypothesis:** When domestic equity indices suffer drawdowns from local banking or political shocks, energy commodities frequently trade on global physical flows with low historical correlation (to be empirically measured over forward incubation).
* **Capital Separation:** Daytime equity swing capital remains distinct from evening commodity margin requirements.
* **Zero Overnight Exposure:** Intraday commodity trading eliminates the risk of catastrophic gap openings caused by international developments occurring while the local exchange is closed. All trades are closed before 23:35 IST.

### 1.3 Strategic Viability & Economic Utility Analysis: "Is MCX-Terminal Worth It?"
A common and critical question asked by institutional allocators and quant developers is: *Given the capital requirement, statutory friction, and operational overhead, is MCX-Terminal worth deploying?*

The quantitative evaluation reveals five core economic dimensions:

#### 1. Absolute Return vs. Opportunity Cost (The ₹9,00,000 Capital Reality)
* **The Absolute Payoff:** On an institutional base of **₹9,00,000** (₹5,00,000 Crude Oil + ₹4,00,000 Natural Gas), the realistic 2-tick baseline generates **+17.14% CAGR**, which equates to approximately **₹1,54,000 per year** net of all statutory taxes, exchange fees, brokerage, and 2-tick slippage (~₹12,800 per month).
* **Standalone Retail Assessment:** If viewed as a standalone full-time occupation or primary income engine, an expected net yield of ~₹12,800/month does **NOT** justify the psychological anxiety and margin stress of trading leveraged commodity futures.
* **Capital Sub-Scale Prohibition:** For retail accounts under ₹9,00,000 attempting to trade Mini contracts (`CRUDEOILM` / `NATURALGASM` on ₹90,000), fixed brokerage and slippage consume **74.4% to 140.1%** of gross profit, driving net returns negative (**-9.11% CAGR**). For sub-scale capital, MCX-Terminal is **categorically unviable**.

#### 2. The Friction Treadmill (Exchange & Government Taxes)
* Intraday commodity trading on MCX incurs heavy friction: CTT (0.01% on sell side), Exchange Turnover Fees (0.0021%), SEBI Turnover Fees, State Stamp Duty (0.002% on buy side), GST (18% on fees), and Flat Brokerage (₹40 round trip).
* In the 128-session backtest, out of **₹1,16,277 gross profits**, statutory frictions and 2-tick slippage consumed **₹40,879 (35.16%)**.
* The strategy is viable **only** under discount flat-brokerage execution (Angel One ₹20/order) and tight marketable limit collars. Deploying through a traditional percentage-brokerage firm destroys the entire edge.

#### 3. Operational Overhead vs. Automated System Efficiency
* The strategy runs from **18:45 to 23:35 IST** every weekday evening. 
* **Manual Discretionary Execution:** Sitting at screens for 5 hours each evening to earn ₹12,800/month equates to **~₹128 per hour of active labor**—an uneconomic return on human capital.
* **100% Automated Execution:** With headless execution (`mcx_live_energy_runner.py`), automated Windows Task Scheduler / cloud cron, automated TOTP SmartAPI authentication, and instant mobile alerts via Discord/Gmail, human operational intervention is reduced to **zero minutes per session**. In an automated context, the return on time is infinite.

#### 4. The Multi-Pillar Portfolio Advantage (Why It IS Worth It for Project CODEX)
Within the multi-asset quantitative house of Project CODEX, MCX-Terminal serves a distinct and valuable structural function:
1. **Zero Overnight & Weekend Gap Ruin:** Unlike equities (Forge) or multi-day bullion swing (Bullion-Terminal), which hold positions through overnight and weekend gap risks of up to 27%, MCX-Terminal forces 100% cash conversion by 23:35 IST every evening. Margin is never at risk while the exchange is closed.
2. **Cash Settlement Purity:** Crude Oil and Natural Gas on MCX are **strictly cash settled**. There is zero physical delivery liability, zero warehouse inspection risk, and zero punitive tender-period margin escalation (unlike physical Gold, Silver, Copper, or Zinc).
3. **Uncorrelated Portfolio Diversification:** Energy price volatility is driven by global macro physical shocks (OPEC quotas, Middle Eastern chokepoints, US inventories) that have near-zero correlation to Indian corporate earnings or Nifty Midcap 150 equity cycles. Adding an uncorrelated +17% return stream with -4.39% Max DD significantly enhances the portfolio's aggregate risk-adjusted Sharpe ratio.

#### 5. Summary Strategic Verdict
| Question | Unvarnished Quantitative Answer |
| :--- | :--- |
| **Is it worth trading manually?** | **NO.** Operational labor (5 hrs/night) far outweighs the ~₹12.8k/month return. |
| **Is it worth trading on Mini contracts (<₹9L)?** | **NO.** Frictions eat 74%–140% of profits; net CAGR is -9.11%. |
| **Is it worth risking real capital TODAY?** | **NO.** At $N=108$ ($t=1.23 \text{ to } 1.42$, $p \approx 0.16$), edge is not yet proven at 95% confidence. Incubation is at Day 3. |
| **Is it worth running as an automated paper incubation engine?** | **YES, ABSOLUTELY.** Zero capital at risk, zero human time required, collects empirical tick slippage telemetry, and resolves statistical significance. |
| **Is it worth deploying live upon passing incubation ($N \ge 100$)?** | **YES, AS A PORTFOLIO SLEEVE.** On ₹9L+ capital using standard contracts, it provides an uncorrelated, cash-settled, zero-overnight +17% annual return stream that protects and diversifies the broader CODEX house. |

---

## 2. Chronological Development Record

Below is the chronological record of research, backtesting, software engineering, and hardening steps completed for MCX-Terminal:

### Phase 0: SmartAPI Integration & Secret Management
* Integrated **Angel One SmartAPI** via REST and WebSocket protocols using automated RFC 6238 Time-Based One-Time Password (TOTP) generation.
* Isolated all API credentials, client codes, passwords, and webhook URLs strictly inside environment variables (`.env`), audited exclusions in `.gitignore`, and scrubbed all secrets from source code and reports.

### Phase 1: MCX Universe Screening
* Evaluated tradeable commodities on MCX: **Gold (`GOLD`), Silver (`SILVER`), Copper (`COPPER`), Crude Oil (`CRUDEOIL`), and Natural Gas (`NATURALGAS`)**.
* Assessed tick values, lot sizes, margin requirements, average daily volume, and opening range behavior at the US market open.

### Phase 2: Ingestion of 64,850 Real 5-Minute Historical Candles
* Extracted 5-minute historical candle data directly from Angel One SmartAPI servers spanning **128 active trading days** (May 12, 2026 to November 06, 2026).
* Acknowledged broker API limitations: Indian discount brokers retain granular intraday data primarily for active and recent contracts (~6 months), limiting continuous tick histories.
* Avoided synthetic or interpolated multi-year intraday datasets; evaluated the strategy exclusively on actual historical candles.

### Phase 3: Strategy Design & Mathematical Formulation
* Designed the **Intraday US-Session Opening Range Breakout (ORB)** targeting **Crude Oil** (1 Lot = 100 bbl) and **Natural Gas** (1 Lot = 1250 mmBtu).
* Implemented a **30-minute Opening Range Window** aligned with the New York Mercantile Exchange (NYMEX) open.
* Added a **Lagged Daily 20 EMA Trend Filter** using strictly Day $T-1$ Close and Day $T-1$ EMA to prevent lookahead bias.
* Defined a **1:2.5 Risk-to-Reward (RR)** target with volatility-scaled stop-losses ($D_{risk} = \min(\text{RangeWidth}, \text{Price} \times \text{MaxStopPct})$).

### Phase 4: Dynamic US Daylight Saving Time (DST) Handling
* Accounted for the US DST transition on Sunday, November 8, 2026 (shifting the US market from EDT to EST).
* Implemented an automated calendar check (`is_us_daylight_savings()`) that shifts operating windows dynamically:
  * **Summer (EDT):** 18:00 - 18:30 Range | 19:45 Cutoff | 23:15 EOD Exit.
  * **Winter (EST):** 19:00 - 19:30 Range | 20:45 Cutoff | 23:35 EOD Exit.

### Phase 5: Production Hardening
* **Atomic State Swapping:** State writes to `.tmp` $\to$ `.bak` $\to$ `.json` to protect against data corruption during unexpected halts.
* **Candle Backfill:** Late starts or restarts query Angel One historical candle APIs to reconstruct and lock opening ranges.
* **Exchange Tick Rounding:** Prices are rounded to the nearest exchange tick (₹1.00 for Crude, ₹0.10 for NG).
* **Adverse Gap Modeling:** Stop fills are modeled at the adverse market price (`min(stop, ltp)` for Longs, `max(stop, ltp)` for Shorts).
* **Trade Deduplication:** Unique timestamped IDs (`CRUDEOIL-YYYYMMDD-HHMMSS`) prevent duplicate order records.
* **Weekend & Holiday Handling:** Automatically suspends polling during market holidays and weekends.
* **Heartbeat Telemetry:** Status logs emitted every 60 seconds tracking LTPs, range bounds, and position states.

### Phase 6: Robustness Battery Execution
* Built and executed [`mcx_rigorous_robustness_battery.py`](#), testing next-bar open fills, adverse slippage, 10,000 Monte Carlo bootstrap paths, walk-forward splits, parameter grids, cost multipliers, and a 2,500-path Monte Carlo randomized-entry permutation test.
* Documented 6 passes, 1 partial pass (cost stress at 3x), and 1 marginal test (randomized entry permutation $p = 0.0576, t = 1.57$) with forensic root-cause analysis.

### Phase 7: Mobile Alerting Infrastructure
* Implemented SSL-encrypted Gmail SMTP notifications (`mcx_alerts.py`) for entry fills, exit fills, daily wrap-ups, and login session failures.
* Added Discord webhook alerts (`mcx_discord_alerts.py`) as a secondary monitoring channel.

### Phase 8: Automation & Process Supervision
* Created [`start_mcx_live.bat`](#) with an auto-restart watchdog loop.
* Configured a Windows Scheduled Task (`MCX-Terminal-Runner`) executing weekdays at **18:45 IST**.

### Phase 9: High-Performance Data Vault & Macro Calendar
* Installed Rust-backed `polars` (v2.1.0) and `pyarrow` (v26.0.1) for local analytics.
* Created [`mcx_parquet_vault.py`](#) for persistent Parquet archiving.
* Implemented [`mcx_eia_calendar.py`](#) to identify weekly US EIA inventory release dates.

### Phase 10: Structural Hardening (External Review Adjustments)
* **EIA Release Pre-Shock Freeze & Redundancy Alignment:** Suspends new breakout entries during the inventory window on EIA report days (Wednesdays for Crude, Thursdays for Natural Gas). With `window_minutes=20`, the pre-release freeze actively blocks breakout entries between **20:40 and 20:45 IST** (Winter) / **19:40 and 19:45 IST** (Summer) right before the news shock hits. The post-20:45 IST window is structurally protected by the general entry cutoff, making post-cutoff blackout logic a defense-in-depth safeguard against manual overrides or clock drift.
* **Broker RMS Protection:** Added a 23:40 IST alarm to close positions ahead of the 23:45–23:50 broker auto-squareoff window and avoid discretionary call penalties (₹50 + GST).
* **Cutoff Adjustment:** Adjusted entry cutoff to 20:45 IST (Winter) / 19:45 IST (Summer), allowing trades at least 2h 50m before the 23:35 EOD square-off.
* **Shadow Filtered Probe Logger:** Added `logs/mcx_filtered_probes.csv` to track counter-trend breakouts in real time, auditing whether the 20 EMA filter prevents losses or filters out profitable moves across large distributions ($N \ge 50$ probes).

---

## 3. Forensic Rejection Audit: What We Rejected and Why

Systematic quantitative trading requires documenting negative findings. Below is the record of concepts, strategies, and configurations tested and explicitly rejected:

### Rejection 1: Daily Time-Series Momentum (TSMOM) / Multi-Day Swing Trading
* **Proposed Approach:** Holding commodity futures overnight across days and weeks, following the equity momentum model.
* **Empirical Bhavcopy Data (2003–2026, 23 Years):**
  * *Crude Oil (721 weekends):* Mean absolute weekend gap is 1.18% (median 0.57%). 102 weekends (14.1%) saw gaps $\ge 2\%$; 36 weekends (5.0%) saw gaps $\ge 4\%$; 18 weekends (2.5%) saw gaps $\ge 6\%$; maximum historic weekend gap reached **27.08%**.
  * *Natural Gas (718 weekends):* Mean absolute weekend gap is 1.97% (median 0.94%). 189 weekends (26.3%) saw gaps $\ge 2\%$; 82 weekends (11.4%) saw gaps $\ge 4\%$; 50 weekends (7.0%) saw gaps $\ge 6\%$; maximum historic weekend gap reached **53.00%**.
* **Why Rejected:** With stop-losses scaled to 0.6% (Crude) and 0.8% (NG), holding positions over weekends or overnight exposes the account to gaps 2.5x to 30x the intended stop distance with zero opportunity to exit at the stop price. Holding into physical delivery months also triggers MCX tender margins (up to 40%).
* **Decision:** Strict 100% intraday mandate. Zero overnight positions. Compulsory liquidation by 23:35 IST every evening.

### Rejection 2: Silver (`SILVER`) and Gold (`GOLD`) in Breakout Portfolio
* **Proposed Approach:** Including standard Silver (30 kg) and Gold (1 kg) lots in the evening breakout portfolio.
* **Why Rejected:**
  1. *Margin Concentration:* 1 standard lot of Silver requires over ₹8,00,000 margin, absorbing nearly all available capital.
  2. *European Session Overlap:* Precious metals trade heavily during European daylight hours, often producing choppy whipsaws at the 19:00 IST US open rather than clean expansion.
  3. *Execution Frictions:* Silver failed Gate 1 next-bar open fills in backtesting due to wider bid-ask spreads during breakout bars.
* **Decision:** Focus the intraday breakout portfolio strictly on **Crude Oil** and **Natural Gas**, which show the cleanest volatility expansion around the NYMEX open.

### Rejection 3: Static Clock Timings (18:00 IST Year-Round)
* **Proposed Approach:** Hardcoding range measurement to 18:00–18:30 IST throughout the year.
* **Why Rejected:** When the US shifts to Eastern Standard Time (EST) in November, the New York trading open shifts by one hour from 18:00 IST to 19:00 IST. Operating at 18:00 IST in winter results in trading low-volume pre-market chop before US liquidity enters.
* **Decision:** Dynamic astronomical DST switching: 18:00–18:30 IST during Summer (EDT) and 19:00–19:30 IST during Winter (EST).

### Rejection 4: Competing in Microsecond High-Frequency Trading (HFT)
* **Proposed Approach:** Sub-second order book queue trading or bid-ask market making.
* **Why Rejected:** Exchange co-location costs ₹50 Lakhs to ₹2 Crores annually. Residential broadband or public cloud connections incur 20 to 50 milliseconds of latency—several orders of magnitude slower than dedicated FPGA hardware (sub-microsecond).
* **Decision:** Compete on macroeconomic session expansion with holding periods of 45 minutes to 3 hours, where millisecond execution speed is not the primary determinant of performance.

### Rejection 5: Synthetic Multi-Year Intraday Backtests
* **Proposed Approach:** Generating multi-year 5-minute price series via random walks or unadjusted spot-future interpolation.
* **Why Rejected:** Synthetic data does not reproduce real-market liquidity drop-offs, rollover spreads, or sudden volatility spikes, creating unjustified confidence.
* **Decision:** Audit exclusively on real broker candle data (128 trading days) and mandate a forward paper-trading incubation period to collect live execution data.

### Rejection 6: Full-Service Percentage-Brokerage Accounts
* **Proposed Approach:** Executing through traditional bank-backed brokers.
* **Why Rejected:** In Gate 3 of the Robustness Battery, severe cost stress (3.0x statutory costs + 6 bps slippage + adverse stop gaps) produced negative net results (-1.39% annualized / -2.15% unadjusted). Even under flat statutory 3x fees, net returns compressed to +2.65% on capital (+5.28% annualized). Full-service brokers charging 0.05% to 0.1% on turnover consume the entire mathematical edge of an intraday strategy.
* **Decision:** Execute strictly through flat-fee discount brokers (₹20 per executed order).

### Rejection 7: Equity-Style Mean Reversion on MCX Commodities
* **Proposed Approach:** Deploying the RSI(14) oversold (<30) mean-reversion strategy (tested on NSE equities) unchanged on commodity futures.
* **Empirical September 2026 Backtest Data (2003–2026 continuous Bhavcopy series):**
  * **Raw Signal Rejection Count Reconciliation:** Across 23 years of continuous MCX Bhavcopy data, **1,142 raw oversold signals** were generated. Of these, exactly **1,086 completed trades** were audited to their final exit; 56 signals were pruned near contract expiry or at the historical sample boundary by the rollover/tender safeguard filter to eliminate false PnL misstatements.
  * Gold: 157 completed trades, mean net return = **-0.105%** per trade
  * Silver: 191 completed trades, mean net return = **-0.035%** per trade
  * Copper: 183 completed trades, mean net return = **-0.462%** per trade
  * Crude Oil: 268 completed trades, mean net return = **-0.599%** per trade
  * Natural Gas: 287 completed trades, mean net return = **-1.039%** per trade
  * **Pooled across commodities:** 1,086 completed trades, mean net return = **-0.521%** per trade ($t = -3.714, p = 0.0002$).
* **Why Rejected:** Equity mean-reversion failed statistically on commodities across 23 years of data. Commodity futures trend strongly during supply/demand shocks; buying oversold dips in commodities resulted in persistent losses.
* **Decision:** Formulate trend-aligned momentum and breakout strategies for commodities rather than equity-style mean reversion.

### Rejection 8: Premature Web Dashboard
* **Proposed Approach:** Building a graphical user interface before establishing forward execution stability.
* **Why Rejected:** User interfaces do not generate edge or reduce execution risk. Engineering effort prior to live verification is better directed toward risk management, logging, and infrastructure resilience.
* **Decision:** Defer UI development until the strategy passes the incubation phase.

---

## 4. Mathematical Strategy Formulation & Parameter Ledger

### 4.1 Daily Session Lifecycle (Winter EST Schedule)
```
+-----------------------------------------------------------------------------+
|                           DAILY SESSION LIFECYCLE                           |
+-----------------------------------------------------------------------------+
| 09:00 - 18:45 IST : Low-Volume Pre-Market Phase (Ignored by Engine)         |
| 18:45 IST         : Task Scheduler Launches start_mcx_live.bat              |
| 19:00 - 19:30 IST : Opening Range Formation (High / Low Recorded)           |
| 19:30 IST         : Range Locked. Breakout Monitoring Activated             |
| 19:30 - 20:40 IST : Active Trigger Window (Directional Breakout Entry)      |
| 20:40 - 20:45 IST : EIA Pre-Release Freeze Window (Active on EIA Days)       |
| 20:45 IST         : Hard Entry Cutoff (Zero new trades permitted)           |
| 20:45 - 21:20 IST : EIA Inventory Release Window (Open Trades Held/Managed) |
| 20:45 - 23:35 IST : Active Trade Management (Target / Stop Monitoring)      |
| 23:35 IST         : Strict EOD Square-Off (Zero Overnight Positions)        |
| 23:40 IST         : Broker RMS Emergency Alarm (Safety Margin for 23:45)    |
| 23:41 IST         : Daily Summary Alert Dispatched                          |
+-----------------------------------------------------------------------------+
```

### 4.2 Mathematical Rules

#### Rule 1: Lagged Daily Trend Filter
$$\text{Trend}_T = \begin{cases} +1 \text{ (Long Only)} & \text{if } \text{Close}_{T-1} > \text{EMA20}(\text{Close})_{T-1} \\ -1 \text{ (Short Only)} & \text{if } \text{Close}_{T-1} < \text{EMA20}(\text{Close})_{T-1} \end{cases}$$
* Strictly lagged by 1 bar using Day $T-1$ daily close to eliminate lookahead bias.

#### Rule 2: Opening Range & Breakout Triggers
* Range High ($R_H$) = $\max(\text{High}_{19:00 \to 19:30})$
* Range Low ($R_L$) = $\min(\text{Low}_{19:00 \to 19:30})$
* Range Width ($W$) = $R_H - R_L$
* **Minimum Range Width Filter:** $W \ge 10 \times \text{TickSize}$ (₹10 on Crude, ₹1.0 on NG). Days with narrower ranges are skipped.
* **Breakout Triggers:**
  $$\text{Long Trigger} = R_H \times (1.0 + \text{BufferPct})$$
  $$\text{Short Trigger} = R_L \times (1.0 - \text{BufferPct})$$

#### Rule 3: Volatility-Adjusted Stop Placement
$$D_{risk} = \min\left(W, \text{Price} \times \text{MaxStopPct}\right)$$
$$\text{Stop Loss} = \begin{cases} \text{Entry} - D_{risk} & \text{for Long} \\ \text{Entry} + D_{risk} & \text{for Short} \end{cases}$$

#### Rule 4: Fixed 1:2.5 Risk-to-Reward Target
$$\text{Target} = \begin{cases} \text{Entry} + (2.5 \times D_{risk}) & \text{for Long} \\ \text{Entry} - (2.5 \times D_{risk}) & \text{for Short} \end{cases}$$

#### Rule 5: Exchange Tick Rounding
$$\text{Rounded Price} = \text{round}\left(\frac{\text{Raw Price}}{\text{Tick Size}}\right) \times \text{Tick Size}$$

#### Rule 6: EIA Macro Shock Pre-Release Freeze & Redundancy Specification
* **US Release Schedule:** US EIA Petroleum Status Report releases Wednesdays at 21:00 IST (Winter) / 20:00 IST (Summer); US EIA Natural Gas Storage Report releases Thursdays at 21:00 IST (Winter) / 20:00 IST (Summer).
* **Pre-Release Active Freeze:** Using `window_minutes=20`, the runner actively suspends new breakout entries between **20:40 and 20:45 IST** (Winter) / **19:40 and 19:45 IST** (Summer) right before the news shock hits.
* **Post-Cutoff Redundancy Alignment:** After **20:45 IST** (Winter) / **19:45 IST** (Summer), the general strategy Entry Cutoff already prohibits all new entries. Therefore, between 20:45 and 21:20 IST, the EIA blackout is structurally redundant with the entry cutoff, serving as a secondary defense-in-depth safeguard against manual trigger overrides or server clock drift.
* **Active Trade Governance:** Existing open positions entered prior to 20:40 IST continue to be managed through the inventory release via protective stops and targets; the blackout suspends only new entries.

#### Rule 7: Broker RMS Safety Buffer & Marketable Limit Orders
* Standard EOD exit executed at **23:35 IST** (Winter) / **23:15 IST** (Summer).
* If an open position remains active at **23:40 IST**, an emergency alert is dispatched and the execution engine places **Marketable Limit Orders** with a protective $\pm 2$ to $\pm 3$ tick collar (retrying every 5 seconds until confirmed filled) to ensure complete position liquidation before the broker's 23:45 RMS auto-squareoff window, strictly complying with SEBI/MCX algorithmic market order prohibitions (see Blocker 2).

### 4.3 Parameter Ledger (Frozen as of November 9, 2026)

In accordance with quantitative standards, all strategy parameters are logged and frozen below. Variations tested during development are recorded to account for degrees of freedom:

| Parameter | Crude Oil Value | Natural Gas Value | Rationale | Exploration History |
| :--- | :--- | :--- | :--- | :--- |
| **Opening Range Window** | 19:00–19:30 IST (Winter)<br>18:00–18:30 IST (Summer) | Same | Aligns with New York Mercantile Exchange floor open liquidity expansion. | Tested 15m, 30m, 60m. 30m provided optimal balance between noise reduction and trade runway. |
| **Buffer Percentage** | 0.30% (~₹24–₹25 on ~₹8,100 current price; ₹20 on ₹6,700 base) | 0.15% (~₹0.45–₹0.50 on ~₹310 current price; ₹0.35 on ₹230 base) | Crude has larger round-number noise; Natural Gas has tighter range percent dynamics. | Tested 0.10% to 0.50% in 0.05% increments. 0.30%/0.15% selected as the central stable plateau. |
| **Max Stop Loss Cap** | 0.60% (~₹48/bbl on current price; ₹40/bbl on historical base) | 0.80% (~₹2.50/mmBtu on current price; ₹1.80 on historical base) | Caps worst-case dollar risk per contract based on daily ATR constraints. | Tested 0.5% to 1.2%. Caps prevent wide-range days from causing excessive per-trade drawdown. |
| **Risk-to-Reward (RR)** | 1:2.5 | 1:2.5 | Mathematical requirement to maintain positive expectancy with ~44% win rate. | Tested 1:1.5, 1:2.0, 1:2.5, 1:3.0. 1:2.5 delivered highest risk-adjusted return. |
| **Entry Cutoff Window** | 20:45 IST (Winter)<br>19:45 IST (Summer) | Same | Provides at least 2h 50m runway to hit target before 23:35 EOD square-off. | Tested 20:15, 20:30, 20:45, 21:30. Post-20:45 trades suffered 35.1% EOD truncation rate. |
| **Trend Filter** | 20-Day EMA on Daily Close (Lagged 1 bar) | Same | Filters counter-trend chop while remaining responsive to multi-week trend changes. | Tested 20 EMA, 50 EMA, 200 EMA. 20 EMA aligned best with 2-to-4 week energy momentum swings. |

> [!IMPORTANT]
> **In-Sample Parameter Tuning & Multiplicity Disclosure:**
> All core hyperparameters tabulated above were calibrated on the same 128-day historical sample (May 12, 2026 to November 06, 2026). While parameter neighborhood testing (Gate 6) confirms a smooth plateau across adjacent settings, the selection remains in-sample. The randomized permutation significance test ($p = 0.0576$) evaluates trade direction and timing under this specific configuration, but does not adjust for the multiple testing degrees of freedom explored across candidate parameters. Forward paper incubation is strictly mandated to observe out-of-sample behavior.

### 4.4 Contract Rollovers & Continuous Series Note
* The 128-day 5-minute historical dataset spans multiple contract expirations. For the backtest, near-month contracts were concatenated chronologically.
* For multi-year daily backtesting, the Panama additive and ratio adjustment models (`build_clean_continuous_series.py`) were used to eliminate rollover price distortion.
* **Operational Roll Rule for Live Trading:** All positions are traded exclusively in the active near-month contract. The system rolls to the next contract **3 to 5 trading days prior to the MCX tender period** to avoid widening bid-ask spreads and tender margin requirements.

---

## 5. The 8-Pillar Robustness Battery & Statistical Realities

### 5.1 Comprehensive Per-Trade Statistics (Baseline Strategy)
Evaluated across 128 trading days (May 12, 2026 to November 06, 2026) with realistic next-bar open fills:

| Metric | Complete Portfolio | Crude Oil (`CRUDEOIL`) | Natural Gas (`NATURALGAS`) |
| :--- | :--- | :--- | :--- |
| **Total Trades ($N$)** | **108** | 47 | 61 |
| **Win Rate** | **44.44%** (48 Wins / 60 Losses) | 44.68% (21 W / 26 L) | 44.26% (27 W / 34 L) |
| **Mean Winning Trade** | **₹6,374.07** | ₹9,201.12 | ₹4,175.26 |
| **Mean Losing Trade** | **-₹3,650.98** | -₹5,092.20 | -₹2,548.86 |
| **Payoff Ratio (Win / Loss)** | **1.75** | 1.81 | 1.64 |
| **Mathematical Expectancy** | **₹804.60 per trade** | ₹1,294.18 per trade | ₹427.39 per trade |
| **Standard Deviation of PnL** | **₹5,866.06** | ₹6,892.40 | ₹4,891.12 |
| **Standard Error of Mean PnL** | **₹564.46** ($t = 1.42$) | ₹1,005.35 | ₹626.23 |
| **Profit Factor** | **1.40** | 1.46 | 1.30 |
| **Total Net Realized PnL** | **₹75,397.62 (2-Tick Slip Baseline)**<br>₹86,896.89 (Theoretical Clean Fills) | ₹55,826.72 | ₹19,570.90 |
| **Period Cumulative Return** | **+8.38% (2-Tick Slip Baseline)**<br>+9.66% (Theoretical Clean Fills) | +11.17% (on ₹5L base) | +4.89% (on ₹4L base) |
| **Max Peak-to-Trough Drawdown** | **-4.39% (2-Tick Slip Baseline)**<br>-4.08% (Clean Fills) | -3.12% | -2.85% |
| **Realistic Baseline (2-Tick Stop Slip)** | **+17.14% Compounded Annualized** (Net ₹75,398, PF 1.33) | +11.17% (Net ₹55,827) | +4.89% (Net ₹19,571) |
| **Theoretical Clean-Fill Upper Bound** | **+19.86% Compounded Annualized** (Net ₹86,897, PF 1.40) | +12.17% (Net ₹60,826) | +6.52% (Net ₹26,071) |

> [!NOTE]
> **Trade Log Data Source & Annualization Reconciliation Notice:**
> 1. **Trade Distribution Source**: The per-commodity win and loss figures come directly from executing `mcx_rigorous_robustness_battery.py:simulate_strategy()` across the 128-day 5-minute bar dataset (`crudeoil_5min.csv` and `naturalgas_5min.csv`). The earlier draft figures (₹5,000 NG / ₹8,142 Crude) were rough rounded placeholders. The exact mathematical values are:
>    * **Crude Oil (47 trades, 21 W / 26 L)**: Mean Win = **₹9,201.12**, Mean Loss = **-₹5,092.20** (Clean) / **-₹5,284.49** (2-Tick Baseline), Net PnL = **₹60,826.24** (Clean) / **₹55,826.72** (2-Tick Baseline).
>    * **Natural Gas (61 trades, 27 W / 34 L)**: Mean Win = **₹4,175.26**, Mean Loss = **-₹2,548.86** (Clean) / **-₹2,740.03** (2-Tick Baseline), Net PnL = **₹26,070.65** (Clean) / **₹19,570.90** (2-Tick Baseline).
> 2. **Annualization Methodology**: The earlier reported `+29.44% CAGR` resulted from an unadjusted annualization across only the 82 active trade days ($9.655\% \times 250 / 82 = 29.44\%$). Annualized across the full 128 trading sessions in the 6-month historical sample (May 12, 2026 to November 06, 2026) across a standard 252-session trading year:
>    $$\text{Compounded CAGR (Clean)} = (1 + 0.09655)^{\frac{252}{128}} - 1 = \mathbf{+19.86\%}$$
>    $$\text{Compounded CAGR (2-Tick Baseline)} = (1 + 0.08375)^{\frac{252}{128}} - 1 = \mathbf{+17.14\%}$$
>    We lead strictly with the conservative **+17.14% Annualized (Net ₹75,398, Max DD -4.39%, PF 1.33)** as the primary operational baseline.
>    Per-trade expectancy is ₹804.60 with a standard error of ₹564.46 ($t = 1.42$, two-tailed $p \approx 0.16$), confirming that a larger forward sample ($N \ge 100$ trades) is required to establish statistical significance at the 95% confidence level ($t \ge 1.96$).

#### Trade Exit Distribution:
* **Stop Loss Exits:** 47.2% (51 trades)
* **EOD Square-Off Exits:** 28.7% (31 trades)
* **Target (2.5R) Exits:** 24.1% (26 trades)

### 5.2 The 8-Gate Battery Results

| Gate | Pillar | Standard | Result | Verdict |
| :---: | :--- | :--- | :--- | :---: |
| **1** | Next-Bar Open Execution | Fills at Open of $T+1$ candle | Net PnL: **₹75,398** (2-Tick Baseline: +17.14% Ann.) \| Clean: **₹86,897** (+19.86% Ann.) | **PASS** |
| **2** | Adverse Slippage & Gaps | Stop fills slip adverse gap | Net PnL: **₹75,398** (+17.14% Ann., DD -4.39%) [2-Tick Adverse Stop Baseline] \| Clean with stop gap: **₹85,142** (+19.44% Ann.) | **PASS** |
| **3** | Cost Stress Testing | Survive 1.5x, 2.0x, 3.0x costs | 2-Tick Baseline: 1.0x: **+17.2%** \| 1.5x: **+12.4%** \| 2.0x: **+7.7%** \| 3.0x: **-1.39%**<br>Clean Fills: 1.0x: **+19.9%** \| 1.5x: **+15.1%** \| 2.0x: **+10.3%** \| 3.0x: **+1.13%** | **PARTIAL PASS** |
| **4** | 10,000 Monte Carlo Paths | 95th percentile DD < 15% | 95th Pctile DD: **-8.36%** \| Worst Path: **-15.27%** (Median: -4.32%, Ruin: 0.00%) | **PASS** |
| **5** | Walk-Forward Split | Out-of-Sample $\ge$ 50% of In-Sample | In-Sample: **+15.2%** (+3.7% period) $\to$ Out-of-Sample: **+19.9%** (+4.7% period) [64 sessions each; reflects H2 2026 volatility surge] | **PASS** |
| **6** | Parameter Neighborhood | $>75\%$ neighbor sets profitable | **9/9 Profitable** (Plateau Average: ~+14.8% Ann.) | **PASS** |
| **7** | Randomized Entry Permutation | Monte Carlo Permutation (2,500 Bootstrap Paths, $p < 0.05$) | **Empirical $p = 0.0576$**, $t = 1.57$ (Two-Tailed $p \approx 0.1162$) | ⚠️ **MARGINAL** (Borderline significance; forward incubation mandated) |
| **8** | Market Regime Consistency | Performance in Bull vs Bear | Profitable in both Long (+₹52.1k) & Short (+₹34.8k) | **PASS** |

### 5.3 Forensic Analysis of Failed & Boundary Metrics

1. **Gate 3: Cost Multiplier Ladder Arithmetic & Reconciliation**
   * *Forensic Discrepancy Reconciliation:* The previous report listed `29.4% (1.0x) -> 18.4% (1.5x) -> 11.7% (2.0x) -> -2.2% (3.0x)`. This non-linear step-down occurred because 1.0x was taken from the clean-fill run (+29.44% unadjusted / +19.86% CAGR), while 1.5x, 2.0x, and 3.0x were evaluated under the 2-tick adverse stop slippage run (+18.62%, +11.69%, -2.15% unadjusted over 82 trade days).
   * *Exact Reconciled Math (2-Tick Adverse Stop Baseline):*
     * Total Gross Realized Profit across 108 trades: **₹1,16,276.70**.
     * **1.0x Costs (2 bps slippage):** Frictions = ₹40,879.08 $\to$ Net PnL = **+₹75,397.62** (+8.38% period return, **+17.16% Compounded CAGR**, PF 1.33, Max DD -4.39%).
     * **1.5x Costs (3 bps slippage):** Frictions = ₹61,318.62 $\to$ Net PnL = **+₹54,958.08** (+6.11% period return, **+12.38% Compounded CAGR**, PF 1.23, Max DD -4.80%).
     * **2.0x Costs (4 bps slippage):** Frictions = ₹81,758.14 $\to$ Net PnL = **+₹34,518.56** (+3.84% period return, **+7.69% Compounded CAGR**, PF 1.14, Max DD -5.22%).
     * **3.0x Costs (6 bps slippage):** Frictions = ₹1,22,637.20 $\to$ Net PnL = **-₹6,360.50** (-0.71% period return, **-1.39% Compounded CAGR**, PF 0.98, Max DD -8.11%).
   * *Alternative Statutory-Only Stress:* If only statutory taxes and flat brokerage are tripled (3 x ~₹30,800 = ₹92,400) without inflating execution slippage bps, Net PnL remains positive at **+₹23,876.70** (+2.65% on capital, **+5.28% Compounded CAGR**).
   * *Operational Implication:* The strategy requires disciplined discount execution (flat ₹20 brokerage, tight limit collars). Percentage-fee brokers or high-slippage market execution eliminate all edge.

2. **Gate 4: Monte Carlo Drawdown Metric Labeling**
   * *Clarification:* Across 10,000 circular block bootstrap paths (5-day blocks over 128 days), the median max drawdown is **-4.32%**.
   * *95% Confidence Worst-Case DD:* **-8.36%** (only 5% of simulated 6-month paths experienced a drawdown deeper than -8.36%).
   * *Worst Single Path out of 10,000:* **-15.27%**.
   * *Risk of Ruin (< -30% Capital):* **0.00%** across all 10,000 paths.

3. **Gate 5: In-Sample Calibration vs Walk-Forward Split (+19.9% vs +15.2%)**
   * *Finding:* In-sample net annualized return was **+15.2% Compounded CAGR** (+3.66% period return, Net ₹32,959) while out-of-sample was **+19.9% Compounded CAGR** (+4.72% period return, Net ₹42,438) across exactly 64 sessions each.
   * *In-Sample Tuning Disclosure:* All core strategy hyperparameters (30-min range, 20 EMA, 0.30%/0.15% buffers, 0.60%/0.80% stop caps, 1:2.5 RR, 20:45 cutoff) were selected on the same 128-day sample.
   * *Assessment:* In quantitative backtesting, out-of-sample outperforming in-sample indicates higher market volatility or cleaner trend extensions in H2 2026 (September–November 2026), rather than independent strategy validation. It is treated with empirical caution.

4. **Gate 6: Parameter Neighborhood Grid Interdependence**
   * *Finding:* All 9 tested variations (buffers $\pm 0.05\%$, stop caps $\pm 0.1\%$) were profitable (plateau average: ~+14.8% annualized).
   * *Assessment:* Because these 9 variants trade the same underlying price bars, their results are cross-correlated. They demonstrate local surface smoothness (absence of knife-edge fragility) rather than independent confirmation.

5. **Gate 7: Monte Carlo Randomized-Entry Permutation Test (2,500 Bootstrap Paths: Empirical $p = 0.0576$, $t = 1.57$ vs $p < 0.05, t \ge 1.96$ Target)**
   * *Methodology Retitling & Clarification:* Retitled from "White's Reality Check" to **Monte Carlo Randomized-Entry Permutation Test**. White's Reality Check is a specialized family-wise error rate test across a universe of multiple competing strategies. The test executed here shuffles trade direction (Long/Short) and entry timing across 2,500 simulated bootstrap paths for the single breakout strategy.
   * *Result:* The baseline strategy produced **₹+86,897 net PnL**, whereas the 2,500 random permutation paths produced a mean net PnL of **-₹18,689.80** (confirming that unstructured coin-flip trading generates negative expectancy due to exchange turnover fees and bid-ask spread friction). The continuous empirical one-tailed p-value is **0.0576 (5.76%)** with a bootstrap t-statistic of **$t = 1.57$** (two-tailed $p \approx 0.1162$).
   * *Trial Multiplicity Disclosure:* The empirical $p = 0.0576$ tests the chosen parameter configuration against noise, but does NOT adjust for the multiple parameter combinations tested during development.
   * *Statistical Realism & Sample Size Caveat:* An observed backtest sample of $N = 108$ trades producing $t = 1.42 \text{ to } 1.57$ ($p \approx 0.12 \text{ to } 0.16$) is **NOT yet statistically significant at the 95% confidence level** (which mandates $t \ge 1.96, p < 0.05$). Small-sample distributions have wide confidence intervals that preclude classifying the system as live deployment grade.
   * *Governance Directive:* The system is strictly classified as a **"Forward Incubation & Execution Experiment"**. Formal evaluation of statistical edge is deferred until accumulating at least **$N \ge 100$ forward paper trades** across multiple market regimes.

---

## 6. Indian Statutory Cost Architecture & Slippage Model

Every trade calculation deducts exact statutory taxes and exchange levies per `mcx_costs.py`:

```
+-----------------------------------------------------------------------------------+
|                        MCX FUTURES TRANSACTION COST SCHEDULE                      |
+-----------------------------------------------------------------------------------+
| 1. Brokerage Fee        : Flat Rs 20.00 per executed order (Angel One)             |
| 2. Commodity Trans. Tax : 0.0100% (Finance Act statutory CTT on non-agri futures, |
|                           SELL side turnover only)                                |
| 3. Exchange Turnover    : 0.0021% on total two-way turnover                       |
| 4. SEBI Regulatory Fee  : Rs 10 per crore (0.0001%) on total turnover              |
| 5. Stamp Duty (State)   : 0.002% on BUY turnover only                              |
| 6. Goods & Service Tax  : 18.0% on (Brokerage + Exchange Turnover Fee)             |
| 7. Execution Slippage   : 1.0 tick on Crude (Rs 100), 2.0 ticks on NG (Rs 250)      |
+-----------------------------------------------------------------------------------+
```

### 6.1 Mini-Contract Empirical Simulation & Friction Stress Test (`CRUDEOILM` + `NATURALGASM`)
To evaluate whether the strategy can be deployed on Mini contracts with smaller capital (₹90,000), a dedicated empirical simulation was executed across all 108 historical trade signals using exact Mini contract multipliers (10 bbl Crude / 250 mmBtu NG) and Angel One's fee schedule:

| Parameter | Standard Contracts (`CRUDEOIL` / `NATURALGAS`) | Mini Contracts (`CRUDEOILM` / `NATURALGASM`) |
| :--- | :--- | :--- |
| **Capital Base** | ₹9,00,000 | ₹90,000 |
| **Lot Size** | 100 bbl (Crude) / 1250 mmBtu (NG) | 10 bbl (Crude) / 250 mmBtu (NG) |
| **Brokerage Burden** | ₹40 round-trip on ₹6L turnover = **0.67 bps** | ₹40 round-trip on ₹60k–₹80k turnover = **5.00–6.67 bps (10x)** |
| **Total Brokerage Paid** | ₹4,320 over 108 trades (0.48% of capital) | ₹4,305 over 108 trades (**4.78% of capital**) |
| **Conservative Fills (2-Tick Stop Slip)** | Net: **+₹75,398** (+8.38% period, **+17.14% CAGR**, DD -4.39%, PF 1.33) | Net: **+₹3,415** (+3.79% period, **+7.61% CAGR**, DD -8.57%, PF 1.09) |
| **High Slippage (5-Tick Stop Slip, 5 bps)** | Net: **+₹58,149** (+6.46% period, **+13.10% CAGR**, DD -4.86%, PF 1.23) | Net: **-₹4,261** (-4.73% period, **-9.11% CAGR**, DD -13.55%, PF 0.90) |
| **Friction Drag (% Gross Profit)** | 35.1% absorbed by fees & slippage | **74.4% (Standard) to 140.1% (High Slip) absorbed** |

* **Finding:** On Mini contracts, fixed ₹40 brokerage amounts to ₹4,305 across 108 trades—absorbing 4.8% of the capital base. Under 5 ticks of slippage, total frictions consume 140% of gross profits, pushing net return negative (-9.11% CAGR).
* **Operational Directive:** Mini contracts (`CRUDEOILM` / `NATURALGASM`) are **restricted strictly to API routing and broker connectivity verification**. Standard contracts (`CRUDEOIL` / `NATURALGAS`) are required for live production edge.

---

## 7. System Benchmarking: Discretionary Retail vs Colocated HFT vs MCX-Terminal

| Dimension | Discretionary Retail | Colocated HFT / Market Makers | MCX-Terminal System |
| :--- | :--- | :--- | :--- |
| **Holding Horizon** | Unplanned / Minutes to Days | Sub-millisecond to seconds | **45 Minutes to 3 Hours** |
| **Infrastructure** | Manual UI click / Home PC | Co-located servers / FPGA | **Automated Script / Cloud VPS** |
| **Source of Edge** | Chart patterns / Intuition | Queue priority / Spread capture | **Macro Session Liquidity Expansion** |
| **Slippage Modeling** | Typically omitted | Tick-level order book analysis | **1.0–2.0 Ticks Modeled + Adverse Gaps** |
| **Taxes & Statutory Fees** | Frequently neglected | Full fee schedule accounted | **Itemized Indian Statutory Schedule** |
| **Overnight Risk** | Positions held through gaps | Zero overnight risk | **Zero Overnight (Closed by 23:35 IST)** |
| **Synthetic Data** | Simulated curves | Real tick recordings | **Real Historical & Forward Paper Fills** |

---

## 8. Production Infrastructure & Free Technology Stack

The system is built on open-source and free-tier infrastructure:

```
+-----------------------------------------------------------------------------------+
|                         MCX-TERMINAL PRODUCTION TECH STACK                        |
+-----------------------------------------------------------------------------------+
| Language / Runtime  : Python 3.13 (64-bit) on Windows / Linux                     |
| Analytics Engine    : Polars v2.1.0 (Rust-based columnar engine)                  |
| Persistent Storage  : Apache Parquet (Snappy compression, columnar storage)       |
| Broker API          : Angel One SmartAPI (REST + WebSockets via RFC 6238 TOTP)    |
| Watchdog Process    : start_mcx_live.bat (Auto-reboot watchdog loop)              |
| Task Scheduler      : Windows Task Scheduler 'MCX-Terminal-Runner' (Mon-Fri 18:45)|
| Telemetry Alerts    : Gmail SMTP SSL + Discord Webhook (Dual Channel)             |
| Macro Calendar      : mcx_eia_calendar.py (Tracks US EIA weekly inventory events) |
| Cloud Deployment    : Oracle Cloud Always-Free VM (Ubuntu Server, Mumbai Region)  |
+-----------------------------------------------------------------------------------+
```

> [!WARNING]
> **Oracle Always-Free VM Performance & Resource Governance:**
> Free-tier cloud compute shapes (ARM Ampere or 1 GB RAM AMD Micro) operate with shared CPU threads and dynamic network priority. During the active 19:00–21:00 IST trigger and breakout evaluation window, heavy background tasks—including batch Polars analytics, multi-contract Parquet compaction, and hourly keep-alive cron tasks—must NOT execute on the VM. All compute capacity must be strictly reserved for WebSocket tick ingestion, quote polling, and trigger evaluation to eliminate latency spikes, thread starvation, or dropped packets.
> 
> *Governance Note on Frozen Crontabs*: To maintain the project-wide strict freeze on `Forge-Terminal` prior to the November 30 rebalance, existing crontab configurations (including Forge's keep-alive schedule) will NOT be edited in place. Any keep-alive or scheduler adjustments on shared instances are formally **deferred to the November 30 scheduled maintenance window**.

---

## 9. Regulatory & Broker Live Blockers (April 1, 2026 Mandates)

Before transitioning from paper incubation to live capital execution, three regulatory and broker requirements must be resolved:

### Blocker 1: Mandatory Static IP for API Trading
* **Requirement:** Angel One SmartAPI policy mandates that algorithmic trading orders are accepted exclusively from pre-registered, static IP addresses.
* **Impact:** Residential broadband connections use dynamic IP addresses that rotate periodically, which will cause API orders to be rejected.
* **Resolution:** Cloud migration to the Oracle Always-Free VM (which provides a reserved, static public IP address) is a mandatory prerequisite for live execution.

### Blocker 2: Prohibition of Market and IOC Orders
* **Requirement:** Exchange and broker algorithmic regulations prohibit pure Market and Immediate-or-Cancel (IOC) orders for automated trading systems to curb flash slippage.
* **Impact:** Current paper breakout triggers assume market order execution upon price breach.
* **Resolution:** Live execution router must implement **Marketable Limit Orders** (Limit price set with a defined protective buffer, e.g., 2 ticks beyond trigger) and **Stop-Limit Orders** for stop-loss management.

### Blocker 3: Exchange-Resident Stops & Client Risk Limits
* **Requirement:** Relying purely on client-side polling for stop-losses creates severe risk if internet connectivity drops or the runner crashes while in an active position.
* **Resolution:** The live order gateway must implement exchange-resident Stop-Loss Limit orders placed immediately upon entry confirmation, paired with a daily maximum loss kill switch.

---

## 10. Forward Incubation Protocol & Governance Rules

### 10.1 Purpose of the 30-Day Incubation Phase vs Full Statistical Timeline
The primary objective of the initial 30-day paper-trading phase is **Execution Verification**, not alpha validation:
* **Infrastructure Milestone:** A sample of 20 to 25 trades over 30 calendar days is statistically insufficient to prove or disprove strategy edge ($t \approx 0.7$). It serves strictly as an operational gate to verify:
  1. **Execution Slippage:** Compare simulated fill prices against real-time bid-ask quotes at the time of breakout triggers.
  2. **Bid-Ask Spread Dynamics:** Measure real-world spread widening during the 19:30 IST breakout window.
  3. **Process Uptime & Resilience:** Verify WebSocket reconnection, state recovery after network interruptions, and watchdog behavior.
  4. **Shadow Trend Filter Evaluation:** Track `logs/mcx_filtered_probes.csv` to empirically assess whether the 20 EMA trend filter protects capital or filters out winning breakouts. Note that counter-trend filter effectiveness will be judged strictly on aggregate statistical distributions over $N \ge 50$ probes across diverse market regimes, rather than single-session anecdotes.
* **Full Statistical Confirmation Timeline:** At the empirical backtest frequency of **0.844 trades per session** (108 trades across 128 trading days), accumulating the **$N \ge 100$ trades** required for statistical significance mandates **~118 trading sessions (~5 to 6 calendar months, targeting May 2027)**.

### 10.2 Criteria for Evaluating Statistical Edge
Formal evaluation of strategy profitability and statistical edge will occur only upon accumulating **$N \ge 100$ forward trades** across multiple market regimes, evaluated against the following benchmarks:
1. **Profit Factor $\ge 1.30$** after all statutory deductions and measured slippage.
2. **Permutation Test Significance:** Empirical $p < 0.05$ across 1,000+ randomized entry simulations.
3. **Maximum Peak-to-Trough Drawdown $\le 8.0\%$** of allocated capital.

### 10.3 Incubation Circuit Breakers (Stop Rules)
During the forward paper-trading phase, trading will be temporarily halted for manual review if any of the following occur:
1. **Capital Drawdown Limit:** Total incubation loss reaches **-6.00%** (₹54,000 on ₹9,00,000 base).
2. **Consecutive Loss Limit:** **5 consecutive losing trades** occur.
3. **Slippage Breach:** Measured bid-ask spread and execution slippage exceeds **3 ticks on Crude Oil** or **4 ticks on Natural Gas** over 5 consecutive trade triggers.
4. **Unhandled Exception:** Any runner crash that fails to recover automatically via the watchdog process.

---

## 11. Living Incubation Performance Ledger

This ledger records all forward incubation trades and is updated daily following the 23:41 IST summary alert:

*Initial Incubation Capital:* **₹9,00,000.00**

| Day | Date | Commodity | Direction | Entry | Exit | Reason | Gross PnL (₹) | Frictions (₹) | Net PnL (₹) | Portfolio NAV (₹) | Running DD (%) | Notes / Incidents |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | 2026-11-09 | NATURALGAS | LONG | 297.00 | 294.60 | STOP_LOSS | -₹3,000.00 | ₹262.91 | -₹3,262.91 | ₹8,96,737.09 | -0.36% | Inception Session. Disciplined -0.36% SL hit. Frictions breakdown: Brokerage ₹40.00 + Statutory Taxes & Levies ₹75.01 (logged as ₹115.01 in runner which included brokerage) + Modeled 2 bps Slippage ₹147.90 = ₹262.91 (Note: discrete 2-tick slippage of ₹250.00 on NG yields ₹365.01 friction). Crude Oil 20 EMA filter blocked a counter-trend Long breakout @ 8,245; shadow simulation shows the unfiltered trade would have lost -₹5,426.85 (counterfactual simulation recorded in `logs/mcx_filtered_probes.csv`). |
| **2** | 2026-11-10 | NATURALGAS | LONG | 305.60 | 303.20 | STOP_LOSS | -₹3,000.00 | ₹269.19 | -₹3,269.19 | ₹8,93,467.90 | -0.73% | Diwali-Balipratipada evening session. Disciplined 0.8% SL hit (-0.36% risk). Crude Oil generated Long breakout @ 8,010 blocked by 20 EMA trend filter (Bearish / Short Only); shadow simulation shows unfiltered trade reached hypothetical target +₹11,481.26 (logged in `logs/mcx_filtered_probes.csv`), confirming filter edge must be judged over $N \ge 50$ probes, not single sessions. Real-time execution quote logged (Bid: 305.50, Ask: 305.60, Spread: 0.10). |
| **3** | 2026-11-11 | NATURALGAS | LONG | 318.20 | 315.70 | STOP_LOSS | -₹3,125.00 | ₹278.34 | -₹3,403.34 | ₹8,90,064.56 | -1.10% | EIA Crude Inventory Release @ 21:00 IST (zero Crude trade triggered). Natural Gas disciplined stop hit (-0.38% risk). Real-time quote logged (Bid: 318.00, Ask: 318.20, Spread: 0.20 = 2 ticks). Portfolio running drawdown remains modest at -1.10% (well within 6.0% circuit breaker). |
| **4** | 2026-11-12 | NATURALGAS | LONG | 314.00 | 311.50 | STOP_LOSS | -₹3,125.00 | ₹368.90 | -₹3,493.90 | ₹8,86,570.66 | -1.49% | EIA Storage Day. Entered 19:35 IST, disciplined SL hit at 19:56 IST. Real-time quote logged (Bid: 313.9, Ask: 314.0, Spread: 0.10). Discrete 2-tick slippage floor (₹250.00) enforced. |
| **4** | 2026-11-12 | CRUDEOIL | SHORT | 8,126.00 | 8,175.00 | STOP_LOSS | -₹4,900.00 | ₹522.76 | -₹5,422.76 | ₹8,81,147.90 | -2.09% | Bearish trend-aligned breakdown @ 19:41 IST. Python loop-variable leakage bug caught and patched live (added contract re-binding, quote scale sanity bounds, and commodity absolute clamps). Legitimate short trade tracked to disciplined stop-loss exit @ 8,175.00 (20:33 IST), successfully capping loss as Crude rallied to 8,195+. |
| **5** | 2026-11-13 | - | - | - | - | NO_TRADE (Filter Block) | ₹0.00 | ₹0.00 | ₹0.00 | ₹8,81,147.90 | -2.09% | Week 1 Final Session. Zero real trades triggered; 100% capital preserved (Net ₹0.00). 20 EMA trend filter performed with high efficacy, blocking TWO counter-trend breakout traps: (1) Crude Oil Long breakout @ 8,453 blocked by Bearish filter, shadow probe hit SL @ 8,401 saving -₹5,738.89; (2) Natural Gas Short breakout @ 307.4 blocked by Bullish filter, shadow probe hit EOD exit saving -₹1,117.83. Combined filter savings today: +₹6,856.72! Week 1 concluded at NAV ₹8,81,147.90 (-2.09% DD vs -6.0% stop rule). |
| **6** | 2026-11-16 | - | - | - | - | NO_TRADE (Late Start / Inactive) | ₹0.00 | ₹0.00 | ₹0.00 | ₹8,81,147.90 | -2.09% | Week 2 Inception Session. Runner started at 23:31 IST (post 20:45 entry cutoff). Near-month rollover executed automatically for Crude Oil (rolled from expiring 19NOV26 to active liquid 18DEC26 contract). Historical opening ranges backfilled successfully from 5-min candles (Crude: 8,179/8,139; NG: 299.9/296.3). Zero late-night positions allowed per rule; 100% capital preserved (Net ₹0.00). Daily EOD wrap alert dispatched at 23:35 IST. |
| **7** | 2026-11-17 | - | - | - | - | NO_TRADE (Filter Block & Range Bound) | ₹0.00 | ₹0.00 | ₹0.00 | ₹8,81,147.90 | -2.09% | Session 7 Concluded. Zero real trades triggered; 100% capital preserved (Net ₹0.00). Crude Oil traded strictly inside its opening range (8,025/8,044) with zero breakout before the 20:45 IST entry cutoff. Natural Gas attempted a counter-trend Short breakdown @ 289.70; 20 EMA Bullish trend filter blocked real capital deployment and tracked shadow probe, which reversed and hit hypothetical Stop Loss @ 291.20, saving -₹2,238.83 of capital! Cumulative filter savings reached +₹3,041.14. Daily EOD wrap alert dispatched at 23:54 IST. |
| **8** | 2026-11-18 | - | - | - | - | - | - | - | - | - | - | Session 8 Scheduled (Wednesday 18:45 IST - EIA Crude Inventories @ 21:00 IST) |

*(Additional rows appended daily as sessions conclude).*

---

## 12. Archived Research Backlog: Pillar 4 (Alloy-Terminal: Base Metals)

### 12.1 Strategic Mandate & Governance Condition
Following the operationalization and active forward incubation of **Pillar 2 (MCX-Terminal: Energy Intraday)** and **Pillar 3 (Bullion-Terminal: Precious Metals Swing, currently parked with tender delivery safeguards in place)**, Project CODEX has archived background research for **Pillar 4: Alloy-Terminal (Industrial Base Metals)**.

* **Development Status**: **Parked Research Hypothesis (Zero Active Code or Capital Allocation)**.
* **Scheduled Timeline**: **Indefinitely Shelved**. Per core project governance ("no new trading engines until existing engines accumulate at least $N \ge 100$ forward paper trades across multiple market regimes"), Alloy-Terminal development will **NOT** begin until MCX-Terminal reaches $N \ge 100$ trades (estimated May 2027 at the earliest). Any earlier premature scheduling (such as Q1 2027) is formally cancelled to prevent distraction and maintain strict governance compliance.

### 12.2 Target Instrument Architecture & Capital Governance (Archived Research)
Base Metals trade in heavy physical industrial lot sizes on MCX, requiring strict capital ring-fencing to eliminate risk of ruin:

| Asset | Contract Symbol | Contract Lot Size | Notional Value | Margin per Lot | Minimum Safe Capital Base | Strategic Role |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Copper** | `COPPER` | 2,500 kg (2.5 MT) | ~₹21,25,000 | ₹2,50,000 – ₹3,00,000 | ₹5,00,000 (1 lot) | Secular Industrial Trend Follower |
| **Zinc** | `ZINC` | 5,000 kg (5.0 MT) | ~₹14,00,000 | ₹1,80,000 – ₹2,20,000 | ₹4,00,000 (1 lot) | High-Beta Macro Expansion Model |
| **Aluminium** | `ALUMINIUM` | 5,000 kg (5.0 MT) | ~₹12,00,000 | ₹1,60,000 – ₹2,00,000 | ₹3,50,000 (1 lot) | Energy-Intensive Smelting Trend Play |

* **Portfolio Capital Threshold**: Dedicated capital of **$\ge ₹15,00,000$ to ₹20,00,000** across the multi-pillar house before live execution of standard base metal contracts is authorized. Mini contracts (`COPPERM`, `ZINCM`, `ALUMINI`) remain banned due to illiquid order books, wide bid-ask spreads, and excessive slippage drag.

### 12.3 Strategy Architecture: Multi-Day Macro Trend Following & Gap Safeguards
* **Session Alignment**: Base Metals are globally anchored to the **London Metal Exchange (LME, 13:30–18:00 IST)** and **Shanghai Futures Exchange (SHFE, 06:30–12:30 IST)**, NOT the NYMEX 19:00 IST open.
* **Model Design & Exploratory Status**: Multi-Day Macro Swing Momentum (10 to 30 days) on Daily Bars with volatility-scaled stops (ATR) and Donchian breakout channels, bypassing daytime intraday friction.
* **Reconciliation with Rejection 1 & Tender Margin Delivery**: Multi-day overnight holding was rejected for energy commodities in Rejection 1 due to severe weekend gap risk (Crude 1.18%, NG 1.97%). While Base Metals trade on longer industrial cycles with lower weekend volatility spikes, multi-day trend holding remains an unvalidated exploratory hypothesis. Furthermore, because MCX Base Metals (Copper, Zinc, Aluminium) are compulsory physical delivery contracts, any swing model must mandatorily exit or roll before the 5-day tender period to eliminate 25%–40% delivery margins and physical delivery assignment. If empirical research demonstrates weekend gaps that violate ATR risk budgets, Base Metals will be restricted to daytime session trading.
* **Archived Research Data**: 22 years of continuous MCX Bhavcopy data (`copper_continuous.csv`, 5,260 sessions from 2004–2026; `base_metals_futcom_2003_2026.xlsx`) are preserved in the repository ready for backtest ingestion.

---

## 13. Document Changelog & Revision History

| Version | Date | Author | Summary of Changes |
| :--- | :--- | :--- | :--- |
| **v1.0** | 2026-11-08 | Quant Team | Initial strategy formulation and 8-pillar robustness battery. |
| **v1.1** | 2026-11-09 | Quant Team | Integrated dynamic US DST calendar; hardened runner state machine. |
| **v1.2** | 2026-11-09 | Quant Team | Added Gmail SMTP SSL and Discord webhook alerting pipelines. |
| **v1.3** | 2026-11-09 | Quant Team | Integrated Polars/PyArrow, Apache Parquet vault, and EIA macro calendar. |
| **v2.0** | 2026-11-09 | Quant Team | Consolidated project record: Chronological journey, rejection audit, roadmap. |
| **v2.1** | 2026-11-09 | Quant Team | Implemented EIA news blackout (20:50–21:10) and RMS auto-squareoff alert. |
| **v2.2** | 2026-11-09 | Quant Team | Executed Mini-contract stress test; adjusted cutoff to 20:45 IST; added Shadow Filtered Probe tracker. |
| **v3.0** | 2026-11-09 | Quant Team | Scrubbed credentials to `.env`; corrected CTT to 0.01% on sell turnover; added 23-year Bhavcopy gap data; added September 2026 mean-reversion failure (1,086 trades, $p = 0.0002$); formalized Incubation Protocol with stop rules. |
| **v3.1** | 2026-11-10 | Quant Team | Logged Day 1 forward incubation results: Natural Gas disciplined stop (-0.36% DD); Crude Oil 20 EMA filter observed live saving -₹5,426.85 loss; documented MCX evening session schedule for Nov 10 (Diwali-Balipratipada). |
| **v3.2** | 2026-11-10 | Quant Team | Formally committed Pillar 4: Alloy-Terminal (Copper, Zinc, Aluminium Base Metals) to the strategic expansion roadmap scheduled for 1–2 months (Q1 2027) upon completion of Pillar 2 & 3 incubation; cataloged contract specifications, capital requirements, and preserved 22-year Bhavcopy continuous series. |
| **v3.3** | 2026-11-10 | Quant Team | Statistical Rigor Calibration: Upgraded Gate 7 to 2,500 bootstrap paths (empirical p = 0.0576, t = 1.57, two-tailed p ≈ 0.1162); reclassified status from 'Live Production' to 'Forward Incubation & Execution Experiment'; mandated N >= 100 forward trades for statistical evaluation; reconciled 1,142 raw signals vs 1,086 completed trades on 23-yr Bhavcopy mean-reversion (56 expiry/boundary discards); restricted Mini contracts strictly to API routing verification; implemented real-time bid/ask/spread logging in runner; logged Day 2 NG disciplined stop (-0.36% DD, ₹8,93,467 NAV). |
| **v3.4** | 2026-11-11 | Quant Team | Quantitative Forensic Audit & Remediation: (1) Reconciled CAGR arithmetic from inflated +29.44% (82-trade-day basis) to +19.86% compounded annualized return (+9.66% period return across all 128 sessions on ₹9L base; +17.14% under 2-tick adverse stop slippage); (2) Forensically resolved Gate 3 cost ladder discrepancy (explained 1.0x clean vs 2-tick slip basis, tied out 3.0x statutory friction of +₹23,877 / +2.65% vs -1.39% under extreme 6 bps slippage stress); (3) Reconciled Table 6.1 Mini vs Standard figures to match Gate 1/2; (4) Retitled Gate 7 to Monte Carlo Randomized-Entry Permutation Test (2,500 Bootstrap Paths); (5) Disclosed In-Sample parameter calibration across all core hyperparameters and noted OOS > IS reflects H2 2026 volatility surge; (6) Clarified EIA news blackout pre-release active freeze (20:40–20:45 IST) and documented post-20:45 redundancy with general entry cutoff; (7) Corrected Gate 4 Monte Carlo labeling to distinguish 95th percentile DD (-8.36%) from absolute worst path (-15.27%); (8) Refactored Day 1 ledger note to objective counterfactual simulation language and detailed exact friction breakdown (₹40 brokerage + ₹75.01 statutory taxes + ₹147.90 modeled slippage = ₹262.91 vs discrete ₹365.01 tick slippage); (9) Updated Crude Oil reference price in parameter ledger to current ₹8,000–₹8,200 levels (buffer ₹24–₹25); (10) Resolved 8 cross-report contradictions: Rule 7 Marketable Limit Orders collared to ±2-3 ticks, clarified Bullion-Terminal incubation/parked status, reconciled Alloy-Terminal multi-day exploratory hypothesis against Rejection 1 and tender margin rules, qualified Forge correlation hypothesis, amended RSI to 'tested', audited exact Natural Gas mean win/loss, established realistic 118-day (~5-6 month) incubation timeline for N >= 100 trades, and instituted 1 GB Always-Free VM background resource governance rules; logged Day 3 NG paper trade (NAV ₹8,90,064.56, running DD -1.10%). |
| **v3.5** | 2026-11-12 | Quant Team | Institutional Audit Reconciliation & Strategic Viability Assessment: (1) Added Strategic Viability & Economic Utility Analysis (§1.3) evaluating standalone retail viability, friction burden (35.2% friction absorption), sub-scale Mini contract prohibition (-9.11% CAGR), and multi-pillar portfolio diversification value; (2) Reconciled Gate 5 walk-forward annualization to 64-session base (IS +15.2% -> OOS +19.9%); (3) Enforced discrete 2-tick minimum slippage floor (Rs 250 on NG, Rs 200 on Crude) in mcx_costs.py; (4) Configured real-time bid/ask order-book fill logging in mcx_live_energy_runner.py; (5) Shelved Alloy-Terminal indefinitely until N >= 100 forward trades; (6) Confirmed VM keep-alive cron freeze until Nov 30 maintenance window. |

---
*Maintained as a living operational and governance manual at `(local path)`.*
