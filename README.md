# Volatility Forecasting Dashboard

Five-day realized volatility forecasting for SPY, benchmarking a GRU+attention
network against GARCH(1,1) and naive persistence — deployed as a live dashboard
that scores all three models daily.

## Headline finding

**GARCH(1,1) outperforms both alternatives** on out-of-sample test data
(2022–2024):

| Model | MSE | QLIKE |
|---|---|---|
| Naive persistence | 0.003576 | 0.099484 |
| GARCH(1,1) | 0.003308 | 0.054930 |
| GRU + Attention | 0.004914 | 0.109734 |

This is consistent with the volatility forecasting literature — see Hansen &
Lunde (2005), *"A Forecast Comparison of Volatility Models: Does Anything Beat
a GARCH(1,1)?"* Diagnostic analysis attributes the neural model's
underperformance primarily to regime mismatch: GARCH refits on trailing data
every 21 trading days, while the GRU's weights remain frozen at the training
cutoff.

## Stack

FastAPI · PyTorch · React (Vite) · Recharts · Postgres · Docker · GCP Cloud Run

## Status

Under construction. See Issues for the build plan.

## Disclaimer

Educational project. Forecasts volatility (magnitude of price movement), not
direction or returns. Not investment advice.
