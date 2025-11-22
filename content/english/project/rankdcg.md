---
title: "RankDCG: Rank-Ordering Evaluation Measure"
description: "A novel evaluation measure for ranking systems that addresses limitations in existing metrics"
draft: false
image : "images/projects/rankdcg.jpg"
bg_image: "images/projects/rankdcg.jpg"
category: ["Machine Learning", "Research"]
weight: 1
information:
  - label : "Project Type"
    info : "Research & Open Source"
  - label : "Domain"
    info : "Information Retrieval"
  - label : "Technologies"
    info : "Python, Ranking Algorithms"
  - label : "Publication"
    info : "arXiv 1803.00719"
  - label : "GitHub"
    info : "https://github.com/dkaterenchuk/ranking_measures"
  - label : "Paper"
    info : "https://arxiv.org/pdf/1803.00719"
  - label : "Stars"
    info : "38"
---

## RankDCG: Rank-Ordering Evaluation Measure

Ranking is used for a wide array of problems, most notably information retrieval (search). There are a number of popular approaches to the evaluation of ranking such as Kendall's tau, Average Precision, and nDCG.

### The Problem

When dealing with problems such as user ranking or recommendation systems, traditional evaluation measures suffer from various limitations:

- **Inability to deal with ties** - Many real-world ranking scenarios include tied rankings
- **Inconsistent lower bound scores** - Existing measures lack clear and meaningful baseline scores
- **Ambiguous scoring** - Difficulty interpreting what scores actually represent
- **Inappropriate cost functions** - Cost functions that don't align with practical ranking needs

### The Solution

We propose **rankDCG**, a new evaluation measure that addresses these fundamental problems. RankDCG provides:

- Proper handling of tied rankings
- Consistent and interpretable lower bound scores
- Clear, unambiguous evaluation metrics
- Cost functions appropriate for real-world ranking applications

### Key Features

The package provides implementations of:

- **Rank Discounted Cumulative Gain (RankDCG)** - the primary novel contribution
- Normalized Discounted Cumulative Gain (nDCG)
- Discounted Cumulative Gain (DCG)
- Average Precision (AP)
- Mean Average Precision (MAP)

RankDCG possesses three fundamental properties:
1. Consistent lower and upper score bounds (from 0 to 1)
2. Works with non-normal value distribution
3. Has transitivity property

### Installation & Usage

The setup is straightforward: download the package and add the `ranking_measures` directory to your Python path or project folder.

```python
from ranking_measures import measures
print(measures.find_rankdcg([9,3,1], [5,1,7]))
# Returns: 0.125
```

This example demonstrates evaluating a movie recommendation algorithm where reference scores [9,3,1] represent ideal preferences, while [5,1,7] represent the algorithm's predictions.

### Resources

- **GitHub Repository**: [ranking_measures](https://github.com/dkaterenchuk/ranking_measures) (38+ stars)
- **Research Paper**: [arXiv:1803.00719](https://arxiv.org/pdf/1803.00719)
- **License**: MIT
- **Citation**: Katerenchuk & Rosenberg (2016), LREC 2016 proceedings

This work contributes to the advancement of evaluation methodologies in information retrieval, recommendation systems, and other ranking-based applications.
