# Credit Risk Classification

Construct a Logistic Regression model to predict the creditworthiness of future borrowers of a peer-to-peer lending services company by classifying the historical lending activity.

## Overview of the Analysis

* We have a dataset of historical lending activity from a peer-to-peer lending services company and we need to build a model to accurately classify the loans as healthy or high risk loans and predict the high risk loans. We want to minimize the cost associated with incorrect classification of loans and maximize the profit associated with the approving maximum healthy loans.

* The dataset has two classes of data - healthy and high risk loans.

* The dataset has also more details about the previous loans including the loan size, interest rate, borrower income, debt to income, number of accounts, derogatory marks and total debt. We need to use this information to identify healthy vs high risk loans. 

* Credit Risk is imbalanced with healthy loans easily outnumbering risk loans - There are 75036 healthy loans and 2500 high risk loans in the data sets 

* We split the data into training and testing sets. The training sets has 58162 total loans with 56271 (96.77%) Healthy Loans and 1881 (3.23%) High Risk Loans.

* Machine Learning Model 1: We build a Logistic Regression model that can identify the creditworthiness of borrowers using this imbalanced training data to predict the high risk loans.

* We randomly oversample the high risk loans training data to balance the training data - we now have 56271 Healthy Loans and 56271 High Risk Loans in the oversampled training data. This gives a balanced opportunity to the Logistic Regression to train on both the Healthy Loans and High Risk Loans.

* Machine Learning Model 2: We build another Logistic Regression model using the resampled training data to predict high risk loans.

* Comparing Machine Learning Model 1 and Model 2, we determine that the resampled Logistic Regression Model (Machine Learning Model 2) improves the performance for predicting high risk loans. 

### Steps

* Read the lending_data.csv lending data into a Pandas DataFrame.
* Create the labels set (y) from the “loan_status” column, and then create the features (X) DataFrame from the remaining columns.
* Check the balance of the labels variable (y) by using the value_counts function.
* Split the data into training and testing datasets by using train_test_split.
* Fit a logistic regression model by using the original training data (X_train and y_train) - Machine Learning Model 1
* Save the predictions on the testing data labels by using the testing feature data (X_test) and the fitted model (Machine Learning Model 1).
* Evaluate the model’s performance by calculating the accuracy score of hte model and using the confusion matrix and classification report
* Use the RandomOverSampler module from the imbalanced-learn library to resample the data. Confirm that the labels have an equal number of data points for healthy and high risk loans.
* Use the LogisticRegression classifier and the resampled data to fit the model and make predictions - Machine Learning Model 2.
* Evaluate the model’s performance by calculating the accuracy score of hte model and using the confusion matrix and classification report

## Results

Describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Logistic Regression with imbalance in training data.
  * Accuracy: 0.95 (95% accurate in predicting loans)
  * Precision for Healthy Loans: 1.00 (almost 100% accurate in the healthy loans predictions)
  * Recall for Healthy Loans: 0.99 (99% accurate in predicting healthy loans as healthy)
  * Precision for High Risk Loans: 0.85 (85% accurate in the high risk loans predictions)
  * Recall for High Risk Loans: 0.91 (91% accurate in predicting high risk loans as high risk)

* Machine Learning Model 2: 
  * Logistic Regression that oversamples high risk loan data before training
  * Accuracy: 0.99 (99% accurate in predicting loans)
  * Precision for Healthy Loans: 1.00 (almost 100% accurate in the healthy loans prediction)
  * Recall for Healthy Loans: 0.99 (99% accurate in predicting healthy loans as healthy)
  * Precision for High Risk Loans: 0.84 (84% accurate in the high risk loans prediction)
  * Recall for High Risk Loans: 0.99 (99% accurate in predicting high risk loans as high risk))

## Summary

* Machine Learning Model 2 performs better than the Machine Learning Model 1 overall and especially in terms of improved high risk loan prediction and it is recommened that Model 2 should be used for classifying the loans.

* Machine Learning Model 2 improved the Machine Learning Model 1's accuracy of 95% to 99% primarily through better prediction of high risk loans.
* The Precision and Recall for the Healthy Loans is the same for both the models. 
* We lose slightly on the precision for High Risk Loans (85% for Model 1 vs 84% for Model 2). So, model 2 has 1% more chance of wrongly predicting healthy loans as high risk loans. This can force the lending service to scrutinize the high risk loans to identify if they may actually be healthy. If they do so, there is a small penalty or cost associated with the extra processing of loans predicted as high risk loans. Otherwise, we have an opportunity cost of not approving healthy loans.
* The recall for High Risk Loans improves from 91% (Model 1) to 99% (Model 2). So, with Model 2, 99% of the actual high risk loans are predicted accurately and only 1% of the actual high risk loans are classified as healthy loans. The risk and associated cost of default is reduced significantly. 
* Overall Model 2's 8% more likelihood of accurately predicting high risk loans as high risk far outweighs its 1% more chance of wrongly predicting health loans as high risk. The cost of default associated with approving high risk loans far outweights the loss of potential profit associated with not approving health loans. Therefore, Model 2 performs much better than the Model 1.