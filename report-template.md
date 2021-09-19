# Module 12 Credit Risk Classification

## Overview of the Analysis

* We have a dataset of historical lending activity from a peer-to-peer lending services company and we need to build a model to predict the high risk loans. 

* The dataset has two classes of data - healthy and high risk loans.

* Credit Risk is imbalanced with healthy loans easily outnumbering risk loans - There are 75036 healthy loans and 2500 high risk loans in the data sets 

* We split the data into training and testing sets. The training sets has 58162 total loans with 56271 (96.77%) Healthy Loans and 1881 (3.23%) High Risk Loans.

* Machine Learning Model 1: We build a Logistic Regression model that can identify the creditworthiness of borrowers using this imbalanced training data to predict the high risk loans.

* We randomly oversample the high risk loans training data to balance the training data - we now have 56271 Healthy Loans and 56271 High Risk Loans in the oversampled training data.

* Machine Learning Model 2: We build another Logistic Regression model using the resampled training data to predict high risk loans.

* Comparing Machine Learning Model 1 and Model 2, we determine that the resampled Logistic Regression Model (Machine Learning Model 2) improves the performance for predicting high risk loans. 


## Results

Describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Accuracy: 0.95
  * Precision for Healthy Loans: 1.00
  * Recall for Healthy Loans: 0.99
  * Precision for High Risk Loans: 0.85
  * Recall for High Risk Loans: 0.91


* Machine Learning Model 2:
  * Accuracy: 0.99
  * Precision for Healthy Loans: 1.00
  * Recall for Healthy Loans: 0.99
  * Precision for High Risk Loans: 0.84
  * Recall for High Risk Loans: 0.99

## Summary

* Machine Learning Model 2 performs better than the Machine Learning Model 1

* With Machine Learning Model 2, we improved our accuracy from 0.95 to 0.99. 
* The Precision and Recall for the Healthy Loans is the same for both the models. 
* We lose slightly on the precision for High Risk Loans (0.85 for Model 1 vs 0.84 for Model 2). So, model 2 has 1% more chance of wrongly predicting healthy loans as high risk loans. This may require more scrutiny and will have associated cost of further reviewing the high risk loans or may result in some unnecessary rejections which can cause some loss of business on credit worthy applications.
* The recall for High Risk Loans improves from 0.91 (Model 1) to 0.99 (Model 2). So, with Model 2, 99% of the actual high risk loans are predicted accurately and only 1% of the actual high risk loans are classified as healthy loans. The risk and associated cost of default is reduced significantly. 
* Overall Model 2's 8% more chance accurately predicting high risk loans as high risk far outweighs its 1% more chance of wrongly predicting health loans as high risk. 
