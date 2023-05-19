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

| |name | minutes | contributor_id | ... |rating|minutes|sub_day|
|--- | --- | --- | --- | --- | --- | --- | --- |
|0 | 1 brownies in the world best ever | 40 | 985201 | ... | 4 | 40 | 27 |
|1 | 1 in canada chocolate chip cookies | 45 | 1848091 | ... | 5 | 45 | 11 |
|2 | 412 broccoli casserole | 40 | 50969 | ... | 5 | 40 | 30 |
|3 | 412 broccoli casserole | 40 | 50969 | ... | 5 | 40 | 30 |
|4 | 412 broccoli casserole | 40 | 50969 | ... | 5 | 40 | 30 |

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
There exists a column **'name'**, the recipe name, that is **NMAR**. The missingness of the recipe name is dependent on itself because it is likely that the name depends on whether the user knows the recipe name or if the recipe has a name, which means if the recipe doesn't have a name, the value for column 'name' likely to be missing. Another column 'recipe_name_exist' could be used to check if the name for recipe exists or not.
NOT NMAR. People usually submit their scores casually after finishing the dishes, and this score has no impact on the submitters. Therefore, the lack of scores is unlikely to be related to one’s own numerical value. The lack of recipes ratings may be related to submitters' online activity, such as adding a column to record the amount of information people post on the website. Some people who are active online are more likely to fill in recipes ratings, while others who do not like or frequently express their opinions online are more likely to not fill in.

### Missingness Dependency

 The distribution of column 'minutes' when column 'rating' is missing and the distribution of column 'minutes' when column 'rating' is not missing:
<iframe src="assets/min_miss_rate.html" width=500 height=300 frameBorder=0></iframe>

The empirical distribution of the absolution difference in minutes means of permutation tests with the absolution difference in minutes means:
<iframe src="assets/ED_min_mean.html" width=700 height=400 frameBorder=0></iframe>

The missingness of 'rating' column does depend on the column 'minutes'. The figure for 'minutes' and 'rating' shows the distributions for cooking time is different when rating is missing and when it is not. When rating value is not missing, we see the distribution is more skewed to the right and there are many outliers above the upper bound compare to no outlier for when rating is missing. Then we see the observed statistic is much higher than the permutation test statistics. With a probability of 0 for getting an absolute difference as extreme as the observed statistic under the assumption that the missingness of 'rating' column does not depend on the column 'minutes', the p-value is 0. The prefered conclusion is the missingness of 'rating' column does depend on the column 'minutes'.

 The distribution of column 'sub_day', day of the month for date that recipe was submitted, when column 'rating' is missing and the distribution of column 'sub_day' when column 'rating' is not missing:
<iframe src="assets/sub_day_miss_rate.html" width=500 height=300 frameBorder=0></iframe>

The empirical distribution of the absolution difference in day means of permutation tests with the absolution difference in day means:
<iframe src="assets/ED_day_mean.html" width=700 height=400 frameBorder=0></iframe>

The missingness of 'rating' column does not depend on the column 'sub_day'. The figure for 'sub_day' and 'rating' shows the distributions for the submitted day is roughly similiar. The box plot also shows similiar ranges, median, and quantile values. From the empirical distribution, we see a large proportion of graph on the right side of the observed statistic suggesting the probability of getting an absolute difference value as extreme as the observed statistics is highly possible. By looking at probabilities of the histogram, the p-value is much larger than the significance level of 0.5. The prefered conclusion is the missingness of 'rating' column doesnot depend on the column 'sub_day'.

## Hypothesis Testing
To answer our **Sample Question: What is the relationship between the cooking time and rating of recipes?**, we focused on two columns 'minutes' and 'rating'.

**Before Moving to the Hypothesis Testing part - Imputation:**
Because from the above analysis, the missing of rating is related to minutes column, we decided to use Probabilistic imputation to fill in those missing.


### Hypothesis Testing: Permutation Test (one-tail)

**Null Hypothesis**: both low rating and high rating recipes corresponding to same minutes (draw from same population)

**Alternative Hypothesis**: recipes with higher rating corresponding to lower minutes (one-tail)

**Test statistic**: the different of the mean of minutes - to compare 2 numerical columns

**Significance Level** : 0.05 - conventional

(we choose one-tail test because it is reasonal to think that popular recipes (or with high rate) corresponding to lower time to cook)

In order to easier compare rating, we seperated rating to two groups first.
1. rating 1-3 as low rate (as **False** in high_rate column)
2. rating 4-5 as high rate (as **True** in high_rate column)

Then, we run a permutation test with 500 runs to find distribution under null hypothesis.

<iframe src="assets/fig_hypo.html" width=700 height=400 frameBorder=0></iframe>

Conclusion: p_value is **0.0** less than 0.05 (significant level), therefore we **reject the null hypothesis** that recipes whether with higher rating or low one will corresponding to same minutes.