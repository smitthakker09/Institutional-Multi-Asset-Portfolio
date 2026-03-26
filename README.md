# Institutional Multi-Asset Portfolio Framework 📈

An end-to-end quantitative research environment built in Python. This framework constructs, backtests, and evaluates a dynamic multi-asset portfolio using **Equal Risk Contribution (Risk Parity)**, an **Exponentially Weighted Moving Average (EWMA)** covariance matrix, and a **Trend-Following Circuit Breaker** to protect against severe market drawdowns.

## 📌 Project Overview
Traditional Mean-Variance Optimization (Markowitz) often acts as an "error maximizer," over-allocating to assets with recent noisy returns. This project solves that by shifting the optimization target entirely to *risk*. 

By equalizing the risk contribution of uncorrelated asset classes (Equities, Bonds, Gold, Alternatives) and overlaying a 200-day Simple Moving Average (SMA) trend filter, this strategy achieves a highly asymmetric return profile: **capturing equity-like returns with bond-like volatility and heavily constrained maximum drawdowns.**

## ⚙️ Key Features
* **Object-Oriented Architecture:** Decoupled modules for Data Handling, Mathematical Optimization, Backtesting, and Reporting.
* **Risk Parity Engine:** Uses `SciPy` to solve for weights where the marginal risk contribution of each asset equals $1/N$.
* **Dynamic Covariance:** Replaces static lookback windows with an EWMA covariance matrix (63-day half-life) to react faster to market regime changes.
* **Downside Protection:** A built-in Trend-Following overlay sweeps capital from crashing assets into a Cash proxy (T-Bills) if they fall below their 200-day SMA.
* **Realistic Friction Modeling:** Incorporates a transaction cost penalty (10-15 bps) dynamically calculated based on portfolio turnover at each rebalancing period.
* **Institutional Tear Sheet:** Generates a performance attribution report isolating the "Allocation Alpha" (Risk Parity) from the "Timing Alpha" (Trend Filter).
* **Anti-Overfitting (Sensitivity Grid):** Automatically runs a parameter grid search across different SMA windows and EWMA half-lives to prove robustness via a Seaborn heatmap.

## 🚀 Installation & Usage

**Dependencies:**
```bash
pip install pandas numpy scipy yfinance matplotlib seaborn
