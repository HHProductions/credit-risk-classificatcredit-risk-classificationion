credit-risk-classificationion
# Module 20 Challenge

## Overview of the Analysis

In order for lending organisations to minimise risk associated with customers defaulting on their loans, there is a need to generate risk predictions for new opportunities.

In order to develop such prediction tool, 77536 lines of historical lending data consisting of the following information was available for analysis.
Features:
- loan_size
- interest_rate
- borrower_income
- debt_to_income
- num_of_accounts
- derogatory_marks
- total_debt
Label:
- loan_status

The available data was used to predict the loan status (healthy loan or high risk loan)

The data was separated into training and test data. Logistic Regression model, which is a practical tool for this type of classification problems, was used to train the system and then the test data was used to check prediction.
Balanced Accuracy Score, confusion matrix and classification report was used to evaluate the accuracy of prediction. 
To improve prediction, RandomOverSampler module from the imbalanced-learn library was used to resample the data. This was followed by training and testing.

It  is important to  note that only  2500 out of 77536 data was considered high risk. Thsi is a very small percentage for the analysis.

 
## Results

* Machine Learning Model 1: Logistic Regression

Balanced Accuracy Score: 0.9520479254722232
The balanced accuracy score averages the accuracy for the helthy and high risk loans. This is preferenable given the inbalance in the amount of data for each class. The obtained score is a good value, but due to the financial risk associated with the lending this should be improved.

Confusion Matrix
						Predicted Healthy Loan	Predicted High_Risk Loan
Actual Healthy Loan		18663					102
Actual High_Risk Loan	56						563

classification report for the model
          precision  recall f1-score  support

 0 (healthy loan)    1.00   0.99   1.00   18765
1 (high-risk loan)    0.85   0.91   0.88    619

     accuracy              0.99   19384
     macro avg    0.92   0.95   0.94   19384
   weighted avg    0.99   0.99   0.99   19384

The precision provides the ratio of True Positives/True + False positives.
For healthy loans are accurately predicted by the model. However 85% of thge high-risk predicted loans are accurate. There are too many False High-Risk loan predictions. This can result in lost business. i.e. loans are not approved as they are considered high risk even though they are not.

Recall provides the ratio of True Positives/True Positives + False Negatives.
this shows high accuracy again for healthy loans, but not so for high risk loans

* Machine Learning Model 2: Logistic Regression with oversampling

Balanced Accuracy Score: 0.9936781215845847
The balanced accuracy score for Model 2 is significantly improved over the Model 1.

Confusion Matrix
						Predicted Healthy Loan	Predicted High_Risk Loan
Actual Healthy Loan		18649					116
Actual High_Risk Loan	4						615

classification report for the model
          precision  recall f1-score  support

 0 (healthy loan)    1.00   0.99   1.00   18765
1 (high-risk loan)    0.84   0.99   0.91    619

     accuracy              0.99   19384
     macro avg    0.92   0.99   0.95   19384
   weighted avg    0.99   0.99   0.99   19384

Oversampling improved the Balanced Accuracy Score. This second model is more useful to predict high risk loans.
Like with Model 1 the precision and recall have a high value for Healthy loans .
For High-risk loans the precision is marginally lower than before. While we improved the number of correctly predicted High-risk loans (563 to 615), the number of falsely predicted High-risk loans also increased (102 to 116)
With the increase in correctly predicted High-risk loans, lower number of high-risk loans were predicted as healthy. Consequently teh recall has increase significantly.


## Summary

Based on the analysis it is recommended that model 2 (logistic regression with oversampling utilised. The predictions ensure a very small percentage (4/619, 0.65%) of high risk loans are classified as healthy. A significant improvement on 56/619 for Model 1.

It is important to note that the data is based on historical information and external factors like economy, regulatory changes, may impact long term accuracy of the prediction.