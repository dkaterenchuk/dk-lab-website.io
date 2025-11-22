---
id: 147
title: Sentiment Analysis of Manhattan Using Instagram
date: 2014-12-28T22:12:42-04:00
author: Den
layout: post
guid: http://www.dk-lab.com/?p=147
permalink: /sentiment-analysis-of-manhattan-using-instagram/
categories:
  - Data Science
  - Data Visualization
  - Fun Science
  - NLP
  - Text Processing
---
New York City is one of the most famous places on earth. Movies, songs, and stories prize the city and its culture. People from around the world bring their habits and cultures, which create eclectic and diverse neighborhoods just feet apart. All this lures people to visit or maybe even move to NYC. On the other hand, it&#8217;s a common belief that New Yorkers are rude and it&#8217;s a tough city to live. Being a Ph.D. student, I take all these stories with a grain of salt. I decided to see what people of New York feel through a day by analyzing Instagram captions. In addition, we will compare the neighborhoods of Manhattan and nearby boroughs to find out which are the most positive and negative.

Data:  
Instagram is a popular service to share photos and videos. However, it is also a great source for text analysis. Users often share their feeling through Instagram captions and because its indirect nature of comments, the words might carry different kinds of information than, let&#8217;s say, text or twitter messages. In total, we have 3.04 million Instagram from almost 400k users. Since the number of Instagram is so large, I will use a random sample. This is a common approach while dealing with large datasets to improve performance while preserving high precision.

Text Sentiment Analysis:  
Sentiment analysis of text is a well-known technique in Natural Language Processing. The idea is that some words hold positive or negative meanings. For example the word &#8220;good&#8221; might have a positive score &#8220;+3&#8221; and the word &#8220;terrible&#8221; &#8211; negative &#8211; &#8220;-5&#8221;. In this project I use <a title="AFINN" href="http://neuro.imm.dtu.dk/wiki/AFINN" target="_blank"><span style="text-decoration: underline;">AFFIN word list</span></a>. Each word in an Instagram caption, added by its owner, is converted into a corresponding score, and all we have to do is to sum them up to get the overall mood.

<!-- Data: Users: 391925 NewYorkers: 137646 29% neg/pos - 190616 - 23% / 656176 - 846792 26% - neutral  posts - 3043295 / 2221289 73% //-->

First, we are looking at the general picture. This is a random sample of 10k Instagrams. The bigger red circles represent a degree of &#8220;positiveness&#8221;. From the map, we can see that positive comments are posted all over New York with a concentration in the Midtown area and around Time Square.

<table width="100% frameborder=">
  <tr>
    <td>
      [1]
    </td>
  </tr>
</table>

Another interesting fact is people&#8217;s behavior change through a day. For this experiment, I take the same data, but order by the hour. As a result, we can have a continuous view of posts for each hour. On the map below, the timer starts at midnight and runs for a 24 hour period. At first the result may seem chaotic. If we take a closer look, we can see a pattern. From the very start, Manhattan bursts with fireworks of positive posts. Controversially, from frame 20 to frame 32, everything slows down for a short period, and then start to burst again. (Note: the numbers represent frames rather than hours. There are 24 hours, but 64 frames)

<table width="100% frameborder=">
  <tr>
    <td>
      [2]
    </td>
  </tr>
</table>

If you paid attention, you must have noticed that the most lively areas are around Time Square, a famous attraction for tourists. Of course tourists are happy, they are in New York! What about the people who actually live in NYC? Hence, the next step is to look only at posts by New Yorkers. In order to do it, I filter out tourists from the data. My hypothesis is based on the idea that most tourists stay in New York for no longer than two weeks. For the rest of the experiments, I am using data from users that have at least two posts that are more than two weeks apart. By doing so, we lost 71% of users (from 400k to 135k), but only 27% of Instagram posts (from 3m to 2.2m).

Below you can see positive [3] and negative [4] post map visualizations. In their essence, they resemble table [1] data. The most noticeable feature is that the positive map has a higher frequency.

<table width="100% frameborder=">
  <tr>
    <td>
      [3]
    </td>
    
    <td>
      [4]
    </td>
  </tr>
</table>

In fact, only 23% of the posts produce negative sentiment. In the graph [5] you can see the correlation of negative to positive posts. Note: neutral posts were omitted because 27% of them are neutral or without text at all.

<table width="100% frameborder=">
  <tr>
    <td>
      [5]
    </td>
  </tr>
</table>

Interestingly, if we compare all 10k posts (negative and positive) by the hour, we can see that positive posts, indeed, overtake negative by a big margin. However, from 7 am till 10 am post sentiment scores are getting really close. My guess is that this is the time before an average New Yorker has his first cup of coffee.

<table width="100% frameborder=">
  <tr>
    <td>
      [6]
    </td>
  </tr>
</table>

Furthermore, if we look at 10k positive and 10k negative posts and compare them by the hour, we can see that our observation is true. With an equal number of negative and positive posts, the trend is that people are the most positive from 10 am to 2 pm and between 10 pm and Midnight. However, from 5 am till 10 am people in New York can be quite cranky.

<table width="100% frameborder=">
  <tr>
    <td>
      [7]
    </td>
  </tr>
</table>

Now we know how New Yorkers&#8217; mood changes throughout a day. We should go ahead and find which neighborhoods are the most and the least happy. For this experiment I took a random sample of 100k instagrams. For each instagram, I mapped it&#8217;s upload location to a zip-code. We already know that data centered around prime areas (i.e. Time Square) would lead to uneven results. In order to eliminate this, I normalize the data for each zip-code by taking the average score. The zip-code locations were taken from the U.S. Census Bureau. The data, unfortunately, contains abbreviations for some zip-codes in form &#8220;10HXX&#8221;, which led to misidentification of two NYC neighborhoods. After all the data is collected, it is clustered into 5 &#8220;buckets&#8221; that are close in score and correspond to the same color.

After plotting the data onto a map [8], we can see that all neighborhoods of Manhattan have a positive score ranging from &#8220;0&#8221; and upward. In Manhattan, the most positive areas are around 42st, Midtown East, Upper West Side and West Harlem. The least positive instagrams came from Financial District, with a score only of &#8220;0.08&#8221;. Not surprisingly, New York boroughs also have to offer great (happy) areas including Brooklyn&#8217;s Flatbush ave, The Bronx&#8217;s Parkchester and Riverdale. The only area with negative sentiment is the La Guardia airport area which score is &#8220;-0.56&#8221;.

<table width="100% frameborder=">
  <tr>
    <td>
      [8]
    </td>
  </tr>
</table>

To sum up, New York City in general is quite positive. From this project we can see that New Yorkers are cheerful people who like to share their positive mood with the rest through Instagram. If you intend to travel to NYC, here are a couple tips you should keep in mind:

1. Tourists in New York are extremely happy.  
2. New Yorkers are happy for 75% of the day.  
3. Try to avoid any interactions with New Yorkers between the hours of 5am and 10am. This is the time when a chance of getting a rude remark increases.  
4. The best time to socialize or meet new people is around 2pm, 10pm or Midnight.  
5. If you consider moving to NYC, keep in mind that the happiest residential parts of Manhattan are Midtown East, Upper West Side and West Harlem.

Acknowledge:  
I would like to say thank you to CUNY Professor Lev Manovich and his team for collecting and sharing Instagram data.