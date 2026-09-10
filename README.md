# Q-Scanner: Multi-Factor Quantitative Trading Signal Research

Q-Scanner is an ongoing quantitative research project focused on developing, testing, and evaluating multi-factor trading signals across financial markets.

The project combines market-data acquisition, technical feature engineering, rule-based signal generation, historical backtesting, and performance analysis.

## Research Objective

The primary objective is to investigate whether combining multiple technical factors into a systematic scoring framework can produce useful trading signals and improve decision-making relative to a simple buy-and-hold benchmark.

## Current Framework

Q-Scanner currently incorporates:

- Moving-average trend analysis using SMA20, SMA50, and SMA200
- Relative Strength Index (RSI)
- Bollinger Bands
- Average Directional Index (ADX) for trend strength
- Average True Range (ATR) for volatility classification
- Price momentum (10-day and 60-day)
- Multi-factor scoring
- Signal classification
- Multi-asset scanning
- Historical backtesting
- Transaction-cost modelling
- Benchmark comparison
- Maximum drawdown analysis
- Win-rate and profit-factor analysis
- Walk-forward evaluation (train / validation / locked out-of-sample)
- Regime-aware position sizing

## Assets

The current research framework has been tested across major US equities including:

- Apple (AAPL)
- Microsoft (MSFT)
- NVIDIA (NVDA)
- Amazon (AMZN)
- Meta Platforms (META)
- Alphabet (GOOGL)
- Tesla (TSLA)

## Research Development

The signal framework has been developed iteratively through multiple versions.

### V1 — Initial Multi-Factor Backtest

The first backtesting framework combines trend, RSI, momentum, and Bollinger Bands, evaluated against a buy-and-hold benchmark while accounting for transaction costs.

### V2 — Enhanced Scoring Framework

V2 introduces positive and negative factor contributions and a wider signal classification, with a confidence measure derived from the magnitude of the composite score.

### V3 — Refined Signal Engine

V3 introduces more granular scoring, including differentiated RSI regimes and categorical momentum and Bollinger Band interpretations.

### V4 — Enhanced Signal Engine

V4 extends the framework with configurable risk-management parameters (stop-loss, take-profit) and a revised signal-generation process. At this stage those parameters were defined but not yet enforced in the backtest simulation.

### V5 — Robust Performance Diagnostics

V5 keeps the V4 trading rules unchanged and focuses on measuring the strategy properly: CAGR, annualised volatility, Sharpe and Sortino ratios, Calmar ratio, win rate, profit factor, expectancy, exposure, and year-by-year performance versus benchmark.

### V6 — Long-Term Regime Scoring

V6 adds SMA200-based long-term regime classification and ADX-based trend-strength filtering to the core score, and introduces a proper walk-forward split (TRAIN 2021-01-01 to 2024-01-01, VALIDATION 2024-01-01 to 2025-01-01, OUT_OF_SAMPLE 2025-01-01 to 2026-08-31).

### V7 — Regime-Aware Strategy

V7 preserves the V6 core score unchanged and adds:

- Trend-regime confirmation using SMA50 slope
- Longer-horizon (60-day) momentum confirmation
- Volatility-aware position sizing using rolling ATR%
- Entry/hold hysteresis to reduce unnecessary exits

The V6 out-of-sample window (2025-01-01 to 2026-08-31) is treated as locked: V7 is not tuned against it, and results are only inspected after the fact.

## Backtesting Results

The initial V1 historical backtest did not outperform a buy-and-hold strategy across the tested assets. This result is intentionally retained as part of the research process rather than presenting the strategy as a profitable trading system.

The V7 locked out-of-sample evaluation shows a mean Sharpe ratio of approximately 0.25 (median 0.41) and a mean profit factor of approximately 1.10 across the tested universe, with 5 of 7 tickers producing a positive Sharpe. This indicates a weak but non-random edge under the current rule set — not yet a result that would justify live capital.

## Methodology

The research workflow is:

1. Retrieve historical market data
2. Clean and prepare the data
3. Construct technical features
4. Generate factor-level signals
5. Combine factors into a composite score
6. Convert scores into trading signals
7. Simulate historical strategy returns
8. Account for transaction costs
9. Compare against buy-and-hold
10. Evaluate drawdown, win rate, and risk-adjusted performance
11. Run walk-forward validation with a locked final out-of-sample window
12. Test parameter stability around the chosen thresholds
13. Iterate on the strategy

## Technology Stack

- Python
- NumPy
- Pandas
- yfinance
- TA
- VectorBT
- Jupyter Notebook

## Project Status

**Status: Active development**

Q-Scanner is an ongoing research project. The current implementation (V7) is regime-aware but remains backtest-only: there is no live data feed, order execution, or broker/MT5 integration yet, and the out-of-sample edge is not yet strong enough to justify live deployment.

## Future Development

Planned improvements include:

- Reconstructing a true portfolio-level equity curve from the locked OOS results (rather than per-ticker averages)
- Implementing stop-loss and take-profit logic directly within the backtesting engine
- Widening the asset universe beyond correlated mega-cap tech names
- Improving portfolio-level risk management and position sizing
- More rigorous transaction-cost and slippage modelling
- MT5 integration for eventual automated execution, once the edge and risk framework justify it

## Disclaimer

This repository is a quantitative research project and is not financial advice. Historical backtest results do not guarantee future performance.
