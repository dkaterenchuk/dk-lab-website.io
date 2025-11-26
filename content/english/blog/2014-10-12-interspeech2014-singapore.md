---
title: "Interspeech2014 @ Singapore – Highlights"
date: 2014-10-12T19:10:27-04:00
draft: false
author: "Denys Katerenchuk"
image: "images/blog/2014/10/landscape-poster-small.jpg"
description: "Conference highlights from Interspeech2014 in Singapore, featuring cutting-edge research in NLP and speech recognition technologies."
categories:
  - "Conference"
  - "NLP"
  - "Speech Recognition"
tags: ["Conference"]
---

This year my colleagues from SpeechLab and I were invited to Interspeech2014 conference to present our work. The conference was held in Singapore, a great city with multilingual culture. The city was the perfect choice for an NLP and speech conference. I was impressed by how well everything was organized from the opening ceremony to the very end. It made the 24-hour flight from NYC to Singapore well worth it. The best part of the conference was the whole slew of interesting research papers in various areas of NLP.

## Conference Impressions

A conference, in general, is a good place to get familiar with the current state-of-the-art research. Interspeech2014 was no exception, featuring great presentations from researchers all over the world. The organization was exceptional, and the multicultural setting of Singapore provided the perfect backdrop for a conference focused on speech communication technologies.

![Conference venue and Singapore cityscape](/images/blog/2014/10/2014-09-15-09.12.36-960x480.jpg)

## Notable Research Papers

Below you can find a small list of some papers I came across and found interesting to read:

### Word-Phrase-Entity Language Models: Getting More Mileage out of N-grams
*Michael Levit, Sarangarajan Parthasarathy, Shuangyu Chang, Andreas Stolcke, Benoît Dumoulin*

This paper presents a modification of the traditional n-gram language modeling approach that departs from word-level data representation and seeks to re-express the training text in terms of tokens that could be either words, common phrases, or instances of one or several classes. Applied to the calendar scenario in the personal assistant domain, their approach reduces word error rates by more than 13% relative to word-only n-gram language models.

### Improving Spoken Document Retrieval by Unsupervised Language Model Adaptation
*Robert Herms, Marc Ritter, Thomas Wilhelm-Stein, Maximilian Eibl*

This research addresses the out-of-vocabulary problem in spoken document retrieval systems. The authors propose a two-step approach that uses web search to obtain adaptation data for block-specific adaptation of pronunciation dictionaries and language models. Their experimental results show improvements of up to 11.7% for MAP and 7.5% WER compared to baseline language models.

![Evening view of Singapore during the conference](/images/blog/2014/10/2014-09-15-19.04.22-1024x579.jpg)

### Prosody Contour Prediction with Deep Recurrent Neural Networks
*Raul Fernandez, Asaf Rendel, Bhuvana Ramabhadran, Ron Hoory*

This work explores Long Short-Term Memory, bidirectional, deep recurrent neural networks for prosody prediction. The authors demonstrate that RNNs provide improved performance over DNNs in terms of various objective metrics for prosodic streams, with about 6% relative reduction in F0 mean-square error and 14% relative increase in F0 variance.

### Word Embeddings for Speech Recognition
*Samy Bengio and Georg Heigold*

The authors present an alternative construction where words are projected into a continuous embedding space where words that sound alike are nearby in the Euclidean sense. This approach allows scoring words that were not in the training dictionary, showing improvements in word error rate through lattice rescoring and model combination.

![Conference sessions and presentations](/images/blog/2014/10/2014-09-16-11.03.36-1024x579.jpg)

## Show & Tell Session: Mobile Crowdsourcing

One particularly interesting presentation was about Crowdee, a mobile crowdsourcing platform. As a scientist, the importance of getting, annotating, and cleaning data cannot be overstated. While Amazon Turk has been the common approach, it requires people to work in front of computers. The mobile platform allows users to perform tasks on the go, making data generation more accessible for diverse languages and research scenarios.

### Crowdee: Mobile Crowdsourcing Micro-task Platform
*Babak Naderi, Tim Polzehl, André Beyer, Tibor Pilz, Sebastian Möller*

This platform operates on mobile devices and makes data generation and labeling scenarios available for many research tracks, potentially covering small and underrepresented languages. The mobility and scalability of the platform is expected to stimulate data-driven studies throughout the research community.

![Research poster presentations at Interspeech2014](/images/blog/2014/10/2014-09-17-09.42.47-1024x579.jpg)

## Conclusion

Interspeech2014 was an excellent conference that showcased the latest developments in speech and language technologies. The combination of high-quality research presentations, well-organized sessions, and the vibrant setting of Singapore made it a memorable and productive event for the speech research community.

![Conference networking and exhibition area](/images/blog/2014/10/2014-09-18-15.54.51-1024x579.jpg)

## Check Out Our Papers Here:

1. ["Was that your mother on the phone?'': classifying interpersonal relationships between dialog participants with lexical and acoustic properties."](https://www.researchgate.net/profile/Denys-Katerenchuk/publication/266079290_Was_that_your_mother_on_the_phone_Classifying_Interpersonal_Relationships_between_Dialog_Participants_with_Lexical_and_Acoustic_Properties/links/542467050cf26120b7a74821/Was-that-your-mother-on-the-phone-Classifying-Interpersonal-Relationships-between-Dialog-Participants-with-Lexical-and-Acoustic-Properties.pdf) – Denys Katerenchuk, David-Guy Brizan, Andrew Rosenberg
2. ["Improving named entity recognition with prosodic features."](https://www.researchgate.net/profile/Denys-Katerenchuk/publication/266079342_Improving_Named_Entity_Recognition_with_Prosodic_Features/links/542466c00cf26120b7a7481a/Improving-Named-Entity-Recognition-with-Prosodic-Features.pdf) – Denys Katerenchuk, Andrew Rosenberg