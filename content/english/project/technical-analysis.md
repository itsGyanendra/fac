+++
bg_image = "/images/featue-bg.jpg"
category = "Summer Project 2020"
description = "To get familiarised with the concepts and applications of technical analysis (mainly related to building and testing the validity of stock indicators) using OLS Linear Regression"
image = "/images/technical.jpg"
title = "Technical Analysis of Nifty 50"
[[information]]
info = "Summer Project 2020"
label = "Project Period"
[[information]]
info = "28th June 2020"
label = "Completed on"
[[information]]
info = "Data Science , Finance"
label = "Skills"
[[information]]
info = "Jupyter Notebook"
label = "Software Used"

+++
> “You don’t make money by trading, you make it by sitting.” It takes patience to wait for the trade to develop, for the opportunity to present itself. Let the market come to you, instead of chasing the market. Chart patterns are very accurate. They have proven their accuracy and predictability time and time again, but you have to wait for them to develop.”  
>                                                                                            ― **Fred McAllen**

Title sounds tough! No, it’s not. Let’s read about this fun-filled, interesting project that our club worked on and what all it consisted of.

Let us start with what the title means.

The **NIFTY 50** is a benchmark Indian stock market index that represents the weighted average of 50 of the largest Indian companies listed on the National Stock Exchange. NIFTY 50 is ranked fourth in the world by equity trading volume, covers 14 sectors of the Indian Economy, and at any point in time, depicts the strength of Indian stock market.

What exactly do we mean by Technical Analysis of any stock?

Technical analysis is the study of chart patterns and statistical figures to understand market trends and pick stocks accordingly. Sounds complicated? Here is a simpler definition.

One day the share price is up, another day it may be down. But over time, if you look at the stock price’s movement, you may see trends and patterns emerge. The study of these chart patterns and trends in stock prices is called technical analysis of stocks.

Many other investors analyse stocks based on their fundamentals: such as their revenue, valuation or industry trends. For that we have a whole other project under us!!

Now, coming to our project!

Initial task was to get used to Python libraries like NumPy, Pandas and Matplotlib, because this is where we coded everything. Then we got to know about various sources through which we can import stock data and get daily prices of the stock that we needed analyse.

We used _read_csv()_ method and extracted the data from Yahoo Finance, dropping unnecessary columns like Open, Low, High, etc.

We also applied the fundamentals of statistics, confidence intervals, and probability distribution, used Methods like _info(), describe(), mean(),_ and _std()_ and analysed the stock data_._

Then we plotted the daily returns by transforming the Adjusted close price into percentage change (new column) using _pct_change()_ and then using Seaborn to plot the KDE distribution of the daily returns. We used _rolling()_ and _mean()_ methods to calculate the simple moving average of the last X days.

Further we plotted line graphs of SMA and Closing Price to check for the cross-overs using _plot()_ method and implemented other key features of Matplotlib.

Technical indicators are chart analysis tools that helps traders better understand and act on price movements There is a huge range of technical analysis tools available that analyse trends, provide price averages, measure volatility and more. In our project, other than Simple Moving Average (SMA) we analysed some extremely popular indicators, building them from scratch on Python for e.g. Relative Strength Indicator (RSI), Bollinger Bands, Exponential Moving Averages (EMA), Moving Average Convergence- Divergence (MACD) etc. After building those indicators, we tried finding bullish and bearish crossovers by visualising the data, plotted signal lines and prepared a trading strategy accordingly.

To test the validity and robustness of our strategy, we calculated mean absolute returns of 10 days. Then, using python library _statsmodels.formula.api, we_ developed an OLS linear regression model in Python with mean absolute return as the dependent variable and each of the three indicators as the independent variable. Separate regression equations for separate indicators.

Also, to test further we developed an OLS multiple linear regression model with absolute return as the dependent variable and all our indicators as the independent variables.

To test the significance of models and variables, we used _model.summary()_ and checked the values of P(f), R2, P(t) and found the coefficients and intercepts of our model.

I hope this summary garnered your interest in the project.

View the full documentation of our project:

> ### [Full Documentation](https://drive.google.com/file/d/1JIm7Gh5LYPQXdjg2ILZCpHahEiqlTBPy/view?usp=sharing "Official Documentation - Technical Analysis of Nifty 50")