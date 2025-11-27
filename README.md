# Indian-sovereign-yield-curve-and-macro-liquidity-monitor
**The Problem Statement:**
"Monetary policy transmission—the process by which changes in the Central Bank's Policy Rate (Repo) affect the real economy—is often non-linear and subject to significant lags.
Financial analysts and risk managers face a critical data engineering challenge: RBI macroeconomic data is fragmented across disparate sources with conflicting time frequencies (Daily Money Market data vs. Ad-hoc Policy announcements vs. Monthly Bond Yields). This fragmentation creates a 'blind spot,' making it difficult to detect:
Liquidity Mismatches: When interbank lending rates (WACR) decouple from the policy anchor.
Structural Risk: When the Yield Curve inverts or flattens, signaling an impending economic slowdown.
Without a unified time-series framework, identifying these regime changes requires manual, error-prone data stitching, leading to delayed insights in a high-velocity market."

# Indian Sovereign Yield Curve & Macro-Liquidity Monitor 🇮🇳 📉

**Project Overview**
This project quantifies the transmission mechanism of the Reserve Bank of India's (RBI) monetary policy into the broader economy. By analyzing the spread between the Policy Anchor (Repo Rate) and Market Rates (WACR & G-Sec Yields), this dashboard identifies regimes of **Liquidity Stress**, **Cost of Capital Volatility**, and **Economic Slowdown signals**.

**Data Sources**
All data was sourced directly from the **RBI Database on Indian Economy (DBIE)**:
1.  **Money Market:** Daily Weighted Average Call Rate (WACR) - *The "Real" cost of overnight funds.*
2.  **Policy Rates:** MPC Voting Patterns & Historical Repo Rates - *The Central Bank's intent.*
3.  **Govt Securities:** Secondary Market Yields (SGL Transactions) for 1Y and 10Y papers.

**Technical Methodology**
The core challenge was harmonizing datasets with **conflicting time frequencies**:
* **Repo Rate:** Irregular (Changes only upon MPC meetings).
* **WACR:** Daily (Market driven).
* **Yields:** Monthly (Reporting cycle).

**The Solution:**
* Built a **Master Time-Series Index** (2020-2025).
* Applied **Forward-Fill Imputation (`ffill`)** to convert event-based Policy Rates and Monthly Yields into a continuous daily signal.
* Engineered the **Term Spread** feature (`10Y - 1Y`) to detect yield curve inversions.

**Key Financial Insights**

1. Liquidity Stress Monitor (Repo vs. WACR)
![Liquidity Chart](Chart1_Liquidity.png)
* **Insight:** During 2023-2024 (Red Zones), the Market Rate (WACR) consistently traded *above* the Policy Rate. This indicates a **Systemic Liquidity Deficit**, forcing the RBI to conduct Variable Rate Repo (VRR) auctions to inject liquidity.

2. The "Bear Flattening" (Cost of Capital)
![Yield Chart](Chart2_Yields.png)
* **Insight:** In 2022, the 1-Year T-Bill Yield (Orange Line) surged faster than the 10-Year Bond (Green Line). This "Bear Flattening" characterizes an inflation-fighting regime where short-term rates rise aggressively to curb demand.

3. The Recession Gauge (Term Spread)
![Spread Chart](Chart3_Spread.png)
* **Insight:** The spread collapsed from ~250 bps in 2020 (Growth Phase) to near zero in 2023/24 (Tightening Phase). A flattening/inverted curve historically signals a slowdown in credit growth and economic activity.

**Tech Stack**
* **Python:** Pandas (Data Cleaning), Matplotlib/Seaborn (Visualization).
* **Excel:** Initial data auditing and matrix transposition.
* **Concepts:** Time-Series Analysis, Fixed Income Analytics, Macro-Prudential Risk.


