# Prediction-of-Seattle-Building-Energy-Consumption
The project is for predicting energy consumption and GHG emission of non-residential buildings of the city of Seattle. For that purpose, multiple supervided learning techniques were tested and the best technique is selected in terms of prediction time, error, and accuracy.

The project is divided into four sections:
~~~
1- First is the cleaning of the data.
    I started by importing the data from the city of Seattle website https://data.seattle.gov/dataset/2016-Building-Energy-Benchmarking/2bpz-gwpy. The definition of the variables can be found there as well.
    Then, I cleaned the data by:
    - removing features with 100% missing values or not useful for the prediction
    - removing buildings with missing values or negative values on energy consumptions and GHG emissions
    - removing residual buildings since we are predicting energy consumptions and GHG emissions of non-residential buildings
    - removing buildings identified as low or high outlier (<5% and >95%) in terms of intensity (energy consumption/surface of the building)
    - removing buildings identified as outlier [Q1-5*IQR; Q3+5*IQR] in terms of energy consumptions and GHG emissions
2- Second we do some treatments listed below:
    - RandomForestClassifier for retrieving the missing zipcode of buildings using the infomations of geographic coordinate system, latitude and longitude, of the building
    - retrieving the missing value in the number of buildings of some property using the median of the number of buildings according to the usage category of the building
    - retrieving the missing value in the number of floor of some property using the median of the number of floor according to the usage category of the building
3- Third we do feature engineering by creating:
    - Building Age: age of the building with reference 2016
    - Property Use Type Count: Number of usage type of the property
    - Main Energy Source: main energy source from electricity or steam or natural gas
    - Energy Source Count: number of energy source used in the property
4- Fourth we analyse the selected features:
    - univariate analysis of each feature
    - bivariate analysis to check for correlation between the features:
        - correlation factor using pearson method between the numerical features
        - Kruskal-Wallis H-test between the categorical features and numerical features
5- Fifth, prediction of energy consumptions and GHG emissions:
    - Dividing the data into 80% train and 20% test
    - "for" loop to test the prediction with and without logarithmic scale of the target (energy consumptions and GHG emissions feature due to their asymmetric distribution)
    - "for" loop to test the prediction on different set/combination of selected features
    - "for" loop to test the prediction on different method for the normalisation of the numerical features (MinMaxScaler, StandardScaler, RobustScaler, et PowerTransformer)
    - "for" loop to test the prediction using different regression models (Linear, ElasticNet, KernelRidge, KNN, RandomForest, et XGBoost)
    - Pipeline together the categorical feature transformation (OneHotEncoder), the normalisation of the numerical features, and the regression model
    - Usage of GridSearchCV to find the optimal hyperparameters for the regression model
    - Usage of the optimal hyperparameters for the regression model to find training time, the error (MAE, RMSE), and the r2 score (for both train and test to check for overfitting)
    - Stock of the results in pandas df to be able to select at the end the the best regression model with the optimal hyperparameters, the best combination of features, the best normalisation method of the numerical features, and the need or not of log scaling the target
~~~

The first, second, third, and fourth points are covered in the notebook 'Exploration_notebook'.\
The fifth point is covered in the notebook 'Energy_prediction_notebook' for predicting the energy consumption and in the notebook 'GHG_prediction_notebook' for predicting the GHG emission of the buildings.\
A powerpoint presentation of the project can be shared under request.
