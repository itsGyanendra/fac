+++
bg_image = "/images/featue-bg.jpg"
category = "Summer Project 2020"
description = "To learn about mean reversion as a concept and how it holds importance when one is forming a profitable trading strategy, along with other basic essentials of corporate Finance"
image = "/images/mrt-2.jpg"
title = "Mean Reversion Trading Strategy"
[[information]]
info = "Trading"
label = "Skills"
[[information]]
info = "30 June 2020"
label = "Projected completed on"
[[information]]
info = "Summer Project 2020"
label = "Project Period"

+++
Mean Reversion Trading Strategies, look like four very mathematically heavy words for a newbie to digest? I hope to make you comfortable with them by the end of this article. The students who took up this project also carried no prior knowledge of the concept but ample amounts of enthu did the trick XP. Mean Reversion is a concept that captures a very fundamental characteristic of human behaviour and the market; if the market has reached a high, it will go downhill too and if the market has taken a hit, it will surely improve soon. Long story short, there is a normal and behaviours fluctuate accordingly in order to maintain it.

Our project aimed to identify the top performing stocks at the NSE and also could predict and alert the trader on when to buy, sell or hold a stock that is mean reverting.

To begin with the project, the team took to learning some basic finance and concepts and how the market functions with its dynamic shareholders. An introduction to Python was also taken up which the team later on manipulated their time series and implemented the models on.

The first essential concept that we made use of was ‘**Stationarity**’ which is covered to length in the documentation provided below. The team was provided with data of 111 companies with a minute based time series for the year 2017 (90,000 data points) and the first step identified the stocks that mean reverted in the train model (60,000 data points). The selected stocks were further processed in varied time series (5min, 10min, hourly basis) and new data frames with their profits were reported. Now, as our project aimed to identify the top 25 performing stocks over that year; so we sorted the data frames on the basis of a number of variables in their respective time intervals and then merged them to identify the 25 best stocks from the list.

First aim fulfilled, now the prediction model was to be prepared. For this, the team made use of the ‘**ARIMA** **Machine Learning Model**’. ARIMA stands for ‘Autoregressive integrated moving average’ and the mathematics behind it is discussed extensively in the documentation. On making use of the past data that we fed to the model through the train set, we first identified the model that fit best and there was no scope of an overfit model. On identifying the right model, the code further produced the predictions which informed the programmer when to buy, sell or hold the specific stock, fulfilling the final aim of the project.

The concept of Mean Reversion finds itself in the essential toolkit for anyone who wants to make a career in finance or trading and the concept has been the foundation of many trading models that earn firms millions on the market. This project, though very primary in its approach, acted as our beginning in the world of finance.

To know about the project implementation in detail, do have a look at the documentation provided below. Cheers!

> ### [Official Documentation](https://drive.google.com/file/d/10P2l95SU6oZYPfjnV05WCPAAAOipSF6U/view?usp=sharing "MRTS - Official Documentation")