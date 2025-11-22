---
id: 389
title: 'RankDCG: Ranking-Ordering Evaluation Measure'
date: 2017-02-01T18:45:35-04:00
author: Denys
layout: post
guid: http://www.dk-lab.com/?p=389
permalink: /rankdcg-ordering-evaluation-measure/
categories:
  - Uncategorized
---
Advanced algorithms improve our lives in subtle, but consistent ways. Google search results seldom make us go to the second page and Netflix magically recommends an interesting movie. These are outcomes of multiple trials and errors to find the best recommendation algorithm. How do these companies determine which algorithm is the best? Evaluating different ranking algorithms is not a trivial task. This is why we developed the Rank Discounter Cumulative Gain (RankDCG) evaluation measure. This measure is designed to evaluate and compare rank-ordering algorithms. RankDCG has three fundamental properties: 

- consistent lower and upper score bounds between 0 and 1
- it works with non-normal element distributions
- it allows element transitivity inside sub-groups of the same rank. 

RankDCG works on a large variety of problems where conventional measures fail.

Problems such as search or recommendation are defined by the umbrella term information retrieval (IR). These problems deal with retrieving and ranking/ordering relative data, whether it is movies or web pages. This data often comes from a large data source. In order to know which of the items is more relevant, there exists a function, we can call it $$Relevance()$$, that returns a relevance score from 0 — not relevant, to some positive number. This function helps to convert categorical data into ordinal (quantifiable) data. For example, imagine that we want to recommend a movie according to its genre. It is impossible to say that a thriller is better than a drama because movie genres don't have a hierarchy. However, the $$Relevance()$$ function orders movie genres according to a defined rule. For visualization purposes, let's say that we have a list of genres with relevance scores: $$[A_3, T_1, D_0]$$ where A - action, T - thriller, D - drama. The subscript number defines the relevance scores for each element. Imagine that there exist two algorithms that order the movie list according to some rules. The first algorithm returns $$[D_0, T_1, A_3]$$ and the second returns $$[T_1, A_3, D_0]$$. None of them returned the perfect result. The question to consider is which algorithm returns a better result. If one of them is better, then how much better? This is when evaluation measures come into play.

Among the variety of measures, discounted cumulative gain (DCG) is the most notable. It is used during information retrieval (IR) competitions, including annual TREC competitions. DCG is defined by the following formula: 

$$ DCG = \sum_{i=1}^{n} \frac{Relevance(x_i)}{log_2(i+1)} $$ 

where n - number of elements in the list, $$Relevance()$$ function - returns relevance score for each element, and i - ith element in the list.

In other words, if DCG is applied to the first list, the result is equal to $$DCG_1 = 0/1 + 1/1.6 + 3/2 = 2.125$$ and the second is $$DCG_2 = 1/1 + 3/2 + 0/3 = 2.5$$. From the result, we can see that the second algorithm works better. Unfortunately, the score of 2.125 is hard to understand. The only way to know how well an algorithm works is by direct comparison with another algorithm or the ground truth score. This creates a problem of understanding the results. For this reason, normalized DCG (nDCG) came into existence. nDCG is defined following way:

$$ nDCG = \frac{DCG}{IDCG} $$

 where DCG - defined above and IDCG - ideal DCG score on a given list (perfect ordering).


In our case, $$IDCG = 9/1 + 1/2 + 0/3 = 9.5$$ resulting in $$nDCG_1 = 2.125/9.5 = 0.22$$ and $$nDCG_2=2.5/9.5=0.26$$. Both algorithms got quite low scores for misplacing the A - action genre with a relevance score of 3. This shows the differences between the algorithms much better. What is more important, reporting a score of 0.26 gives a much better picture to describe the performance. Unfortunately, nDCG has a few drawbacks as well. First of all, the nDCG measure is designed for IR tasks. It works better when the relevance scores are binary (0 or 1) and the algorithm needs only to retrieve relevant elements. For example, given a list $$[A_1, B_0, C_0, D_1, E_1]$$ returning $$[A_1, D_1, E_1]$$ would produce the perfect score and $$[B_0, C_0]$$ the lowest score of “0.” In our example list $$[A_3, T_1, D_0]$$, the nDCG measure never produces “0.” Thus, the lowest score is defined by the reversed list $$ [D_0, T_1, A_3] $$, which results in the nDCG score of 0.22. To a person not familiar with the problem, 0.22 might sound like a reasonable performance. This measure makes performance analysis confusing because the lowest score can be perceived as a good result.

Secondly, this measure does not work well with subgroups. Let us say that the collection contains multiple movies but only two genres: action (value of 2) and drama (value of 1). A list for new movie scores looks like this: $$[A_2, B_2, C_1, D_1, E_1]$$. Since there are only two genres, the problem can be interpreted as a binary classification. Thus $$[C_1, B_2, A_2, D_1, E_1]$$ and $$[E_1, B_2, C_1, D_1, A_2]$$ must be equal. Think of it as an example of transitivity property. In other words, permutations inside subgroups should not change the score.

Lastly, some problems might require predicting the relevance function scores and ordering the list according to this new scoring. If the estimated values are used instead of the original, this creates a bias towards assigning larger values to the elements. For instance, if an algorithm assigns $$ [A_10, T_10, D_10] $$ and evaluates using this new function than nDCG is equal to 5.232. Clearly, this is above the intended score range of 1.0. 

RankDCG was designed to address these and other problems. The main idea of this measure is to: 1) normalize the scores to be in the range from 0 to 1; 2) add transitive property to subgroups. Ex: in $$ [A_3, T_1, D_1] $$, the following permutations are equal $$ [T_1, A_3, D_1] $$ = $$ [T_1, D_1, A_3]$$; 3) abstraction from the relevance scores, ex: both $$ [A_3, T_1, D_1]$$ and $$ [A_10, T_5, D_5] $$ must receive the same RankDCG score.

Formally stated: $$ RankDCG = \sum_{i=1}^n \frac{relevance'(x_i)}{reversed_relevance(i)} $$  $$ relevance'()$$ is derived by counting the unique relevance scores (Ex: $$ [A_3, T_1, D_1] $$ => $$ [3,1] $$ => which equals to 2 and then assigning this score to the top element $$ (A_3 => A_2) $$ . The consecutive scores are reduced by one (no change is needed to $$ T_1 $$ and $$ D_1 $$).$$ reversed_relevance() $$ - the reverse of the values obtained from the $relevance$ function above with the correction to the subgroup position. If we apply this to $$ [A_3, T_1, D_1] $$, the result will be a list of discounting factors $$[1, 2, 2]$$.

    
By adding two functions to the definition, the measure addresses all the points from above in a consistent manner. By using RankDCG, researchers will be able to better understand their results and design algorithms with much higher precision. Evaluating the results of ordering is a hard task where conventional measures fail to deliver consistent results on a wide range of problems. RankDCG, on the other hand, delivers better results on wider types of problems. More details in more experimental settings can be found in this paper: [RankDCG](https://arxiv.org/pdf/1803.00719.pdf){:target="_blank"}


RankDCG python library can be downloaded from here: [RankDCG](https://github.com/dkaterenchuk/ranking_measures){:target="_blank"} python library