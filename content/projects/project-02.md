---
title: "Post Collegiate Income Prediction 🏛💲 "
date: 2022-04-05T23:15:00+07:00
slug: post-college
category: projects
weight: 2
summary:
description:
cover:
  image:
  alt:
  caption:
  relative: true
showtoc: true
draft: false
---

### Background
The U.S. Department of Education launched College Scorecard in September 2015 as a means of gathering more data on degree-granting institutions, the demographics of college students, and the status of alumni of these institutions [[1](https://collegescorecard.ed.gov/data/)]. By doing so, the U.S. Department of Education hopes to empower students to make more informed college decisions through a data-driven  approach. Considering the soaring cost of higher education as well as the accompanying rise of student debt, prospective students can greatly benefit from such information. However, College Scorecard has faced scrutiny due to its omission of over 700 colleges, particularly community colleges, in its data set [[2](https://www.washingtonpost.com/news/grade-point/wp/2015/10/15/hundreds-of-colleges-missing-from-obamas-college-scorecard/?utm_term=.1b5b030701c0)]. Hence, applying machine learning to fill in omissions in the data set, particularly related to earnings and debt, and finding correlations between characteristics of colleges and the future success of their alumni has great value to society. Despite the relevance of machine learning to this issue, fairly little research has been done in this area. Machine learning has been used in several related topics, such as predicting corporate earnings and predicting income based on census data about individuals [[3](http://ieeexplore.ieee.org/document/6753946/),[4](https://archive.ics.uci.edu/ml/datasets/Census+Income)]. However, no research has been conducted on using college data to predict the earnings and debt of its alumni, potentially because higher-education institutions do not condone a solely numbers-based approach to the college selection process.

### Goal 
We hope to use a variety of machine learning models to make predictions regarding post-college earnings and debt of alumni who were on federal financial aid from various institutions based on factors that reflect the current status of each institution, such as majors and degrees offered, tuition, and admissions rates. Such statistics are easier to obtain than post-college earnings, so our predictions can be used to fill in gaps in the current data set and potentially unearth interesting factors that influence alumni earnings and debt. In addition, alumni earnings can be compared with tuition costs and average student debt to determine the typical interest and length of student loans for a particular school.

## DATA AND FEATURE SET PROCESSING 
### Data
College Scorecard provides a publicly available data set consisting of approximately 2000 metrics for 7805 degree-granting institutions [[1]](https://collegescorecard.ed.gov/data/). These metrics include demographic data, test scores, family income data, data about the percentages of students in each major, financial aid information, debt and debt repayment values, earnings of alumni several years after graduation, and more. We chose to focus on the 2011 data set because it was the least sparse data set in the last five years (more future earnings information was available than for more recent years). Our first tasks were to select variables to predict, transform the dataset into pairs of features and prediction variables, and segment the data for evaluation purposes.

### Selecting Features and Prediction Values
We chose two values for our prediction variables – the median postgraduate debt and the median postgraduate earnings for alumni 6 years after graduation. We then went through several steps to prune the full feature set to an initial feature list. We first eliminated all features that had non-numerical/categorical values (primarily school name).

Additionally, we removed unrelated features that should not be used to make predictions, such as features that provided the number of students in different data collection cohorts. We also removed all features related to debt, earnings, and repayment. All metrics in these categories are highly correlated with the two we chose to predict, so they would be weighted very strongly compared to other features and would hurt the ability of our models to generalize to schools without any of this information available, which is the motivation for this project. Finally, after the preprocessing steps listed above and the non-standard data value processing described below, we removed all features (mostly null-indicators and unused categories) which had only one value for all examples, as they offer no predictive power.


### Preprocessing Non-Standard Data Values

Some features in the data set were categorical fields; we chose to turn each category into separate indicator features. Many values in the data set were listed as "NULL", and a portion of these were meaningful (for example, indicating the absence of a binary feature) rather than indicative of missing data. In order to transform the nulls into usable numeric values while preserving the original meaning of the nulls, we replaced each null value with 0 and created an extra feature for each feature that contained null values. This new feature used 1s and 0s to indicate whether the value in the previous feature was null or non-null. For categorical fields that contained null values, we created just one null indicator feature in addition to the category indicators described previously.

[Here's the Code](https://github.com/hrishikeshh/FortuneTeller)
