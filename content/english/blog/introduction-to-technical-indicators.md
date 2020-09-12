+++
author = "Abhishek Verma"
bg_image = "/images/featue-bg.jpg"
categories = ["Technical Indicators"]
date = 2020-08-27T21:30:00Z
description = ""
image = "/images/ta-2.png"
tags = ["Finance", "Algorithmic Trading"]
title = "Introduction to Technical Indicators [ Part 1 ]"
type = "post"

+++
## **What is Algorithm Trading?**

Algorithmic trading simply means that process which helps execute trade orders in an automated manner. It is more beneficial than manual trading since it provides for much more trading profits.

In simple words, Algorithmic Trading is a process of converting a trading strategy into computer code which buys and sells (place the trade) the shares in an automated, fast and accurate way. Since the automated way of trading is faster and more accurate, it is preferred nowadays and is increasing its reach in emerging markets rapidly.

So as the name sounds interesting this field is very vast and promising. But for now I wants to share one of the most important part of Algo-trading i.e. **Technical Indicators**.

## **Five Indicators To Build A Trend Following Strategy**

Trend following strategies are strategies where you simply ride the trend, i.e. buy when the price is going up and sell when the price starts going down. In this strategy, one does not aim to forecast or predict, but simply keep an eye on the market for any emerging trends.

We cover the following trend indicators in this article:

### **1.  MACD (Moving Average Convergence Divergence):**

Moving Averages indicator is a widely used technical indicator that is used to arrive at a decision that is not based on one or two episodes of price fluctuations. A set of historical data can be employed to observe the price fluctuations of the stock for a predetermined period of time. The same assists in depicting the general direction of the trend flow. This technique is used for generating support and building resilience for future outcomes.

It is a trend following momentum indicator which is calculated by taking the difference of 2 exponential moving averages of an asset price (typically 26 period EMA and 12 period EMA). A signal line is also calculated which is the moving average of the MACD line(typically 9 period) calculated in the above step.

More info at - [Click Here](https://www.investopedia.com/terms/m/macd.asp "MACD - Investopedia")

    def MACD(DF,a,b,c):
        df = DF.copy()
        df["MA_Fast"]=df["Adj Close"].ewm(span=a,min_periods=a).mean() # ewm is Exponential Moving Average 
        df["MA_Slow"]=df["Adj Close"].ewm(span=b,min_periods=b).mean()
        df["MACD"]=df["MA_Fast"]-df["MA_Slow"]
        df["Signal"]=df["MACD"].ewm(span=c,min_periods=c).mean()
        df.dropna(inplace=True)
        return df

### **2.  RSI (Relative Strength Index) :**

The Relative Strength Index (RSI) indicator, as the name suggests, tells us the relative strength of the asset. In other words, the RSI tells us how well the stock is performing (or not) with respect to itself. RSI is counted as a robust technical indicator which can be used to analyse the market and is an important part of the trader’s arsenal as it helps them to make better decisions in timing the market.

It is a momentum oscillator which measures the speed and change of price movements. RSI values oscillates between 0 to 100 with values above 70 indicating that the asset has now reached overbought territory. Values below 30 signify oversold territory. Assets can remain in oversold and overbought territory for a long period of time.

The relative strength index ie RSI Indicator is calculated using the following formula:

**RSI = 100 – 100 / (1 + RS)**

where RS = Average gain of up periods during the specified time frame / Average loss of down periods during the specified timeframe.

More info at: [Click Here](https://www.investopedia.com/terms/r/rsi.asp "RSI - Investopedia")

    def RSI(DF,n):
        df = DF.copy()
        df['delta']=df['Adj Close'] - df['Adj Close'].shift(1)
        df['gain']=np.where(df['delta']>=0,df['delta'],0) # np.where is the if else staement for numpy, also check documentaion page
        df['loss']=np.where(df['delta']<0,abs(df['delta']),0) # note we are taking absolute value of loss
        avg_gain = []
        avg_loss = []
        gain = df['gain'].tolist()
        loss = df['loss'].tolist()
        for i in range(len(df)):
            if i < n:
                avg_gain.append(np.NaN)
                avg_loss.append(np.NaN)
            elif i == n:
                avg_gain.append(df['gain'].rolling(n).mean().tolist()[n])
                avg_loss.append(df['loss'].rolling(n).mean().tolist()[n])
            elif i > n:
                avg_gain.append(((n-1)*avg_gain[i-1] + gain[i])/n)
                avg_loss.append(((n-1)*avg_loss[i-1] + loss[i])/n)
        df['avg_gain']=np.array(avg_gain)
        df['avg_loss']=np.array(avg_loss)
        df['RS'] = df['avg_gain']/df['avg_loss']
        df['RSI'] = 100 - (100/(1+df['RS']))
        return df

### **3. OBV (On Balance Volume)**

OBV Indicator is a momentum based indicator which measures volume flow to gauge the direction of the trend. Volume and price rise are directly proportional. A rising price is depicted by a rising OBV and a falling OBV stands for a falling price. If OBV depicts a rise in the same pattern as the prices this is a positive indicator. While a contrast with the pattern depicts a negative indicator.

OBV is used as a confirmation tool with regards to price trends. If the OBV increases with respect to the increasing price trend, it can be inferred that the price trend is sustainable. If, however, the OBV shows a decline with respect to the increasing price trend, then it could signal a price trend reversal.

A rising OBV reflects positive volume pressure that can lead to higher prices and falling OBV predicts decline in prices. Leading market indicator but prone to making false signals. Typically, used in conjunction with lagging indicators such as MACD.

More info at: [Click Here](https://www.investopedia.com/terms/o/onbalancevolume.asp "OBV -Investopedia")

    def OBV(DF):
        df = DF.copy()
        df['daily_ret'] = df['Adj Close'].pct_change() # Percentage change between the current and a prior element
        df['direction'] = np.where(df['daily_ret']>=0,1,-1)
        df['direction'][0] = 0
        df['vol_adj'] = df['Volume'] * df['direction']
        df['obv'] = df['vol_adj'].cumsum()
        return df

### **4. ADX (Average Directional Index)**

You can use the Average Directional Index (ADX) indicator if you want to determine the intensity or strength of a trend. But why would you want to find the intensity of a trend? If you trade in a weaker trend then there is a high probability of reversal compared to a stronger trend. So combining your directional trades with a stronger trend will help you achieve higher hit ratio and higher average profitability per trade.

Here is an interesting fact, while the name is the Average Directional Index (ADX), it does not tell us the direction of the trend. While it may sound alarming, the reason for this is quite simple, The ADX indicator is always used in conjunction with the Positive directional indicator and the Negative directional indicator, which indicate the up and downtrend respectively.

ADX is non directional meaning it makes no inference about the direction of the trend but only about the strength of the trend. The calculation involves finding both positive and negative directional movement (by comparing successive highs and lows) and then calculating the smoothed average of the difference of these.

More info at: [Click Here ](https://www.investopedia.com/articles/trading/07/adx-trend-indicator.asp "ADX - Investopedia")

    def ADX(DF,n):
        df2 = DF.copy()
        df2['TR'] = ATR(df2,n)['TR'] #the period parameter of ATR function does not matter because period does not influence TR calculation
        df2['DMplus']=np.where((df2['High']-df2['High'].shift(1))>(df2['Low'].shift(1)-df2['Low']),df2['High']-df2['High'].shift(1),0)
        df2['DMplus']=np.where(df2['DMplus']<0,0,df2['DMplus']) # Directional Movement Up
        df2['DMminus']=np.where((df2['Low'].shift(1)-df2['Low'])>(df2['High']-df2['High'].shift(1)),df2['Low'].shift(1)-df2['Low'],0)
        df2['DMminus']=np.where(df2['DMminus']<0,0,df2['DMminus']) # Directional Movement Down
        TRn = []                 # To smooth the True Range
        DMplusN = []             # To smooth upward Directional Movement
        DMminusN = []            # To smooth downward Directional Movement
        TR = df2['TR'].tolist()
        DMplus = df2['DMplus'].tolist()
        DMminus = df2['DMminus'].tolist()
        for i in range(len(df2)):
            if i < n:
                TRn.append(np.NaN)
                DMplusN.append(np.NaN)
                DMminusN.append(np.NaN)
            elif i == n:
                TRn.append(df2['TR'].rolling(n).sum().tolist()[n])
                DMplusN.append(df2['DMplus'].rolling(n).sum().tolist()[n])
                DMminusN.append(df2['DMminus'].rolling(n).sum().tolist()[n])
            elif i > n:
                TRn.append(TRn[i-1] - (TRn[i-1]/n) + TR[i])
                DMplusN.append(DMplusN[i-1] - (DMplusN[i-1]/n) + DMplus[i])
                DMminusN.append(DMminusN[i-1] - (DMminusN[i-1]/n) + DMminus[i])
        df2['TRn'] = np.array(TRn)
        df2['DMplusN'] = np.array(DMplusN)
        df2['DMminusN'] = np.array(DMminusN)
        df2['DIplusN']=100*(df2['DMplusN']/df2['TRn'])
        df2['DIminusN']=100*(df2['DMminusN']/df2['TRn'])
        df2['DIdiff']=abs(df2['DIplusN']-df2['DIminusN'])
        df2['DIsum']=df2['DIplusN']+df2['DIminusN']
        df2['DX']=100*(df2['DIdiff']/df2['DIsum'])
        ADX = []
        DX = df2['DX'].tolist()
        for j in range(len(df2)):
            if j < 2*n-1:
                ADX.append(np.NaN)
            elif j == 2*n-1:
                ADX.append(df2['DX'][j-n+1:j+1].mean())
            elif j > 2*n-1:
                ADX.append(((n-1)*ADX[j-1] + DX[j])/n)
        df2['ADX']=np.array(ADX)
        return df2

### **5. Bollinger Bands**

Bollinger band is a volatility based indicator. Bollinger band indicators are signals plotted on a singular line which represent the price fluctuations for a particular stock. They consist of three lines, Upper Bollinger band, Middle band, Lower Bollinger band. The upper and lower Bollinger bands are plotted two standard deviations away from the mean average. The two signals or the bands are plotted to measure the volatility of the price fluctuations.When markets become more volatile, the distance between the signals increases or in short the bandwidth widens and the reverse for low volatility. Higher the volatility, higher the cue for quitting the trade. The reason the Bollinger bands are plotted two standard deviations away from the mean average is to make sure that the distance between the two bands comprises more than 80% of the price action, thus making any price above or below the bands highly significant.

##### More info at:  [Click Here ]()

    def BollBnd(DF,n):
        df = DF.copy()
        df["MA"] = df['Adj Close'].rolling(n).mean()
        df["BB_up"] = df["MA"] + 2*df['Adj Close'].rolling(n).std(ddof=0) #ddof=0 is required since we want to take the standard deviation of the population and not sample
        df["BB_dn"] = df["MA"] - 2*df['Adj Close'].rolling(n).std(ddof=0) #ddof=0 is required since we want to take the standard deviation of the population and not sample
        df["BB_width"] = df["BB_up"] - df["BB_dn"]
        df.dropna(inplace=True)
        return df