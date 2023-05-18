# Savor and Score: Recipes and Ratings Report

by Christine Wu (chw081@ucsd.edu) and Zhiqing Wang (zhw055@ucsd.edu)

---

## Introduction

In this project, we studied some recipes' data based on two raw data sets: RAW_recipes.csv and RAW_interactions.csv. 
We focused on the question: **What is the relationship between the cooking time and rating of recipes?**
The importance of this question is to know if the cooking time potentially influences people's preferences through observation of rating and also if the time taken by the user is related to their ratings.
There are 234429 rows in the dataset.
Based on the question, we mainly focus on two columns: 'rating', 'minutes', and 'sub_day'. <br>
**'rating'**: Recipe rating given by user <br>
**'minutes'**: Minutes to prepare recipe <br>
**'sub_day'**: Day of the month for date that recipe was submitted

---

## Cleaning and EDA

Before analyzing the data, the raw data needs to be processed first。

### Data Cleaning
Step 1: combine two Datasets to one table with more information: with 234429 rows × 16 columns <br>
Step 2: create a column for average cooking time of each recipes to provide potential information: with 234429 rows × 17 columns  <br>
Step 3: seperate nutrition column to be easier for accessing data in float values individually and for missingness dependency test: with 234429 rows × 23 columns  <br>
Step 4: seperate submitted column to be easier for accessing data in numberical (int) values individually and for missingness dependency test: with 234429 rows × 25 columns  <br>

|rating|minutes|sub_day|
| --- | --- | --- |
| 4 | 40 | 27 |
| 5 | 45 | 11 |
| 5 | 40 | 30 |
| 5 | 40 | 30 |
| 5 | 40 | 30 |

After general cleaning, we focused back on our question ('rate' and 'minutes' columns)

### Univariate Analysis
First, we focused on the column 'minutes' distribution:
<iframe src="assets/raw_minutes.html" width=400 height=300 frameBorder=0></iframe>
The above figure doesn't show any trend well, which is largely because of outliers. 

So, we ploted the distribution of minutes again without outliers.
<iframe src="assets/cleaned_minutes.html" width=400 height=300 frameBorder=0></iframe>
From the above figure, we find there are more values on multiples of 5, like 5, 10, 15...Also, the graph is skewed to the right.


Second, we focused on the column 'rating' distribution:
<iframe src="assets/rating.html" width=400 height=300 frameBorder=0></iframe>
The graph is skewed heavily to the left. We see most data are gathered at a rating of 5 and the density probability increases as the rating increases.

### Bivariate Analysis
The relationship between 'rating' and 'minutes' in boxplot:
<iframe src="assets/BA1.html" width=500 height=400 frameBorder=0></iframe>
For each group of rating, we see the boxplot is generally skewed to the right. There are no outliers on the lower bounds while multiple outliers exists above the upper bound.

The relationship between 'rating' and 'minutes' in scatterplot:
<iframe src="assets/BA2.html" width=500 height=400 frameBorder=0></iframe>
This figure shows the data is more likely skewed to the right since the scattered data points are more clustered on the lower end. We see that for all group of rating, the longest time is 120 minutes.<br>

### Interesting Aggregates

|rating | minutes|
| --- | --- |
|1.0 | 38.717320|
|2.0 | 39.630958 |
|3.0 | 38.088193 |
|4.0 | 36.474287 |
|5.0 | 36.364948 |

This shows the mean of minutes grouped by rating. The dataframe gives insights on comparing mean differences of the cooking time for ratings from 1 to 5. It helps us to see people might prefer recipes that take less time and rate them higher compared to longer time.

## Assessment of Missingness

### NMAR Analysis

### Missingness Dependency

 The distribution of column 'minutes' when column 'rating' is missing and the distribution of column 'minutes' when column 'rating' is not missing:
<iframe src="assets/min_miss_rate.html" width=500 height=300 frameBorder=0></iframe>

The empirical distribution of the absolution difference in minutes means of permutation tests with the absolution difference in minutes means:
<iframe src="assets/ED_min_mean.html" width=500 height=300 frameBorder=0></iframe>

 The distribution of column 'sub_day', day of the month for date that recipe was submitted, when column 'rating' is missing and the distribution of column 'sub_day' when column 'rating' is not missing:
<iframe src="assets/sub_day_miss_rate.html" width=500 height=300 frameBorder=0></iframe>

The empirical distribution of the absolution difference in day means of permutation tests with the absolution difference in day means:
<iframe src="assets/ED_day_mean.html" width=500 height=300 frameBorder=0></iframe>

## Hypothesis Testing
<iframe src="assets/fig_hypo.html" width=500 height=300 frameBorder=0></iframe>