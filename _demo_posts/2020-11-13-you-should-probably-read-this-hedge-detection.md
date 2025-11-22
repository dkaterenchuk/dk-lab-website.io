---
layout: post
title:  "'You Should Probably Read This': Uncertain Statement Detection."
date:   2020-11-13 00:00:08
author: Denys
categories: 
    - NLP
    - ML
    - Research
comments: false
permalink: /you-should-probably-read-this-dedge-detection/
---

Humans express ideas, beliefs, and statements through language. The manner of expression can carry information indicating the author’s degree of confidence in their statement. Understanding the certainty level of a claim is crucial in areas such as medicine, finance, engineering, and many others where errors can lead to disastrous results. In this work, we apply a joint model that leverages words and part-of-speech tags to improve hedge detection in text. This approach achieves a new top F1 score on the CoNLL-2010 Wikipedia corpus.

Imagine a situation where a doctor says to a patient “I think you need surgery immediately!” Many will take this statement seriously without any additional considerations. However, the phrase “I think” signals uncertainty in the diagnosis. Identifying these signs of uncertain claims, known as hedges, can prevent cases of malpractice and save lives. For this reason, uncertainty detection is an important problem in medicine, finance, engineering, and other high-risk fields.

 The degree of certainty in language was first introduced by G. Lakoff [1]. His work introduces the concept of hedges, which are linguistic devices that are used in conversations to indicate the degree of belief or to mitigate orders. The hedge phrases that signal uncertainty can be expressed through linguistic devices such as modal verbs (“could”, “might”, etc.), peacock expressions (“very likely”, “everyone”, “I think”, etc.), and weasel words (“some believe”, “clearly”, etc.). These expressions are context-dependent and the presence of these in a sentence doesn’t indicate uncertainty. Hence, advanced methods are required to identify uncertain claims.


![](/Users/den/Web/dk-lab/images/2020/11/hedge_related_work.png)


References:

[1] George Lakoff, “Lexicography and generative grammar i: Hedges and meaning criteria,” Annals of the New York Academy of Sciences, vol. 211, no. 1, pp. 144–153, 1973.