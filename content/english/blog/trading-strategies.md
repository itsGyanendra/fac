+++
author = "Kritarth Lohomi"
bg_image = "/images/featue-bg.jpg"
categories = ["Trading"]
date = 2020-08-29T18:56:00Z
description = ""
image = "/images/blog2.png"
tags = ["Stocks", "Trading", "Finance"]
title = "Trading Strategies "
type = "post"

+++
> Note : All the finance related words are described just after they are used, so there’s no need to panic!

### **1. Value Investing:**

Value investing is an investment strategy in which the trader buys stocks that are trading at a lower price than its book value and sell the stocks that are trading at a higher price than their book value.

It is believed that market overreacts to good or bad news resulting this fluctuation of the stock price which is different from the fundamental analysis of the company ,this presents the trader with a good trading opportunity as these effects are temporary and the stocks will eventually close in to their book prices!

**•This brings us to the question that “How is a stock valued by investors?”**

So ,what we are doing is calculating the expected market price of a stock using the financial statements of the company and then comparing the price to the current market price to make a call on whether to buy or sell the stock.

A stock is valued using its expected return, a stocks return is mainly of 2 types:

**Capital Appreciation:** Rise in an investments market price, calculated as the difference between the purchase price and the current market price.

**Dividends**: A dividend is a distribution of profits by a corporation to a class of its shareholders. When a profit is earned by a company it can either reinvest it or can distribute dividends.

Dividends can be summed up as the reward for holding onto the stock, it can be paid out in cash or even through additional stocks.

A commonly used method to calculate the present value of the company is:

1. **Dividend discount model (DDM**): The DDM is a way of applying net present value analysis to predict the future dividends a stock will pay, these dividends are then discounted back to their present value to give the present value of the stock.

Essentially, the DDM is built on taking the sum of all future dividends expected to be paid by the company and calculating its present value using a net interest rate factor (also called discount rate).The estimated price per share is calculated as:

#### **Price per share = D / (r - g)**

D = estimated value of next year’s dividend

r = companies cost of capital or discount rate (rate of growth of the company)

g = constant growth rate of dividend

Discount rate refers to the interest rate used in discounted cash flow (DCF) analysis to determine the present value of future cash flows.

**Book Value:** Theoretically, book value represents the total amount a company is worth if all its assets are sold and all the liabilities are paid back. This is the amount that the company’s creditors and investors can expect to receive if the company is liquidated.

1. **Financial Ratios:** Investing has a set of four basic elements that investors use to break down a stock’s value.

**P/B Ratio**: Price to Book ratio represents the value of the company if it is sold today. Useful for valuing matured company that do not have much margin to grow and the market have realised it (decreased stock price).

\**Strategy-**Low P/B is considered a good indication for matured companies, as they own assets (high book value) that are worth a lot.

**E/P Ratio:** The ratio of earning to price, usually used to value growing companies like recent startups, depicts the current market position considering the growth potential of the company.

**Strategy**-Investors should go long on high E/P (bullish market).

**PEG Ratio:** Instead of merely looking at the price and earnings, the PEG ratio incorporates the historical growth rate of the company's earnings. The PEG ratio is calculated by taking the P/E ratio of a company and dividing it by the year-over-year growth rate of its earnings. The lower the value of your PEG ratio, the better the deal you are getting for the stock's future estimated earnings.

**Strategy** - Low PEG as it means what we are paying for expected growth by 1.

**Dividend Yield**- It is the value for your money, like interest on a loan with an advantage of capital appreciation of the stock price.

### **2. Pairs Trading:**

It is a trading strategy that involves matching a long position with a short position in two

stocks with high correlation, usually a pair of stocks are traded in a market-neutral strategy, i.e. it does not matter whether the market is trending upwards or downwards, the two open positions for each stock hedge against each other (as we go long on one and short on other which have high correlation) .

* A hedge is an investment position intended to offset potential losses or gains that may be incurred by a companion investment.
* Hedging is used a lot to decrease the risk associated with a trade, but it has the same effect on profits too.

**Correlation**:

A statistical measure between -1 and +1; +1 represents perfect positive correlation while -1 represents perfect negative correlation 0 means no correlation.

A perfect positive correlation is when one variable moves in either up or down direction, the other variable also moves in the same direction with the same magnitude while a perfect negative correlation is when one variable moves in the upward direction, the other variable moves in the downward (i.e. opposite) direction with the same magnitude. The relative direction is decided by the sign and the mag determines the amount of correlation.

**Now comes the question “What are the possible outcomes?”**

From the pair selected we generally go short on the stock with higher market price and long on the other one.

1. If the difference between the prices decrease, then we make money.
2. If the difference in the prices increase and our assumption was wrong, then we lose money.
3. In all other cases we will not make any money.

As we can see that we might lose money, we need to define an entry and exit position for the trade.

**But first let us see how to select better pairs for pairs trading!**

1. The chosen pairs must be from same sector and of about the same size, if either of these is not followed then there might be correlation mathematically, but still there remains a chance that they are not related at all.
2. **Cointegration** -It is a technique to test for a relationship between 2 non-stationary time series. It is a better way to look for more accurate correlations between stocks.

Cointegration tests identify scenarios where two or more non-stationary time series are integrated together in a way that they cannot deviate from **equilibrium** in the **long term**. Integration of two non-stationary time series refer to their linear combination.

If we define spread = log(a)-nlog(b), as the correlation for the selected pairs should be high thus the spread would be close to 0 as we need to sell n stocks of B and buy 1 stock of A (every time) to keep the integration in equilibrium and thus minimize loses.

We calculate n using regression so that the spread is as close to 0 as possible, here we can say with some confidence that the two time series are mean reverting ( as we were able to find a stationary linear combination).

* **Mean reverting**- States that the prices will tend to move toward the mean and not go with the momentum. A simplistic example of a **mean reversion strategy** is to buy a stock after it has had an unusually large fall in price.

Having already established that the equation above is mean reverting, we now need to identify the extreme points or threshold levels which when crossed by this signal, we trigger trading orders for pairs trading.

#### **Z Score: z =** (x – mean) / standard deviation, where x is a raw data point and z is the z-score.

* Simply put, given a normal distribution of raw data points z-score is calculated so that the new distribution is a normal distribution with mean 0 and standard deviation of 1. Having such a distribution is very useful for creating threshold levels. For example, in pairs trading, we have a distribution of spread between the prices of stocks A and B. We can convert these raw scores of spread into z-scores as explained below. This new distribution will have mean 0 and standard deviation of 1. It is easy to create threshold levels for this distribution such as 1.5 sigma, 2 sigma so on.

**Trading signals**

Enter when the difference between the observed stocks grow above 1.5 - 2 sigma and exit when the difference between the observed stocks come close to 0 - 0.5 sigma.

These sigma values / Z values come from our normal distribution curve where 2 sigma is identified as 95% confidence of divergence which is calculated using Z-table.

Once we see the desired uptrend of sigma we should invest up (in intervals) and when the sigma value tends to come close to 0, we start trimming down.

**Following this strategy, the probability of loses reduces significantly (hedging plays a huge role!)**

### **3. Momentum Strategies:**

These strategies work with volatility by finding buying opportunities in **short-term** uptrends and then sell when the securities start to lose momentum.

**Momentum**- The current trend (believed) of the market (Bullish or Bearish). This trend can be predicted to some extent using Technical and Fundamental analysis.

We can find the strength of our trend using Quantitative methods which involve fitting a good regression plot in the time series data of the stock, we look for slope and goodness of the plot to determine the strength of the trend.

**• Slope -** represents the direction and strength of a trend. Higher the better in upwards trends and lower (with sign) the better in downward trend.

**• Goodness of fit (Reliability/R2)** - Standard deviation of the original curve with respect to our regression line. Lower the better. Std dev measures how much the plot is spread and thus it needs to be smaller for a better fit.

Now that we know what is a good fit to determine the strength, we need **to get the time series data**, as we know that larger data is always better, still its seen that 30 is the optimal number and the model doesn’t change much upon adding more data, to be on the safer side we take the **time series data of 52 weeks** which accounts to an year of trading data. We also take buy and hold period of 6 months and **we don’t interfere** with our portfolio in this period.

As we trade on momentum, we have a chance to make handsome profit, but on the downside the loses are huge too, we adapt the following strategy to reduce the risk involved:

1. Entering the market at perfect time and leaving when we see a trend reversal (for uptrend) and vice versa.
2. **Diversification:** Reduces the risk involved by trading multiple, unrelated markets/stocks, so that their trade don’t affect each other.
3. **Market Neutrality**: We short and long equal amount of money in **different sector**. If the market drops by 10% we earn 10% in shorted stocks and lose 10% in longed stocks neutralizing each other and thus diminishing the risk.
4. **Sector Neutrality:** We short and long equal amount of money in **same sector**. If the sector drops by 10% we earn 10% in shorted stocks and lose 10% in longed stocks neutralizing each other and thus diminishing the risk.

Sector neutrality is considered first for reducing the risk involved with a portfolio, both use hedging one stock against other.

**Now that we have reduced the risk involved and have a regression plot fitted in the data, we now move on to the trading perspective of the momentum strategy.**

In large portfolios capital distribution can be very hectic, we can do this on the basis on reliability. We take higher position with highly reliable stocks and vice versa (only after selecting the slopes in which we want to invest).

In the real market we have hundreds of stocks and it's hard to see each one of them and

individually decide a price to trade upon. In this scenario we group them and buy equal positions of the security that fell into each group. This is called **Basket Trading**.

**“How do we evaluate if the trade was good?”**

* **Sharp Ratio:** Help investors understand return on an investment compared to the risk involved. The ratio is the average return earned in excess of the risk-free rate per unit of volatility or total risk.
* 

Basically, depicts what is the excess profit upon taking risk. So, we take risks on high sharp ratio stocks in order to profit from the market volatility using the momentum strategy!

**BOTTOM LINE**

**Steps to be followed while using Momentum Strategies**

1\. Select the sectors where you want to apply the strategy.

2\. Create a linear regression model for every stock in your portfolio, you want the slope and R2 values (reliability) for every stock.

3\. Group the stocks based on slope and reliability, thus creating different baskets which different characteristics.

4\. A general ideology should be to buy positions in high positive slope and high reliable baskets and sell positions in high negative slope and high reliable baskets.

5\. Neutrality, both market and sector should be kept in mind, this will decrease your risk and increase your Sharpe Ratio and MRAP.

6\. Keep the above portfolio stacked and **untouched for at least 6 months** without bothering about the daily/weekly returns.

### **4.Accruals Trading Strategies:**

**Accruals:**

Accruals are any revenue earned or expense incurred, for which cash has not yet been exchanged. These are the postponed components of a Balance Sheet of a company. These can be both positive and negative. Generally, any unrealized earning have a risk associated that people will not pay the owed money. Therefore, the earning is relatively poor.

A company with low level of accruals in their earning has high level of real cash flow and therefore more certain earning, and vice versa. As a result**, stocks with low accruals should earn higher market returns than high accruals stocks**.

As we know that the accruals are both positive and negative, we need to define some ratio to classify companies. That ratio came out to be **Accruals to Total Assets.** It provides accounting measure, indication of size meet monotonic function guidelines (denominator should be positive always).

**Strategy:** As we know that as accruals accumulate the quality of earnings degrade, we tend to hold long position for stocks with low accruals to assets ratio and a short position for stocks with high accruals to assets ratio.

Most investors do not pay attention to the accruals of the company; thus this strategy can prove to be quite valuable!