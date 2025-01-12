---
title: "LECTURE 11: Non-parametric Statistics"
date: 2024-12-27T19:15:44+02:00
deadline: "No assignment"
categories: ["Statistics"]
draft: false
---

#### Lecture summary:

Non-parametric tests are hypothesis-testing methods that do not require assumptions about the population parameters, making them robust alternatives to parametric tests, especially when data violate standard assumptions such as normal distribution and equal variances. Common challenges include ceiling or floor effects, skewness, and the presence of outliers. 

To address these issues, data transformations—such as square root, logarithmic, or inverse transformations—are employed to normalize distributions. For negatively skewed data, a reflection transformation precedes these adjustments. Alternatively, rank-order transformations convert scores to ranks, resulting in uniform distributions and facilitating rank-order tests. These tests compare group medians rather than means and are advantageous when scores are inherently ranks.

Computer-intensive methods like randomization and bootstrap tests have revolutionized statistical analysis by enabling repeated computations to assess data robustness. Randomization tests evaluate all possible data reorganizations to determine the likelihood of the observed configuration under chance, while bootstrap tests estimate statistic consistency by generating numerous resampled datasets. These methodologies ensure flexibility and precision in data analysis, particularly in psychological and social sciences, where data often deviate from idealized assumptions.

#### Reading materials:

###### Mandatory: 

Aron, A., Coups, E. J., & Aron, E. N. (2013). *Statistics for psychology* (6th ed.). Pearson. {{< a_blank title="(.pdf)" url="https://ibuit-my.sharepoint.com/:b:/g/personal/kirjakovski_ibu_edu_mk/EY8YX1R78ChDqORSuUCMc-0BJXGBAPEKL8k-AoSJ_B_0qw?e=wdi6Us">}}

* Chapter 14: Strategies When Population Distributions  Are Not Normal  Data Transformations and Rank-Order Tests
