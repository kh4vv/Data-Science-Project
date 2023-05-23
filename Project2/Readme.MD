# Chicago House Price and Prediction

### Given dataset which contains information about houses prices in the suburbs of chicago

## TASK

First analysis the data ,and then to apply a regression model to it.

## Data Source

Data from [Kaggle](https://www.kaggle.com/datasets/tawfikelmetwally/chicago-house-price) 

## Data Overview

dataset consists of following variables:

**Price :** price of house  
**Bedroom:** number of bedrooms  
**Room:** number of rooms  
**Space :** size of house (in square feet)  
**Lot :** width of a lot  
**Tax :** amount of annual tax  
**Bathroom :** number of bathrooms  
**Garage :** number of garage  
**Condition:** condition of house (1 if good , 0 otherwise)  

## EDA

1. Check *null* or missing data  

Space and Lot have the most missing values about 7%. I decided to drop it.

2. Check duplicate data

There is none.

3. Check outliers

Box plot to check outliers for each features.  
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/b4a3db84-d8ac-48ed-94be-c6d4a68c835b)  

I do not find major outliers after checking each features.

4. Check corrleation with dependet variable

Pairplot to check correlations among features.
![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/f3c453bc-2fc3-4ad0-91a0-e894bd6c5dc5)

5. Check dependant variable.

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/53160cbd-ab77-4005-a474-2178cfde2f33)

## Build Model

For modeling, I used:  **Linear Reg , Decision Tree, Random Forest, XGB Reg**

## Result

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/7efa0119-0a47-4c5b-963d-be20620caac3)

Random forest has the smallest MSE. 

## Evaluation and Visualization

1. Predict Price vs True Price

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/d9ab8602-66ea-400e-a336-f196a930ed4d)

2. Histogram of Residual

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/f1c3596f-3027-4aa7-b41e-644009e189ce)

3. Feature Importance Plot

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/24a37ffc-4e13-4b34-be09-69bc62314d31)


4. Price vs Space (the most important feature)

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/f13a2a38-5054-4c32-a6ed-898b2a100b8c)


  
