# Report of Recipes and Ratings

by Christine Wu (chw081@ucsd.edu) and Zhiqing Wang (zhw055@ucsd.edu)

---

## Introduction

In this project, we studied some recipes' data based on two raw data sets: RAW_recipes.csv and RAW_interactions.csv. 
We focused on the question: **What is the relationship between the cooking time and rating of recipes?**
So, we mainly focus on two columns: 'rate' and 'minutes'

---

## Cleaning and EDA

Before analyzing the data, the raw data needs to be processed first。

Genernal Cleaning:
Step 1: combine two Datasets to one table with more information: with 234429 rows × 16 columns
Step 2: create a column for average cooking time of each recipes to provide potential information: with 234429 rows × 17 columns
Step 3: seperate nutrition column to be easier for : with 234429 rows × 23 columns

After general cleaning, we focused on our question ('rate' and 'minutes' columns)

First, we focused on the column 'minutes' distribution:
<iframe src="assets/raw_minutes.html" width=800 height=600 frameBorder=0></iframe>
The above figure doesn't show any trend well, which is largely because of outliers. 
So, we ploted the distribution of minutes again without outliers.

