# kaggle-predicting-optimal-fertilizers
This is my submission for [Kaggle Playground Series S5E6 Predicting Optimal Fertilizers](https://www.kaggle.com/competitions/playground-series-s5e6).

I achieved 650th/2650 (~top 25%) in this competition and built an Ensemble model for the first time.

# Summary

Our objective is to select the best fertilizer for different weather, soil conditions and crops.

We could make 3 predictions for each data entry. The evaluation metric is Mean Average Precision @ 3 (MAP@3).

We first examine the distributions of the features and noticed that they are quite even, which is expected for this synthetic dataset.

We found that adding derived columns like 'K/N Ratio', 'P/N Ratio' and 'Env Max' improves prediction precision.

The mutual information of those derived features are generally higher than original features.

We trained one XGBoost model and one LightGBM model and then trained an ensemble LightGBM model to determine the final predictions.

For the competition, we submitted the version with 5-fold cross validation and tried 10-fold cross validation afterwards.

The findings is that 5-fold CV outperformed 10-fold CV as 10-fold CV could be overfitting.

# Learnings from Winners

1. Feature Engineering - Soil Type x Crop Type is a strong feature that we should include.

2. Ensemable Structure - They tend to use a diverse set of models do the ensemable, including XGBoost, LightGBM, Logistic, Neural Network with various hyperparameter sets.

3. Hyperparameter Optimization - Use framework like 'optuna' to tune hyperparameters can improve performance.
