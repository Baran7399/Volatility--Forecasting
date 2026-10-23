# Forecasting Commodity and Crypto Volatility

Forecasting next-week volatility of gold, silver, crude oil and Bitcoin (2015–2026),
comparing classical models (HAR, ARIMA, GARCH) with machine learning models
(Random Forest, LightGBM). All models are evaluated with a walk-forward backtest:
each forecast uses only data available at the time.

## Results so far (test period 2021–2026, RMSE, lower is better)

| Asset   | Naive  | HAR    | HAR + implied vol | ARIMA  | GARCH  |
|---------|--------|--------|-------------------|--------|--------|
| Bitcoin | 0.3591 | 0.2760 | 0.2764            | 0.2749 | 0.3206 |
| Oil     | 0.1923 | 0.1634 | 0.1532            | 0.1681 | 0.1684 |
| Gold    | 0.1010 | 0.0834 | 0.0773            | 0.0878 | 0.0849 |
| Silver  | 0.2607 | 0.2023 | 0.2029            | 0.2093 | 0.2165 |

- HAR, the simplest model, beats the naive forecast by 15–23%.
- Adding option-implied volatility (OVX for oil, GVZ for gold) improves forecasts by a further 6–7%.
- Adding all 24 features to a linear model causes overfitting.

## Notebooks
1. `g-s-bc-o-data.ipynb` — data download, returns, weekly realized volatility
2. `linear models.ipynb` — naive baseline, HAR, ARIMA, GARCH
3. `features-lin.ipynb` — market and macro features, HAR with features

Work in progress: machine learning models and significance tests.
