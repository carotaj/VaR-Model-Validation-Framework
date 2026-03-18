# VaR-Model-Validation-Framework


A Python/Jupyter project for **independent validation of Value-at-Risk (VaR) models** on a multi-asset portfolio.  
The framework compares three common VaR methodologies:

- Historical Simulation VaR
- Parametric / Variance-Covariance VaR
- Monte Carlo VaR with GARCH volatility forecasts

The project also includes formal **backtesting** and validation logic through:
- Kupiec Unconditional Coverage Test
- Christoffersen Independence Test
- Breach analysis and model comparison

---

## Project Objective

The goal of this project is to reproduce, in a simplified but realistic way, the workflow of a **quantitative model validation analyst** working in market risk / model risk management.

Instead of just building one risk model, the project focuses on:
- comparing alternative VaR methodologies,
- testing their assumptions,
- evaluating how well they perform out-of-sample,
- identifying their weaknesses and limitations,
- and documenting findings.

This makes the project closer to a **model validation exercise** than to a standard portfolio analytics notebook.

---

## Main Features

- Construction of a multi-asset portfolio from market data
- Return cleaning and exploratory data analysis
- Estimation of:
  - Historical Simulation VaR
  - Parametric VaR
  - Monte Carlo VaR
- Volatility forecasting with **GARCH**
- Rolling out-of-sample backtesting
- Statistical validation tests
- Visualization of:
  - return distributions,
  - volatility clustering,
  - VaR time series,
  - breach events,
  - model comparison tables

---

## Methodology

### 1. Data Collection
The project uses historical market data for a portfolio of assets / ETFs and computes daily returns.

### 2. Exploratory Analysis
The notebook investigates the empirical properties of returns, including:
- fat tails,
- non-normality,
- volatility clustering,
- and changing dependence across assets.

### 3. VaR Models
Three VaR approaches are implemented:

#### Historical Simulation
Uses the empirical distribution of past returns to estimate the loss quantile.

#### Parametric VaR
Assumes a distributional form for returns, typically based on mean and volatility estimates.

#### Monte Carlo VaR with GARCH
Forecasts conditional volatility using GARCH and simulates future return paths to estimate VaR.

### 4. Validation and Backtesting
Each model is evaluated through rolling out-of-sample forecasts and compared using:
- observed violation frequency,
- Kupiec test,
- Christoffersen test,
- and qualitative interpretation of where the model performs well or fails.

---

## Repository Structure

```text
.
├── notebooks/
│   └── VaR_Model_Validation_Framework
│   └── VaR_Section2_Exploratory_Analysis
│   └── VaR_Section3_Theory
│   └── VaR_Section4_Model_Implementation
│   └── VaR_Section5_Backtesting
├── data/
│   └── data_portfolio_returns.csv
│   └── data_prices_clean.csv
│   └── data_returns.csv
│   └── results_var_estimates.csv
├── images/
│   └── 01_price_paths_and_returns.png
│   └── 02_acf_comparison.png
│   └── 02_correlation_heatmap.png
│   └── 02_histograms_normal_overlay.png
│   └── 02_normality_summary.png
│   └── 02_qq_plots.png
│   └── 02_rolling_vol_per_asset.png
│   └── 02_rolling_volatility.png
├── README.md
├── LICENSE
└── .gitignore
