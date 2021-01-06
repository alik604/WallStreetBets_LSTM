# Pitch Ideas
## Sentiment Analysis for Price Forecasting
Similar paper: [https://arxiv.org/abs/2002.02010](https://arxiv.org/abs/2002.02010)
- Scrape sites like r/wallstreetbets [and/or other subreddits], /biz/ [and/or other imageboards], and/or other places.
- Train a doc2vec model to turn posts into vectors
- Feed vectors to LSTM
- Train on price data from WRDS [SFU subscription]
- ???
- Profit
### Alternative: Just predict volatility, not price
- Can be volatility for an individual stock or market-wide volatility (like the VIX) [will be much easier]
- For volatility, a possibility is not web scraping and instead just using stock market data itself; similar paper: [https://arxiv.org/abs/2002.02008](https://arxiv.org/abs/2002.02008)
## Stock Picking from Board Composition and Compensation
- Get Board of Directors and/or Executives composition and compensation from WRDS
- Train a model to find out which Boards, Executives, and compensation methods lead to EPS increases
- ???
- Profit
## Security Pricing from Derivatives
- Get price data for a stock(s) and related derivatives (options, ETFs) from WRDS
- Train a LSTM to regress the price of the stock from the price of its derivatives
- ???
- Profit
## Real Estate Selection from Census Data
- Get price data from BC Assessment and census data
- Other stuff???
- Train a model to find out which factors lead to real estate price increases
- ???
- Profit

