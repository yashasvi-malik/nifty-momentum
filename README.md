# Cross-Sectional Momentum on Nifty 200

A backtested systematic equity strategy in Python.

## Hypothesis
Stocks with the highest returns over the past 12 months (excluding the most recent month) tend to outperform the following month. Buying the top decile monthly beats the Nifty on a risk-adjusted basis after costs.

## Results (2010–2025, net of 0.20% transaction costs)

| Strategy | CAGR | Sharpe | Max Drawdown | Turnover |
|---|---|---|---|---|
| Momentum long-only top decile | 31.9% | 1.42 | -22.7% | 27.2% |
| Nifty 50 benchmark | 11.0% | 0.72 | -29.3% | — |
| Long-short spread | 8.0% | 0.45 | -39.0% | 27.2% |

## Method
- Universe: 113 Nifty-listed large-cap stocks
- Signal: 12-1 month momentum (past 12 months return, skip most recent month)
- Portfolio: Top 10% by momentum, equal weighted, monthly rebalance
- Costs: 0.20% one-way, scaled by actual turnover
- Data: Yahoo Finance via yfinance, 2010–2025

## Key findings
- Momentum delivered 31.9% CAGR vs 11.0% for the Nifty
- Sharpe ratio nearly doubled: 1.42 vs 0.72
- Lower maximum drawdown than the index: -22.7% vs -29.3%

## Limitations
- Survivorship bias: universe uses today's list, not historical membership
- Cost model is simplified: ignores market impact on illiquid stocks
- No shorting constraints modelled in the long-short spread

## Data
Yahoo Finance (yfinance). Free, adjusted for splits and dividends.

## How to run
1. Install Python 3 and run: pip install notebook yfinance pandas numpy matplotlib
2. Open: jupyter notebook momentum_backtest.ipynb
3. Run all cells top to bottom
