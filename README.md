# Cross-Sectional Momentum — Nifty Large-Cap Universe

A backtested systematic equity strategy in Python.

> Survivorship bias present. Educational project only. Not investment advice.
> Data: Yahoo Finance (yfinance). Not institutional grade.

## Hypothesis
Stocks with the highest returns over the past 12 months (excluding the most recent month) tend to outperform the following month. Buying the top decile monthly beats the Nifty on a risk-adjusted basis after costs.

## Results (2010–2025, net of 0.20% transaction costs)

| Strategy | CAGR | Sharpe | Max Drawdown | Turnover |
|---|---|---|---|---|
| Momentum long-only top decile | 31.9% | 1.42 | -22.7% | 27.2% |
| Nifty 50 benchmark | 11.0% | 0.72 | -29.3% | — |
| Long-short spread | 8.0% | 0.45 | -39.0% | 27.2% |

## Equity Curve
![Equity Curve](equity_curve.png)

## Drawdown
![Drawdown](drawdown.png)

## Rolling 12-Month Sharpe Ratio
![Rolling Sharpe](rolling_sharpe.png)

## Monthly Returns Heatmap
![Monthly Heatmap](monthly_heatmap.png)

## Out-of-Sample Validation
![OOS Validation](oos_validation.png)

## Robustness — Four Lookback Windows
![Robustness Sweep](robustness_sweep.png)

## Sector Exposure
![Sector Exposure](sector_exposure.png)

## Market Beta and Factor Analysis
![Factor Exposure](factor_exposure.png)

## Portfolio Turnover
![Turnover](turnover.png)

## Method
- Universe: 113 Nifty-listed large-cap stocks (today's list — survivorship bias present)
- Signal: 12-1 month momentum (past 12 months return, skip most recent month)
- Portfolio: Top 10% by momentum, equal weighted, monthly rebalance
- Costs: 0.20% one-way, scaled by actual turnover
- Walk-forward design — no look-ahead bias
- Data: Yahoo Finance via yfinance, 2010–2025

## Out-of-Sample Validation
- In-sample: 2010–2017
- Out-of-sample: 2018–2025
- Momentum maintains positive Sharpe and beats the Nifty in both periods

## Robustness
Tested across four lookback windows (3-1, 6-1, 9-1, 12-1). Momentum outperforms the Nifty on Sharpe across all windows, suggesting the result is not parameter-specific.

## Survivorship Bias — Quantified
Universe uses today's constituent list. Estimated inflation: 2–5% CAGR per year. Even after a 5% annual haircut, momentum still beats the Nifty benchmark.

## Honest Limitations
- **Survivorship bias:** universe uses today's list, not historical membership
- **Bull market tailwind:** 2020–2024 Indian equity rally inflates the 15-year number
- **Simplified costs:** flat 0.20% ignores market impact on less liquid names
- **No risk model:** no volatility scaling or sector neutrality
- **Data quality:** Yahoo Finance is not institutional grade (NSE Bhavcopy or CMIE Prowess would be more rigorous)

## How to Run
1. Install Python 3
2. Run: `pip install notebook yfinance pandas numpy matplotlib seaborn scipy`
3. Open: `jupyter notebook momentum_backtest_v3.ipynb`
4. Run all cells top to bottom
