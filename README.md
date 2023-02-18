# Project: Momentum-Trading-Strategy
> Inspired by Momentum Trading Strategy Course on Qunatra; Improved the strategy by myself

## Data
  - S&P 500 component stocks
  - Time period for portfolio construction:
  - Time period for back-testing:  
## Portfolio Selection: Volatility Decile Portfolio Strategy
- **What is it?**
  - When you divide the dataset into 10 equal parts, then each part is called as decile. 
  - When the dataset is ordered by volatility and then split into 10 equal parts, they are called volatility decile.
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
>   $$ TBV = \sum_{i = 1}^n BV_i $$
>
>   $$ \bar{R} = \sum_{j=1}^n \frac{BV_j}{TBV} R_j $$
>  
> Where BV denotes the beginning market value of security 
## Trading Signal: Moving Average + Breakout + Bollinger Band
- In Quantra course, the strategy involves moving averge and breakout. However, based on my previous trading experience, Bollinger Band could provide a good sense of price movement. Thus, I incorporate it into indicator pool.
- **Moving Average**
  - **How to use it?**
    - If the price crosses beyond moving average, it is likely price goes further upward.
    - If the price crosses below moving average, it is likely price goes further downward.
  - **Limitation**
    - Moving averages work in a trending market. However, if the asset prices keep following a cyclic pattern without any trend, the moving average won't generate any signals.
    - Moving average of different time span could provide conflicting signals. 
- **Breakout Strategy**
  - **How to use it?**
    - If the price goes over the maximum value of a past period, it is likely price goes further upward.
  - **Why**
    - This jump is usually the result of an accumulation phase. When the price is moving sideways, it tends to accumulate a lot of positions. Once there are enough positions on one side (buying or selling), the pressure builds up. And it suddenly bursts, resulting in a jump in the price. You can say that the price breakout is due to a build-up of momentum.
    - Similarly, when the price is moving in the same direction for a given period, it tends to lose momentum after a while. There is an accumulation of positions on the other side, leading to a reversal and a breakout.
- **Bollinger Band**
  - **What is it?**
    - Bollinger band is consisted of three lines: Moving avaerge + 2 STD(upper bound), Moving average, Moving avaerge - 2 STD(lower bound)   
  - **How to use it**
    - When the price is between the range of upper bound and moving average, it is likely to be an upward trend.
    - When the price is between the range of moving average and lower bound, it is likely to be an downward trend.
- **Implementation**
    - Quantra
      - If (price is above moving average) *AND* (price is greater than past period), then long the portfolio.
      - Otherwise, leave the market. 
    - My Improvement
      - If ((price is above moving average) *AND* (price is greater than past period) *OR* (price is between the range of upper BB band), then long the portfolio.
      - Otherwise, leave the market.
## Strategy Performance Metrics
