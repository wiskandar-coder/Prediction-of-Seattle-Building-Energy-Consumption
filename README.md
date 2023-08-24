# Prediction-of-Seattle-Building-Energy-Consumption
The project is for predicting energy consumption and GHG emission of non-residential buildings of the city of Seattle. For that purpose, multiple supervided learning techniques were tested and the best technique is selected in terms of prediction time, error, and accuracy.

The project is divided into four sections:
~~~
1- First is the cleaning of the data.
    I started by importing the data from Open Food Facts website https://world.openfoodfacts.org/.
    The definition of the variables can be found in https://world.openfoodfacts.org/data/data-fields.txt
    Then, I cleaned the data by:
    - removing features with more than 80% missing values
    - removing food products with missing values on the nutritional informations
    - removing food products with wrong nutritional informations
    - removing food products without name or wrong barcode
    - removing duplicates on the product name and brand
2- Second we treat the missing values using:
    - iterative imputer for the highly correlated features
    - the median of the feature according to the category of the product
    - RandomForestClassifier for the other categorical columns like nutrition score and grade
3- Third we analyse the selected features:
    - univariate analysis of each feature
    - bivariate analysis to check for correlation between the features:
        - correlation factor using pearson method between the numerical features
        - ANOVA analysis between the categorical features and numerical features
            (because of asymetrique distribution of the numerical features,
             I should use Kruskal-Wallis test instead of ANOVA)
    - multivariate analysis using dimension reduction of PCA
4- Finally, arguments about the feasability of the idea are given
    (what missing in this project is the actual application)
~~~

The first and second points are covered in the notebook 'Exploration_notebook'.\
The third and fourth points are covered in the notebook 'Energy_prediction_notebook' for predicting the energy consumption and in the notebook 'GHG_prediction_notebook' for predicting the GHG emission of the buildings.\
A powerpoint presentation of the project can be shared under request.
