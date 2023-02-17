# Project: Momentum-Trading-Strategy
> Inspired by Momentum Trading Strategy Course on Qunatra; Improved the strategy by myself

## Data
  - S&P 500 component stocks
  - Time period:  
## Portfolio Selection: Volatility Decile Portfolio Strategy
- **What is it?**
  - When you divide the dataset into 10 equal parts, then each part is called as deciles. 
  - When the dataset is ordered by volatility and then split into 10 equal parts, it is called volatility decile.
  - We pick up stocks of first (or first several) decile to form our portfolio.
- **Why this method?**
  - Gains received through technical indicator strategies are an increasing function of stocks’ volatility.
- **Implementation**
  - Step 1: Calculate STD for daily returns
  - Step 2: Annualize STD
  - Step 3: Sort the stocks by volatility
  - Step 4: Select top 10% stocks with highest volatility
## Portfolio Weights: Equal-weighted Method
  - **What is it?**
    - For equal-weighted average return calculations, the market value is ignored since all securities in the  portfolio are assumed to have the same weight. In this project, we rebalance the portfolio every day.
  - **How to calculate average return?**

$$ \bar{R} = \sum_{k=1}^n \frac{R_k}{n} $$

  - **Implementation**
    - Step 1: Get the daily price for each stock
    - Step 2: Calculate average of daily returns of stocks
    - Step 3: Compute cumulative returns of portfolio
> **NOTE:** for asset-weighted portfolio, the average return should be 
>
>   $$ TBV = \sum_{j = 1}^n BV_j $$
>
>   $$ \bar{R} = \sum_{i=1}^n \frac{BV_i}{TBV} R_i $$
>  
> Where BV denotes the beginning market value of security 
## Trading Signal: Moving Average + Breakout + Bollinger Band
- In Quantra course, the strategy involves moving averge and breakout. However, based on my trading experience, Bollinger Band could provide a good sense of price movement. Thus, I incorporate it into indicator pool.
- **Moving Average**
  - **How to use it?**
    - If the price crosses beyond moving average, it is likely price goes further upward.
    - If the price crosses below moving average, it is likely price goes further downward.
    - Limitation
      - Moving averages work in a trending market. However, if the asset prices keep following a cyclic pattern without any trend, the moving average won't generate any signals.
      - Moving average of different time span could provide conflicting signals. 

## 
