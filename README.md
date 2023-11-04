# Machine Learning in Quantitative Finance: Incorporating Sentiment Analysis

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Data](#data)
- [Features](#features)
- [Models & APIs used](#models & APIs used)
- [Results](#results)
- [Conclusion](#conclusion)
- [Contributing](#contributing)
- [License](#license)

### Overview
A traditional 60-40 portfolio, comprising 60% stocks and 40% bonds, has been favored by institutional investors due to its historical resilience during demand shocks. Stocks are riskier assets, but bonds tend to rise when interest rates fall, which occurs during economic downturns. Earnings call transcripts, unlike daily news, hold latent information, providing insights that might not be immediately factored into market prices. Leveraging Natural Language Processing (NLP), we aim to analyze sentiments in these transcripts to navigate market volatility and optimize asset allocation. We will pass in the sentiment score of each individual earnings call transcript (extracted with NLP FinBert), together with the predicted Adj. Close price as inputs into the Black-Litterman Model. This model is unique in the world of portfolio optimization due to its ability to incorporate subjective views of investors or analysts about expected returns. Prior to the implementation of the Black-Litterman model, we will implement a simple Markowitz model as a baseline for comparative analysis, to compare and contrast the resulting portfolio allocation with the Black-Litterman Model's output. This comparison helps assess how the incorporation of subjective market views alters the portfolio allocation strategy. 

## Installation

## Usage

## Data
1) Earnings call transcripts Data retrieved from Refinitiv Eikon. Timeline of transcripts used are from 1 Jan 2010 - 1 October 2023.
-> Consists of 5 Companies
   Apple Inc (NASDAQ:AAPL): 55 Transcripts
   Boeing Co (NYSE: BA): 55 Transcripts
   Lockheed Martin Corp (NYSE: LMT): 54 Transcripts (Jan 2015 Transcripts not available for retrieval)
   Marriott International Inc (NASDAQ: MAR): 55 Transcripts
   NVIDIA Corp (NASDAQ: NVDA): 55 Transcripts

2) Stock Price Data retrieved from Yahoo Finance. Timeline of data used are from 1 Jan 2010 - 1 October 2023.
-> Consists of the same 5 companies as stated above

## Features 
Each of the 5 stocks, as stated above, will have the following features. We will then use XGBoost to determine feature importance and aid us in feature selection.
- Daily_Return
- Adj Close
- Volume
- High
- Low
- Open
- Close
- RSI
- Sentiment_score
- Volatility
- MACD
- SMA
- Upper_Bollinger
- Lower_Bollinger

## Models & APIs used
1) **Financial & Mathematical Models:**
   - Markowitz Model: Risk-return Portfolio Optimization
   - Black-Litterman Model: Incorporates investor views into portfolio optimization process
2) **Machine Learning Models:**
   - NLP FinBert: Financial text analysis
   - Extreme Gradient Boosting (XGBoost): Feature importance
   - Long Short-Term Memory (LSTM): Time-series forecasting
3) **APIs**
   - yiyanghkust/finbert-tone
   - tensorflow/keras
   - scikeras: KerasRegressor
   - PyPortfolioOpt

## Results

## Conclusion

## Contributing

## License

