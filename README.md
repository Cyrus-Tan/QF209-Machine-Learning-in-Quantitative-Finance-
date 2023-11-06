# Machine Learning in Quantitative Finance: Incorporating Sentiment Analysis

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Data](#data)
- [Features](#features)
- [Models_and_APIs_used](#models_and_APIs_used)
- [Results](#results)
- [Conclusion](#conclusion)
- [Contributing](#contributing)
- [License](#license)

### Overview
A traditional 60-40 portfolio, comprising 60% stocks and 40% bonds, has been favored by institutional investors due to its historical resilience during demand shocks. Stocks are riskier assets, but bonds tend to rise when interest rates fall, which occurs during economic downturns. Earnings call transcripts, unlike daily news, hold latent information, providing insights that might not be immediately factored into market prices. Leveraging Natural Language Processing (NLP), we aim to analyze sentiments in these transcripts to navigate market volatility and optimize asset allocation. We will pass in the sentiment score of each individual earnings call transcript (extracted with NLP FinBert), together with the predicted Adj. Close price as inputs into the Black-Litterman Model. This model is unique in the world of portfolio optimization due to its ability to incorporate subjective views of investors or analysts about expected returns. Prior to the implementation of the Black-Litterman model, we will implement a simple Markowitz model as a baseline for comparative analysis, to compare and contrast the resulting portfolio allocation with the Black-Litterman Model's output. This comparison helps assess how the incorporation of subjective market views alters the portfolio allocation strategy. 

## Usage
1) sentimentAnalysis.ipynb
   Overview: conducts sentiment analysis on each earnings call and accords a numerical score in range(0,1)
   Duration: 70 mins (computationally heavy due to FinBERT and the analysis of 275 .docx files)
   Output: sentiment_score.xlsx (sentiment score of each earnings call, indexed by file name)
2) MLQF_stock_prices.ipynb
   Overview: Markowitz-Model for comparison, 
             Incorporates financial indicators and sentiment score
             Data cleaning, EDA, Feature Engineering
             Feature Selection using XGBoost
   Duration: < 1 min
   Output: merged.xlsx (includes both financial and non-financial indicators)
3) LSTMPreprocess.ipynb
   Overview: Trains preliminary LSTM model based on 4 features from XGBoost
   Duration: < 1 min
   Output: loss graph of each stock
4) LSTMModel.ipynb
   Overview: Conducts hyperparameter tuning of LSTM model using GridSearchCV
   Duration: 30 mins (GridSearchCV is a greedy algorithm that searches through grid sequentially)
   Output: predictions.xlsx (predicted Adj Close, indexed by date)
5) BlackLitterman.ipynb
   Overview: Obtains prior using financial indicators,
             Updates prior using confidence level to derive posterior,
             Uses posterior to calculate portfolio weights and sharpe ratio

## Dependencies
Python 3.11:
   - sentimentAnalysis.ipynb
   - MLQF_stock_prices.ipynb
   - LSTMPreprocess.ipynb
   - BlackLitterman.ipynb
Python 3.9: 
   - BlackLitterman.ipynb
     Uses PyPortfolioOpt
     - dependencies: cvxpy and qdldl, both are only compatible with Python 3.9 and below
   - workarounds: create separate Python 3.9 environment using:
      1) MacOS: brew install python@3.9 (creates Python 3.9 Brew environment, separate from pip3)
      2) Win (Anaconda): conda create --name myenv

## Data
1) Earnings call transcripts Data retrieved from Refinitiv Eikon. Timeline of transcripts used are from 1 Jan 2010 - 1 October 2023.
   
   - Consists of 5 Companies
      - Apple Inc (NASDAQ:AAPL): 55 Transcripts
      - Boeing Co (NYSE: BA): 55 Transcripts
      - Lockheed Martin Corp (NYSE: LMT): 54 Transcripts (Jan 2015 Transcripts not available for retrieval)
      - Marriott International Inc (NASDAQ: MAR): 55 Transcripts
      - NVIDIA Corp (NASDAQ: NVDA): 55 Transcripts
   
3) Stock Price Data retrieved from Yahoo Finance. Timeline of data used are from 1 Jan 2010 - 1 Oct 2023.

   -  Consists of the same 5 companies as stated above

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

Dataframes of Sentiment score, Stock price data and Technical indicators are merged to a single dataframe on date. We used backfill interpolation to fill up the NaN values of all columns, since this interpolation method is useful for consecutive NaN values.

## Models_and_APIs_used
1) **Financial & Mathematical Models:**
   - Markowitz Model: Mean-Variance Portfolio Optimization
   - Black-Litterman Model: Incorporates investor views into portfolio optimization process
2) **Machine Learning Models:**
   - NLP FinBert: Financial text analysis
   - Extreme Gradient Boosting (XGBoost): Feature importance
   - Long Short-Term Memory (LSTM): Time-series forecasting
        - GridSearchCV is used for hyperparameter tuning in LSTM model
3) **APIs**
   - yiyanghkust/finbert-tone
   - tensorflow/keras
   - scikeras: KerasRegressor
   - PyPortfolioOpt
4) **Libraries & Packages**
   - numpy
   - pandas
   - yfinance
   - matplotlib.pyplot
   - seaborn
   - scipy
   - plotly.express
   - xgboost
   - sklearn
   - nltk

## Results

## Conclusion

## Contributing

## License

