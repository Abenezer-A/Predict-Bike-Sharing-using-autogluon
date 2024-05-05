# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Abenezer Alemayehu

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
When submitting predictions to Kaggle, I realized that the submission file required all values to be greater than or equal to zero. However, the predictor's output contained negative values. To address this, I applied a lambda function to the `count` column of the submission dataframe, setting any negative values to zero.

### What was the top ranked model that performed?
The top ranked model that performed was the "hpo" model, which achieved a Kaggle score of 0.47712.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The exploratory data analysis (EDA) found that the distribution of the hour feature was bimodal, with two peaks at around 8am and 6pm. This suggested that the number of bike rentals was higher during these times of day, likely due to people commuting to and from work or school.

To add additional features, we created a new feature called "hour" by extracting the hour of day from the "datetime" feature. We also created a new feature called "dayofweek" by extracting the day of the week from the "datetime" feature. These new features were then used as inputs to the AutoGluon model.

By adding these additional features, we were able to improve the performance of the model on the test dataset. The initial model achieved a root mean squared error (RMSE) of 1.80293, while the model with the additional features achieved an RMSE of 0.61673. This represents a significant improvement in the model's accuracy.

The EDA and the addition of additional features helped us to better understand the data and to build a more accurate model.

### How much better did your model preform after adding additional features and why do you think that is?
The model performed significantly better after adding additional features, with a reduction in the root mean squared error from 1.80293 to 0.61673. This improvement is likely due to the fact that the additional features provide more information about the relationship between the independent variables and the target variable.

* hour
* dayofweek

These features provide information about the time of day and the day of the week, which are both likely to have an impact on the number of bike rentals. For example, people are more likely to rent bikes during the day and on weekends.

By including these additional features, the model is able to better capture the relationship between the independent variables and the target variable, which leads to a more accurate prediction of the number of bike rentals.


## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The model performed 73.54% better after trying different hyperparameters.

### If you were given more time with this dataset, where do you think you would spend more time?
- Spend more time on feature engineering and selection.
 - Explore different models and hyperparameter tuning.
- Perform more extensive data analysis to identify patterns and trends.


### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|default|default|default|1.80293|
|add_features|default|default|default|0.61673|
|hpo|num_boost_round|learning_rate|scheduler|0.47712|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary
Overall, the code provides a comprehensive workflow for training and evaluating a model for bike-sharing demand prediction using AutoGluon, including data preparation, feature engineering, hyperparameter optimization, and submission to Kaggle.
