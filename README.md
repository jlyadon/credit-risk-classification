# credit-risk-classification

## Files in the repository

### credit_risk_classification.ipynb

This notebook contains the code for training the various machine learning models, with assessment and comments.

### Resources/lending_data.csv

This csv contains the raw data for developing the models.

## Analysis Report

### Overview of the Analysis

The analysis conducted in this repository attempts to develop a logistic regression model for predicting the status of loans as healthy or high-risk. The data set includes financial information such as the initial principle amount of the loan, the interest rate, and the borrower's annual income. Healthy loans are assigned a 'loan status' of 0; loans at high risk of defaulting are assigned a 'loan status' of 1. The dataset included 75,036 healthy loans and 2500 high-risk loans.

Developing the models included extracting a set of data on which to train the model, fitting the model to this training data, and testing the model against a testing set, or the whole dataset. It is preferable to test against data that does not include any of the data on which the model was trained, but for constraints of time and technology, this was not possible for this project.

### Results

Five models were trained and tested.

* lr1_model:
    * The first model was trained against 1,250 randomly selected high-risk loans and 1,250 randomly selected healthy loans.
    * This model scores very high on healthy loans and lower, though still well, on high-risk loans. 
        * Predictions of healthy loans returned a precision of 1.00, recall of 0.99, and an f-score of 1.00.
        * Predictions of high-risk loans returned a precision of 0.85, a recall of 0.99, and an f-score of 0.92.
        * This indicates a low risk of false negatives in identifying high-risk loans, but a significant risk of false positives.
* lr2_model:
    * The second model was trained against 1,250 randomly selected high-risk loans and 7,500randomly selected healthy loans. This sacrifices balance in training data for the inclusion of more data in the training set.
    * The model returns very similar results to lr1_model.
        * Predictions of healthy loans returned a precision of 1.00, recall of 0.99, and an f-score of 1.00.
        * Predictions of high-risk loans returned a precision of 0.86, a recall of 0.98, and an f-score of 0.92.
        * This indicates a low risk of false negatives in identifying high-risk loans, but a significant risk of false positives.
* lr3_model:
    * The third model was trained using a division of data provided by the train_test_split function with default parameters.
    * Compared to the first two, this model performs slightly more poorly in identifying high-risk loans 
        * Predictions of healthy loans returned a precision of 1.00, recall of 1.00, and an f-score of 1.00.
        * Predictions of high-risk loans returned a precision of 0.87, a recall of 0.89, and an f-score of 0.88.
        * This model includes a significant risk of both false negatives and false positives.
        * This model is, however, at a disadvantage compared to the other two: it was tested against data that did not include the training data. It did not perform significantly better when tested against the entire dataset. Precision and recall scores changed by <= 0.01 and f-scores did not change.
* lr4_model:
    * The fourth model was developed in the same way as the third, except for the employment of the stratify parameter. The stratify parameter sets the function to include equal proportions of healthy and high-risk loans in training and testing data.
    * Results did not improve significantly over the third model, with f-scores increasing by <= 0.01.

### Summary

Models lr1_model and lr2_model perform best in identifying high risk loans. Their higher f-scores indicate stronger overall performance. More importantly, their higher recall scores indicate substantially lower risk of false negatives. A false-positive for high risk on a loan could mean the financial institution misses an opportunity. A false-negative could mean substantial loss of money. Therefore, the very slightly lower precision of models lr1_model and lr2_model (which indicate higher risk of false positives) are a more-than-acceptable trade-off for their substaintially higher recall scores (which indicate lower risk of false negatives).