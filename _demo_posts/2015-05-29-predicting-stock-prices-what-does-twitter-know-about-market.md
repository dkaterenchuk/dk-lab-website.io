---
id: 336
title: 'Predicting Stock Prices: What Does Twitter Know About the Market?'
date: 2015-05-29T00:54:58-04:00
author: Den
layout: post
guid: http://www.dk-lab.com/?p=336
permalink: /predicting-stock-prices-what-does-twitter-know-about-market/
categories:
  - Data Science
  - Finance
  - Fun Science
  - NLP
  - Stock Market Prediction
  - Text Processing
---
Is it possible to use a public opinion to predict stock market movements? In recent years with advancements in natural language processing (NLP) this questions is being asked more and more frequently. Being an NLP scientist I decided to give it a try, find the answers and satisfy my own curiosity. To be honest, this question has been in my mind for a while. When The Graduate Center offered a class &#8220;Machine Learning in Quantitative Finance&#8221; I knew this was my chance to get familiar with finance and build a project to predict stock quotes. It was serendipitous to meet three like-minded students, Mingbo Ma, Eric Dagobert, and Konstantinos Vamvourellis. Each of us is a computer science Ph.D. student working in different areas. This fact enabled us to bring knowledge from different domains to the project and achieve a performance of over 80% prediction rate. 

Data  
Since this is an exploratory project with time constraints, we decide to scale down and concentrate on two company stocks. The first two companies that came to our mind are Apple and Microsoft. The companies are chosen arbitrarily, without any incentives. The stock prices we get from Yahoo Finance. We agree to use only closing daily quotes.

For the text data, we turn our attention to Twitter. Due to license restrictions, we had to set up our own server to stream tweets. At the time of first experiments, tweet collection consisted of only three months of data. After cleaning and excluding weekends and holidays, this comes down to 56 days of trading. With time, we will collect more data, but for now this is sufficient for an exploratory project. In addition, this data unbiased because we have no control over the events during this period, nor we chose a time period to match some expectations.

Experiments  
In order to predict stock prices, we look at different approaches. Partially this is because the team members come from different backgrounds and the view of what will and will not work is different as well. This, in fact, turned out to benefit the project. We work in parallel to derive useful features from Twitter as well as historical stock prices. 

The most trivial prediction model is a simple linear regression. This is what used as our baseline. In addition, we explore well-known statistical models that are used in finances such as ARIMA and others. But the main focus is to derive prediction features from tweets. The most interesting discovery is a high correlation of tweet sentiment and daily stock prices. Below you can see two plots for Apple and Microsoft stock quotes and sentiment with a polynomial fit function to highlight the similarities. 

<iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/546.embed"></iframe>
<iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/533.embed"></iframe>

Results  
In total, we construct four experiments. The first one being a baseline &#8211; linear regression and the rest are our experiments. To my surprise, despite a high correlation between sentiment and stock price movements, it did not produce height accuracy. Instead, we moved toward more advanced techniques. I do not provide our algorithm descriptions here because it would require quite extend and thorough story. Instead, an interested reader can find more details in a paper we are going publish soon. It will contain all algorithm descriptions in addition to more experiments. For now I provide the result graphs below.

<table width="100%">
  <tr>
    <td>
    <iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/619.embed"></iframe>
    </td>
    <td>
    <iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/621.embed"></iframe>
    </td>
  </tr>
</table>