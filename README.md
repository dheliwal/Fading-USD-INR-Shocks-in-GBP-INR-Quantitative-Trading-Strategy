# Fading USD/INR Shocks in GBP/INR: Quantitative Trading Strategy

## Overview

This project investigates whether unusually large movements in the USD/INR exchange rate are associated with short-term mean reversion in GBP/INR. Motivated by observed foreign exchange market behaviour, the study examines whether a contrarian trading strategy can exploit potential temporary deviations in the GBP/INR exchange rate.

Using historical daily exchange-rate data, the project develops an event-driven trading strategy, evaluates multiple parameter combinations, and tests performance on an out-of-sample period. Transaction costs and risk-adjusted performance are incorporated to assess whether the observed pattern translates into a potentially exploitable trading opportunity.

## Research Question

Does GBP/INR exhibit short-term mean reversion following significant USD/INR movements, and can this relationship support a profitable contrarian trading strategy after transaction costs?

## Methodology

The analysis follows these steps:

1. **Data collection:** Retrieve historical USD/INR and GBP/INR exchange-rate data using `yfinance`.
2. **Data preparation:** Sort observations chronologically, remove duplicate dates, handle missing or invalid prices, and inspect unusually large daily movements.
3. **Event detection:** Identify significant USD/INR shocks using rolling 252-day volatility, with thresholds applied to historical volatility calculated up to the previous day.
4. **Signal generation:** Identify events where GBP/INR moves in the same direction as the USD/INR shock and evaluate a contrarian position in GBP/INR.
5. **Backtesting:** Test different shock thresholds and holding periods, incorporating assumed round-trip transaction costs.
6. **Model evaluation:** Compare in-sample and out-of-sample performance using cumulative returns, Sharpe ratio, maximum drawdown, hit rate, average trade return, and transaction-cost sensitivity.

## Strategy Configuration

- **Instruments:** USD/INR and GBP/INR
- **Data frequency:** Daily
- **Volatility lookback:** 252 trading days
- **Shock thresholds:** 1.5, 2.0, 2.5, and 3.0 times rolling volatility
- **Holding periods:** 4–8 trading days
- **Parameter selection:** Training-period Sharpe ratio, subject to a minimum trade-count requirement
- **Transaction costs:** Assumed round-trip cost of 10 basis points
- **Out-of-sample testing:** Test period beginning January 2020

## Results

The selected strategy achieved a cumulative return of **35.3% in the training period**, with a Sharpe ratio of 0.457. However, its out-of-sample cumulative return was **−2.4% after assumed transaction costs**, with a Sharpe ratio of −0.029.

The results suggest that the in-sample performance did not persist out of sample. Transaction-cost sensitivity further demonstrates the importance of implementation costs when evaluating short-horizon trading strategies.

These findings do not establish a robust, consistently profitable mean-reversion effect.

## Key Learnings

- The importance of separating training and testing periods to evaluate generalisation.
- The impact of transaction costs on short-horizon trading profitability.
- The risk of overfitting when selecting parameters from multiple strategy configurations.
- The need for realistic execution assumptions and further robustness testing.

## Technology Stack

- **Python**
- **pandas** and **NumPy** for data manipulation and numerical analysis
- **yfinance** for historical exchange-rate data
- **Statistical analysis** and **quantitative backtesting**

## Limitations and Future Work

Potential extensions include introducing a one-day execution lag, incorporating bid–ask spreads and carry costs, testing alternative currency pairs, conducting walk-forward validation, and investigating whether results differ across market regimes.

## Disclaimer

This project is for academic and research purposes only. It does not constitute investment advice or a recommendation to trade foreign exchange. Historical backtest results do not guarantee future performance.
