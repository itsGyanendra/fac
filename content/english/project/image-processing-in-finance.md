+++
bg_image = "/images/featue-bg.jpg"
category = "Summer Project 2020"
description = "2-D Deep Convolutional Neural Network model is used with financial stock market data and technical analysis indicators for developing an algorithmic trading system."
image = "/images/imageprocessing-2.jpg"
title = "Image Processing in Finance"
projectname = "image-processing-in-finance"
[[information]]
info = "Summer Project 2020"
label = "Project Period"
[[information]]
info = "17th July 2020"
label = "Completed on"
[[information]]
info = "Jupyter Notebook"
label = "Software used"
[[information]]
info = "Data Science , Finance"
label = "Skills"

+++
## Image Processing in Finance

> _”Finance is not merely about making money. It’s about achieving our deep goals and protecting the fruits of our labor. It’s about stewardship and, therefore, about achieving a good society. ”_

Image Processing in Finance, Sounds Interesting right ! You might be thinking what is there in this project, so let me make you aware about the beauty of deep neural network and how we applied this in the field of finance, you might have noticed application of deep neural network in various fields like AI, object detection , image recognition ,voice search and tons of other things, but here we have done something out of the box. Have Patience and let's begin this journey.

You might have heard about financial time series data , here we have proposed a novel approach to convert 1-D financial time series into a 2-D image-like data representation, yeah you heard it right! How? In our study the daily stock prices of various firms or companies are obtained from finance.yahoo.com for training, validation and testing purposes. Here, we considered data of daily stock prices in a specific interval of period . Once the data is successfully extracted we move on to the labelling part where we apply Buy,Sell and Hold labels for each day in the dataset . Now we are ready for the image creation phase but before that we have to use some technical indicators to grab some additional information (how the daily stock price fluctuates) needed for image creation, so we use 12 different technical indicators for the same. Now the data part is ready after all extraction and normalization and now it's time for python to do its magic ,thereby successfully creating 12 x 15 image using the processed data.

Now after the preprocessing part, comes the part where we train our model using Convolutional Neural Network (CNN) not with some standard image but with the images we generated earlier. Passing these images into a multilayer Deep ConvolutionNetwork we predict the result and try to maximise our testing and validation accuracy using different machine learning techniques.In our model each stock is bought, sold or held according to the predicted label. We then analyse the results predicted by the Convolutional Neural Network (CNN) model and compare it with the results predicted by using financial evaluation, that’s amazing our model is predicting quite awesomely in the real world financial scenario.

From a general perspective, more applications might start adapting 2-D CNN for non-image data in the future. There are already some indications for this trend for time series forecasting, gait recognition through radar signals and malware classification. Following these recent developments, in the near future, we might expect similar implementations in other fields to start utilizing image based CNN.

If this finds you interesting, this is the research paper that we have followed and documentation of our project :

> #### [_Research Paper_](https://drive.google.com/file/d/1cLtXabM0X7A5loXE2C6LWMtH6_5-Yivd/view "Research Paper")
>
> #### [_Our Full Documentation_](https://drive.google.com/file/d/1Uk4O_rEsXSTGH2Foeuc0R5QYzcdVu6Xz/view?usp=sharing "Documentation")
