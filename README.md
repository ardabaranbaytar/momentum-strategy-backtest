# Momentum Strategy Backtest

This project tests a rule-based equity momentum strategy using historical U.S. stock price data.

The strategy selects stocks with the strongest recent momentum and compares the portfolio performance against SPY, which is used as the benchmark for broad U.S. equity market performance.

## Project Overview

The project includes two backtests:

1. A small large-cap stock universe test
2. An extended current S&P 500 universe test

The strategy uses 60-day momentum, monthly rebalancing, and equal-weighted portfolio construction.

## Strategy Rules

- Calculate 60-day momentum for each stock
- Rebalance monthly
- Select top momentum stocks
- Build an equal-weighted portfolio
- Compare results against SPY
- Evaluate transaction cost impact

## Small Universe Test

The first version uses a small universe of 15 large-cap U.S. stocks.

The strategy selects the top 5 stocks by 60-day momentum each month and holds them equally weighted until the next rebalance.

### Results

| Metric | Momentum Strategy | Momentum Strategy with TC | SPY Benchmark |
|---|---:|---:|---:|
| Total Return | 2237.57% | 2053.62% | 225.32% |
| Annualized Return | 38.96% | 37.78% | 13.10% |
| Annualized Volatility | 24.02% | 24.02% | 17.76% |
| Sharpe Ratio | 1.62 | 1.57 | 0.74 |
| Max Drawdown | -33.53% | -33.53% | -33.72% |
| Win Rate | 58.12% | 58.04% | 54.68% |

## Extended Current S&P 500 Universe Test

To make the test more realistic, the strategy was also tested on the current S&P 500 universe.

After filtering for sufficient historical price data, the final universe included 474 tickers from 2016-11-01 to 2024-12-30.

In this version, the strategy selects the top 20 stocks by 60-day momentum each month.

### Results

| Metric | S&P 500 Momentum Strategy | SPY Benchmark |
|---|---:|---:|
| Total Return | 418.91% | 184.37% |
| Annualized Return | 23.70% | 14.45% |
| Annualized Volatility | 24.04% | 18.53% |
| Sharpe Ratio | 0.99 | 0.78 |
| Max Drawdown | -37.83% | -33.72% |
| Win Rate | 56.84% | 55.41% |

## Interpretation

The momentum strategy outperformed SPY in both tests.

The small universe test produced very strong results, but these results should be interpreted carefully because the selected universe includes several large-cap technology stocks that performed extremely well during the backtest period.

The extended S&P 500 universe test produced less extreme but more realistic results. The strategy still outperformed SPY in total return, annualized return, Sharpe ratio, and win rate, but it also had higher volatility and a larger maximum drawdown.

## Limitations

This project has several important limitations:

- The extended test uses the current S&P 500 universe, so survivorship bias may still exist.
- The strategy does not use historical point-in-time S&P 500 membership.
- Transaction costs are simplified.
- Slippage, bid-ask spreads, taxes, and liquidity constraints are not fully modeled.
- The strategy does not include advanced risk management rules.
- Historical performance does not guarantee future results.

## Next Steps

Possible improvements include:

- Using historical S&P 500 constituents to reduce survivorship bias
- Testing different momentum windows such as 20-day, 60-day, and 120-day momentum
- Comparing top 5, top 10, and top 20 stock selection rules
- Adding volatility-adjusted position sizing
- Adding sector constraints
- Adding more realistic transaction cost and slippage assumptions
- Running out-of-sample testing

## Tools Used

- Python
- pandas
- NumPy
- matplotlib
- yfinance
- requests

## Project Files

```text
momentum-strategy-backtest/
│
├── README.md
├── momentum-strategy-backtest.ipynb
└── requirements.txt
