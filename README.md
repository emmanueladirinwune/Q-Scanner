# Q-Scanner: Multi-Factor Quantitative Trading Signal Research

Q-Scanner is an ongoing quantitative research project focused on developing, testing, and evaluating multi-factor trading signals across financial markets.

The project combines market-data acquisition, technical feature engineering, rule-based signal generation, historical backtesting, and performance analysis.

## Research Objective

The primary objective is to investigate whether combining multiple technical factors into a systematic scoring framework can produce useful trading signals and improve decision-making relative to a simple buy-and-hold benchmark.

## Current Framework

Q-Scanner currently incorporates:

- Moving-average trend analysis using SMA20 and SMA50
- Relative Strength Index (RSI)
- Bollinger Bands
- Price momentum
- Multi-factor scoring
- Signal classification
- Signal confidence estimation
- Multi-asset scanning
- Historical backtesting
- Transaction-cost modelling
- Benchmark comparison
- Maximum drawdown analysis
- Win-rate analysis

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

The first backtesting framework combines:

- Trend
- RSI
- Momentum
- Bollinger Bands

The strategy is evaluated against a buy-and-hold benchmark while accounting for transaction costs.

### V2 — Enhanced Scoring Framework

V2 introduces positive and negative factor contributions and a wider signal classification:

- Strong Buy
- Buy
- Neutral
- Sell
- Strong Sell

A confidence measure is also derived from the magnitude of the composite score.

### V3 — Refined Signal Engine

V3 introduces more granular scoring, including differentiated RSI regimes and categorical momentum and Bollinger Band interpretations.

### V4 — Enhanced Signal Engine

V4 extends the framework with configurable risk-management parameters and a revised signal-generation process.

The stop-loss and take-profit parameters are currently part of ongoing development and have not yet been incorporated into the historical trade simulation.

## Backtesting Results

The initial historical backtest did not outperform a buy-and-hold strategy across the tested assets.

This result is intentionally retained as part of the research process rather than presenting the strategy as a profitable trading system.

The backtest provides a basis for identifying weaknesses in the current signal design and for testing future improvements.

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
10. Evaluate drawdown and win rate
11. Iterate on the strategy

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

Q-Scanner is an ongoing research project. The current implementation is being progressively extended to improve signal robustness, risk management, backtesting methodology, and quantitative evaluation.

## Future Development

Planned improvements include:

- Implementing stop-loss and take-profit logic directly within the backtesting engine
- Improving portfolio-level risk management
- Testing additional factor combinations
- Parameter sensitivity analysis
- Walk-forward testing
- Out-of-sample evaluation
- More rigorous transaction-cost and slippage modelling
- Risk-adjusted performance metrics
- Portfolio construction and position sizing
- Comparison against additional benchmarks

## Disclaimer

This repository is a quantitative research project and is not financial advice. Historical backtest results do not guarantee future performance.
