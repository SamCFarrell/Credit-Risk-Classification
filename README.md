# Credit Risk Classification

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and basic information on what you were trying to predict
* Describe the stages of the machine learning process you went through and touch on any methods you used.
* Provide a basic summary of the results as well as any comments/recommendations.   

## Purpose
The goal of this exercise was to create a Logistic Regression classification model that can accurately predict wheather a loan has a healthy or high-risk Loan status. 

## Data/Variables
The analysis used data from the [`lending_data` CSV File](Resources/lending_data.csv) which includes the financial information of various applicants and and details about their respective loans. These include a borrower's `income`, `total debt`, `debt-to-income ratio`, `number of other accounts`, `derogatory credit marks` as well as their `principal` and `interest rate`.

The data also included a binary label for `loan status` with `0` representing "healthy" and `1` representing "high-risk". Given that this is what we are trying to predict, it was seperated from the rest of the data and used as the target (`y`) while everything else was used as the features (`X`).

Of the origional target data, loans with a status of healthy(`0`) had a value count of 75036 and loans with a status of high-risk(`1`) had a value count of 2500. This makes the total of 77536 values with high-risk loans composing roughly 3.22% of that total.

## Stages/Methods
The first step in this machine learning process is to create a logistic Logistic Regression model using the origional data. After dividing the features and target data into testing and training sets,
I initialized the `sklearn.linear_model.LogisticRegression` model and `fit` it using the training data. From there I used the `testing_features` data to make predictions, and evaluated the model using the `testing_targets`data and said predictions.

The second step is to create a second Logistic Regression model using resampled data. I initiated the `imblearn.over_sampling.RandomOverSampler` model and used the `fit_resample` function to create the `resampled_features` and `resampled_targets` sets. From there, I initialized the second Logistic Regression model, `fit` it using the resampled data and repeated the same prediction/evaluation process outlined above.

## Results

Model Evaluation Scores:
* Machine Learning Model 1:
  * Balanced Accuracy Score: 0.9520479254722232 (95.2%)  
  * Healthy Loans:
    * Precision: 1.00 (100%)
    * Recall: 0.99 (99%)
  * High-risk Loans:
    * Precision: 0.85 (85%)
    * Recall: 0.91 (91%)

* Machine Learning Model 2:
  * Balanced Accuracy Score: 0.9936781215845847 (99.7%)
  * Healthy Loans:
    * Precision: 1.00 (100%)
    * Recall: 0.99 (99%)
  * High-risk Loans:
    * Precision: 0.84 (84%)
    * Recall: 0.99 (99%)

## Summary
From a performance standpoint, the second moddel (using resampled data) seems to be the best. It's balanced accuracy score (99.7%) and recall score for high-risk loans (99%) are much higher than those of the first model (95.2% and 91% respectively) with all else remaining the same.  

While high-risk loans make up a relatively small portion of the data, their impact to creditors is disproportionately negative compared to healthy ones. It is, therefore, vital that models are able be able to successfully predict/recall high-risk loans.

Both models have reletively the same precision score for predicting high risk loans (85% for the first and 84% for the second). While the latter is slightly lower, the increases to balanced accuracy and recall in the second model are significant enough to to warrent it's recommendation over the first.

---

