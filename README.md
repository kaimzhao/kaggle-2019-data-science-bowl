# Kaggle Compitition - 2019 Data Science Bowl

## Executive Summary:

### Introduction
The competition, sponsored by PBS KIDS, is to gain insights into how media can help children learn important skills for success in school and life. The participants use anonymous gameplay data from PBS KIDS Measure Up! App to develop models that predict scores on in-game assessments and create an algorithm that will lead to better-designed games and improved learning outcomes. Detailed description of the competition and data can be found on Kaggle throught the link below: https://www.kaggle.com/c/data-science-bowl-2019

### Results
The best performing score was produced by the average of the predictions by CatBoost and LightGBM models.

- Private Score: 0.543
- Public Score: 0.544
- [Kaggle Rank: 167/3497 (Silver Medal, Top 5%)](https://www.kaggle.com/c/data-science-bowl-2019/leaderboard)
- [Kaggle published notebook](https://www.kaggle.com/vlpavlov/silver-medal-solution-for-2019-data-science-bowl)

### Approach
- **Data Preparation**: The data preparation includes data processing, feature engineering, and feature selection.

- **Data Processing**: Removing assessment sessions without outcomes and calculating the accuracy group for the train data.

- **Feature Engineering**: We generate over 20,000 features using information from the given numerical (e.g., time) and categorical features (e.g., event code, title, etc.) and statistics of the data extracted from the event_data column. Detail see 1.2 Data Processing. There were ~2000 unique features after removing the duplicate columns.
Feature Selection: 400 most important features were selected for the final model. We ranked features through experiments with the Catboost model via local cross-validation. Note, permutation could have been a more general feature selection mechanism. However, since our final submission is based on Catboost and LightGBM, using important features ranked by the same model seems more relevant. Details of the op features can be found in 1.4 Feature Selection.
Modeling: We evaluated linear model, logistic regression, random forest, neural network, Catboost, and LightGBM algorithms. Based on the local cross-validation performance, we decided to choose the hybrid model with Catboost and LightGBM (best local cross-validation score) and single LightGBM model (best public score) as the two final submissions.

- **Model Evaluation**: We are aware that the public LB could be misleading especially when the model overfits the testing data used to calculate the public score. Our model selection relied on the local cross-validation. We performed 3-Fold cross-validation so that the size of the validation set was close to the actual testing set. We set the unit of analysis to be installation_id that was used to partition the data during the cross-validation. Ten iterations (total 30 validatinos) were performed and the average scores were used as the metric for model selection.

## Team Member
- [Vlad Pavlov](https://www.kaggle.com/vlpavlov)
- [Kai Zhao](https://www.kaggle.com/miecky)
