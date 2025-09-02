# Momentum Trading Strategy

This repository contains a Jupyter notebook analyzing a volatility decile portfolio strategy for S&P 500 component stocks between 2010-01-01 and 2022-12-31. The strategy combines moving average, Bollinger Bands, and breakout signals to evaluate momentum-based trading ideas.

## Strategy Performance

| Strategy                               | Sharpe Ratio | Cumulative Return | Max Drawdown |
|----------------------------------------|-------------:|------------------:|-------------:|
| MA_signal & BO_signal (Quantra)        | 0.15         | 1.09              | -21.84%      |
| BB_signal                              | 0.96         | 2.90              | -22.69%      |
| MA_signal + BB_signal + BO_signal      | 0.98         | 3.59              | -24.87%      |

> Inspired by the Momentum Trading Strategy course on Quantra and expanded with additional indicators.

## Repository Structure

- `Volatility Decile Portfolio Strategy & Technical Indicators.ipynb` — main notebook implementing the strategy.
- `.ipynb_checkpoints/` — notebook checkpoints.

## Getting Started

1. Clone the repository.
2. Install the required packages (pandas, numpy, etc.).
3. Launch Jupyter Lab or Notebook and open the notebook:
   ```bash
   jupyter lab
   ```
4. Execute the notebook to reproduce the results.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
