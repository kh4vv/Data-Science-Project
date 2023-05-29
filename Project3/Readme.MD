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

### Dataset Basics

**Train data shape:**  (1460, 81)  
**Test  data shape:**  (1459, 80)  

**Numerical columns :** 36 + ID/SalePrice = total 38 
**Categorical columns:** 43

### Categorical Feature Exploration

**Box Plot** : Check for outliers and figure out unrelavent features

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/ba76bdfc-88e1-4bf4-843c-74e9c970364b) 

From these box plots, there are three categorical columns that contains two options: Street, Utilities, CentralAir. Look at those data. 
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/3de08344-9465-4134-86d9-6847dd7de697) 

Remove Street and Utilities because of no relevant to prediction. Found more columns that unrelvant to prediction.  
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/acec3d94-e4c0-49ba-ba93-6f9747b6babe)

Deleted these three categorical features. Then handle the outliers in training set. 

### Missing Values in each feature:  

Here is the list of all features that have missing values - 19 of them.  
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/d7dd1c30-bd06-4616-8796-a96a8728a3bc)

19 columns with missing values. Majority missing values are in 'MiscFeature', 'Alley', 'Fence', 'FirePlaceQu'.  
'MiscFeature', 'Alley', 'Fence' > 80% missing values. I drop these features.  
 
### Dependant Variable Characterisic

Look at any skewness of dependant variable.  
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/f26e31b1-23b5-4b37-b989-343655305297)  

The dependant variable is NOT normal distribution. It means that we need transform the data. 
It seems like Johnson Distribution is good fit for the depandant variable. 

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/d2a66453-3b1c-4135-b840-be5485cbeafd)

### Numerical Feature Exploration

In order to look closer to numerical features, I use heatmap. 

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/ee333cbc-c027-4efa-b510-88197c73ac6c)

In order to reduce the sizes of heatmap, I try to plot the features that are highly correlated to the depeandant variable.
I set the threshold 0.7 and above.

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/c5405601-711b-4747-bfeb-b3c7b2c7c1a6)

I dropped few features from heatmap information:  'TotalBsmtSF', 'GrLivArea','GarageCars'

### Create new features by combining existed features

```
 #Total area of property
 df_feature['Total_SQ']   = df_train['1stFlrSF']+df_train['2ndFlrSF']+df_train['TotalBsmtSF']
 df_feature['Total_bath'] = df_train['FullBath']+df_train['HalfBath']*0.5 + df_train['BsmtFullBath'] + df_train['BsmtHalfBath']*0.5
 df_feature['Total_porch']= df_train['OpenPorchSF'] +df_train['EnclosedPorch'] + df_train['ScreenPorch'] + df_train['WoodDeckSF'] +df_train['3SsnPorch']
 
 #Amenity of property
 df_feature['Has_pool']     = df_train['PoolArea'].apply(lambda x: 1 if x > 0 else 0)
 df_feature['Has_2ndFloor'] = df_train['2ndFlrSF'].apply(lambda x: 1 if x > 0 else 0)
 df_feature['Has_garage']   = df_train['GarageArea'].apply(lambda x: 1 if x > 0 else 0)
 df_feature['Has_base']     = df_train['TotalBsmtSF'].apply(lambda x: 1 if x >0 else 0)
 df_feature['Has_fire']     = df_train['Fireplaces'].apply(lambda x: 1 if x>0 else 0)
```
### Scaleing on Numerical Features

The numerical features are not normal distribution so the scaleing and transform is requried. 
I tried two scaleing on this project: StandardScale and Box1PScale.

My experience is that StandardScale is good enough for this competition.

### Filling Missing Values

If missing values are less than 100 on each feature, I fill median of each feature to the missing values.  
If missing values are more than 100, I fill "None" or 0 for missing values depending on Categorical or Numerical features

### Combine two datasets

Before I use `pd.get_dummies` to encode the categorical features, I added two datasets in order to two datasets transform together.  
Then I seperate Train and Test dataset again.



Visualization: 

Sale Price vs Month

Sale Price vs Properties Age

Sale Price vs Properties Remodeling Age

Heatmap



