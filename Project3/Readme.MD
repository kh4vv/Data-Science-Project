# House Prices - Advanced Regression Techniques

### Predict sales prices and practice feature engineering, RFs, and gradient boosting

## Competition Description

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/cbfbed1a-99b9-4a27-b1d5-aff9cc6e3753)

Ask a home buyer to describe their dream house, and they probably won't begin with the height of the basement ceiling or the proximity to an east-west railroad.
But this playground competition's dataset proves that much more influences price negotiations than the number of bedrooms or a white-picket fence.

With 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa, this competition challenges you to predict the final price of each home.

## Acknowledgments

The Ames Housing dataset was compiled by Dean De Cock for use in data science education. It's an incredible alternative for data scientists looking for a modernized and expanded version of the often cited Boston Housing dataset. 

Photo by Tom Thain on Unsplash.

## Goal

It is your job to predict the sales price for each house. For each Id in the test set, you must predict the value of the SalePrice variable. 

## Data Overview

Here's a brief version of what you'll find in the data description file.

[DATA OVERVIEW](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data)

## Approach 

### EDA

Here are questions to me for EDA: 

1. Do we need all features?  
2. If not, what features do we want to use?  
3. Any new feature from combining/finding relationship between exist features?  
4. Do numerical features stay numerical? Or do categorical feature stay categorical?  
5. Any nomarlization needs for any features?  
6. What about missing values?  
and more...  

##### Dataset Basics

**Train data shape:**  (1460, 81)  
**Test  data shape:**  (1459, 80)  

**Numerical columns :** 36 + ID/SalePrice = total 38 
**Categorical columns:** 43

##### Categorical Feature Exploration

**Box Plot** : Check for outliers and figure out unrelavent features

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/ba76bdfc-88e1-4bf4-843c-74e9c970364b) 

From these box plots, there are three categorical columns that contains two options: Street, Utilities, CentralAir. Look at those data. 
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/3de08344-9465-4134-86d9-6847dd7de697) 

Remove Street and Utilities because of no relevant to prediction. Found more columns that unrelvant to prediction.  
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/acec3d94-e4c0-49ba-ba93-6f9747b6babe)

Deleted these three categorical features. 


##### Missing Values in each feature:  

##### Dependant Variable Characterisic

##### Feature Engineering



Visualization: 

Sale Price vs Month

Sale Price vs Properties Age

Sale Price vs Properties Remodeling Age

Heatmap



