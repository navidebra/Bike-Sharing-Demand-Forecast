# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Navid Ebrahimi-Madiseh

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
Negative predictions needed to be converted to 0 in order for Kaggle to accept submission.

### What was the top ranked model that performed?
After model tuning, RandomForest and XGBoost performed the best.
However, The WeightedEnsemble_L3, L2 always outperformed others as they are weighted average of multiple models.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
Matrix Correlation showed that temp and atemp (Reel Feels) are highly correlated, then accordingly temp was removed.
Datetime was broken down into year, month, and hour.
other categorical variables were set as categories in order for AutoGluon to identify them correctly.

### How much better did your model preform after adding additional features and why do you think that is?
Significantly better, as features especially time were broken down into smaller parts and represented each observation better. Consequently, upon adding additional features to the model kaggle score improved almost by 7%, from 1.80 scored by baseline model in kaggle, to 1.68 after feature engineering.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Almost no improvement was visible after multiple iterations of tuning.

### If you were given more time with this dataset, where do you think you would spend more time?
Trying RNN instead of other models and tuning appropriately.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|Default|Parsing Dates|GBM, CAT, RF|1.80|
|add_features|Default|New columns Added|NN_TORCH, XG|1.68|
|hpo|Default|feature selection|num_trials = 3|1.83|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.
![model_test_score.png](img/model_test_score.png)

## Summary
Data was fairly cleaned and only needed 2 columns removed ['casual', 'registered] whichi weren't present in the test dataset, datetime columns needed to be broken down, and highly correlated values could be removed. After preparation and EDA model performance and Kaggle score were highly improved by 7%. However, hyperparameters optimization didn't help much. Considering RNN models might be worth the time in this case.
