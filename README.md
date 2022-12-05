# Cuisine Recommender System

This cuisine recommender system is adapted from [What's Cooking](https://www.kaggle.com/competitions/whats-cooking/) on Kaggle.

### Folder Guide
* EDA & Data Preprocessing contains exploratory data analysis and numeric generation.
* Feature Engineering contains one-hot encoding and frequency technique.
* Model - One Hot Encoding contains RFC, GB, Multinomial NB, Linear and RBF SVC.
* Model - Frequency Technique contains RFC, Linear SVC, and Bernoulli NB models.
* Source Files contains all json/csv files required by all notebooks excluding trainOneHotEncoded.csv.
trainOneHotEncoded.csv can be generated in the 'One-Hot Encoding' notebook.

### Problem Statement

Have you ever experienced the feeling that when you open the fridge, you have a list of/remaining ingredients, you might ask yourself
what can you prepare with those ingredients? Introducing the cuisine recommender system, 
designed to recommend potential cuisine that can be prepared given a set of ingredients.

### Exploratory Analysis

Here, we explore the following frequency distributions:
* Top 20 ingredients
* Cuisine types
* Top 20 ingredients for Italian cuisine
* Number of cuisine type in which top 20 and bottom 20 ingredients appear
* Number of ingredients appearing in each cuisine type

### Data Preprocessing: Numeric Generation

We find and generate unique numbers for each ingredient and cuisine type to be used later during feature engineering.

### Feature Engineering: One-Hot Encoding

Each ingredient is a Bernoulli random variable. In other words, it is either present or not present in each sample.
Due to a large number of unique ingredients, the number of features is 6714.

### Feature Engineering: Number of Ingredients by Cuisine Type (Frequency Technique)

The concept of this feature engineering:

* An ingredient which appears at least once in all 20 cuisine types can be classified as 'general' ingredient.
* For an ingredient which does not appear in all different cuisine types, 
if the highest occurrence by cuisine type is at least 10, 
this ingredient will be classified as all cuisine types with at least 10 times appearance. 
For example, black olives appear in greek (31), italian (67), mexican (92), brazilian (21) cuisines. 
So, black olives will be classified as greek, italian, mexican, or brazilian ingredient.
* For an ingredient which does not appear in at least 10 times in at least one cuisine type, 
it will be classified as the cuisine type with highest occurrence.

This feature engineering has successfully reduced the number of features from 6714 to 21 while maintaining model performance.

### Model: One-Hot Encoding

* Random Forest Classifer (74% accuracy)
* Linear Support Vector Classifier (77% accuracy)
* Bernoulli Naive Bayes (71% accuracy)

### Model: Frequency Technique

* Random Forest Classifier (74% accuracy)
* Gradient Boosting (75% accuracy)
* Linear Support Vector Classifier (74% accuracy)
* RBF Support Vector Classifier (76% accuracy)
* Multinomial Naive Bayes (69% accuracy)