---
title: "Predicting Stock Prices: What Does Twitter Know About the Market?"
date: 2015-05-29T00:00:00-04:00
draft: false
author: "Denys Katerenchuk"
image: "images/blog/2016/01/nyse_nyc.jpg"
description: "Exploring the relationship between Twitter sentiment and stock market movements using machine learning and social media analytics to achieve over 80% prediction accuracy."
categories:
  - "Data Science"
  - "Finance"
  - "NLP"
  - "Machine Learning"
tags: ["Stock Market Prediction", "Twitter Analysis", "Sentiment Analysis", "Machine Learning", "Finance", "Social Media Analytics"]
---

## Introduction

Can public opinion predict stock market movements? With recent advancements in natural language processing (NLP), this question has gained significant attention in both academic and financial circles. As an NLP scientist, I decided to investigate this relationship and satisfy my own curiosity about the intersection of social media sentiment and financial markets.

The opportunity arose when The Graduate Center offered "Machine Learning in Quantitative Finance," providing the perfect chance to explore this domain. I was fortunate to collaborate with three talented fellow Ph.D. students: Mingbo Ma, Eric Dagobert, and Konstantinos Vamvourellis. Each brought expertise from different computer science domains, enabling us to approach the problem from multiple perspectives and ultimately achieve prediction accuracies exceeding 80%.

## Research Objectives

Our primary research questions were:
- Can Twitter sentiment serve as a reliable predictor of stock price movements?
- How does social media sentiment correlate with traditional financial indicators?
- What machine learning approaches best capture the relationship between public opinion and market behavior?

## Data Collection and Preprocessing

### Stock Market Data
Given the exploratory nature of this project and time constraints, we focused on two major technology companies: Apple (AAPL) and Microsoft (MSFT). These companies were selected for their high social media presence and trading volume. Historical stock prices were obtained from Yahoo Finance, with analysis limited to daily closing prices to maintain consistency.

### Social Media Data
For text data, we leveraged Twitter's real-time stream of public opinions. Due to API licensing restrictions, we established our own data collection infrastructure to stream relevant tweets. Our initial dataset comprised three months of Twitter data, which after preprocessing (removing weekends, holidays, and noise) yielded 56 trading days of analysis.

**Data Preprocessing Steps:**
1. Tweet filtering based on company-specific keywords and hashtags
2. Removal of spam, bot accounts, and duplicate content
3. Text normalization and cleaning
4. Temporal alignment with trading hours and market calendar

This unbiased dataset was particularly valuable as we had no control over market events during the collection period, ensuring our analysis reflected genuine market conditions.

## Methodology

### Experimental Design
Our interdisciplinary team approach proved beneficial, as members from different backgrounds brought diverse perspectives on potential solutions. We implemented parallel development streams to derive predictive features from both Twitter sentiment and historical stock price patterns.

### Baseline Models
We established baseline performance using traditional approaches:
- **Simple Linear Regression**: Basic relationship modeling between features and price movements
- **ARIMA Models**: Time series analysis incorporating autoregressive and moving average components
- **Technical Indicators**: Traditional financial metrics (moving averages, RSI, MACD)

### Social Media Feature Engineering
The core innovation focused on extracting meaningful signals from Twitter data:

**Sentiment Analysis Pipeline:**
1. Tweet preprocessing and tokenization
2. Sentiment classification using lexicon-based and machine learning approaches
3. Aggregation of sentiment scores by trading day
4. Normalization and smoothing of sentiment time series

**Volume and Engagement Metrics:**
- Tweet volume per trading day
- Retweet and mention frequencies
- User influence weighting based on follower counts
- Temporal patterns in social media activity

### Key Discovery: Sentiment-Price Correlation
Our most significant finding was the strong correlation between Twitter sentiment and daily stock price movements, as illustrated in the embedded visualizations below:

<iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/546.embed"></iframe>
*Figure 1: Apple Stock Price vs. Twitter Sentiment Correlation*

<iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/533.embed"></iframe>
*Figure 2: Microsoft Stock Price vs. Twitter Sentiment Correlation*

## Results and Analysis

### Experimental Framework
We conducted four distinct experiments to evaluate different modeling approaches:

1. **Baseline Linear Regression**: Traditional price prediction using historical data
2. **Sentiment-Enhanced Model**: Incorporating Twitter sentiment as primary feature
3. **Multi-Feature Ensemble**: Combining sentiment, volume, and technical indicators
4. **Advanced ML Pipeline**: Implementing sophisticated algorithms with feature selection

### Performance Metrics
Surprisingly, despite the high correlation between sentiment and stock movements, sentiment alone did not yield optimal prediction accuracy. This led us to explore more sophisticated feature engineering and ensemble methods.

**Final Results:**
<table width="100%">
  <tr>
    <td>
    <iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/619.embed"></iframe>
    <em>Apple Prediction Results</em>
    </td>
    <td>
    <iframe width="100%" height="300" frameborder="0" scrolling="no" src="//plotly.com/~dk-lab/621.embed"></iframe>
    <em>Microsoft Prediction Results</em>
    </td>
  </tr>
</table>

Our final ensemble models achieved prediction accuracies exceeding 80% for both companies, demonstrating the viability of combining traditional financial indicators with social media analytics.

## Key Insights and Implications

### Technical Findings
1. **Sentiment Correlation**: Strong positive correlation between Twitter sentiment and same-day stock performance
2. **Feature Complementarity**: Social media metrics complement rather than replace traditional financial indicators
3. **Temporal Dynamics**: Real-time sentiment provides early signals of market sentiment shifts
4. **Company Specificity**: Different companies exhibit varying degrees of social media influence sensitivity

### Methodological Contributions
- Demonstrated feasibility of real-time social media integration in financial modeling
- Established preprocessing pipeline for noisy social media data in financial contexts
- Validated ensemble approaches combining heterogeneous data sources

## Limitations and Future Work

### Current Limitations
- Limited dataset size (56 trading days) affects model generalizability
- Focus on only two companies restricts broader market applicability
- Simplified sentiment analysis may miss nuanced opinion dynamics
- Lack of consideration for market manipulation and coordinated social media campaigns

### Future Research Directions
- Expand analysis to broader market indices and sectors
- Investigate longer-term prediction horizons beyond daily movements
- Integrate additional social media platforms (Reddit, LinkedIn, news outlets)
- Develop real-time trading strategy implementation and backtesting
- Address ethical considerations around market manipulation detection

## Conclusion

This research demonstrates that social media sentiment, particularly from Twitter, can serve as a valuable component in stock market prediction models. While sentiment alone is insufficient for accurate predictions, its integration with traditional financial indicators through advanced machine learning techniques significantly improves forecasting performance.

The work opens promising avenues for incorporating real-time public opinion into financial modeling and automated trading strategies. As social media continues to influence market psychology, understanding and quantifying these relationships becomes increasingly critical for both academic research and practical financial applications.

## Acknowledgments

Special thanks to my collaborators Mingbo Ma, Eric Dagobert, and Konstantinos Vamvourellis for their invaluable contributions to this research. Their diverse expertise in machine learning, financial modeling, and data engineering made this interdisciplinary project possible.

## References and Further Reading

*Note: Detailed algorithm descriptions and comprehensive experimental results will be available in our forthcoming publication.*

---

*This research was conducted as part of the "Machine Learning in Quantitative Finance" course at The Graduate Center. The findings represent exploratory research and should not be construed as financial advice.*