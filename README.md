# Recipes and Ratings Report

by Christine Wu (chw081@ucsd.edu) and Zhiqing Wang (zhw055@ucsd.edu)

---

## Introduction

In this project, we studied some recipes' data based on two raw data sets: RAW_recipes.csv and RAW_interactions.csv. 
We focused on the question: **What is the relationship between the cooking time and rating of recipes?**
The importance of this question is to know if the cooking time potentially influences people's preferences through observation of rating and also if the time taken by the user is related to their ratings.
There are 234429 rows in the dataset.
Based on the question, we mainly focus on two columns: 'rating' and 'minutes'. <br>
**'rating'**: Recipe rating given by user <br>
**'minutes'**: Minutes to prepare recipe

---

## Cleaning and EDA

Before analyzing the data, the raw data needs to be processed first。

Genernal Cleaning:
Step 1: combine two Datasets to one table with more information: with 234429 rows × 16 columns <br />
Step 2: create a column for average cooking time of each recipes to provide potential information: with 234429 rows × 17 columns  <br />
Step 3: seperate nutrition column to be easier for : with 234429 rows × 23 columns  <br />
Step 4: seperate submitted column to be easier for : with 234429 rows × 26 columns  <br />

After general cleaning, we focused back on our question ('rate' and 'minutes' columns)

### Univariate Analysis
First, we focused on the column 'minutes' distribution:
<iframe src="assets/raw_minutes.html" width=400 height=300 frameBorder=0></iframe>
The above figure doesn't show any trend well, which is largely because of outliers. 

So, we ploted the distribution of minutes again without outliers.
<iframe src="assets/cleaned_minutes.html" width=400 height=300 frameBorder=0></iframe>


Second, we focused on the column 'rating' distribution:
<iframe src="assets/rating.html" width=400 height=300 frameBorder=0></iframe>

### Bivariate Anallysis

## Assessment of Missingness
<iframe src="assets/min_mis_rate.html" width=800 height=600 frameBorder=0></iframe>

## Hypothesis Testing