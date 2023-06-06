# Store Sales - Time Series Forecasting

Use machine learning to predict grocery sales.

## Goal of the Competition

In this “getting started” competition, you’ll use time-series forecasting to forecast store sales on data from Corporación Favorita, a large Ecuadorian-based grocery retailer. 
Specifically, you'll build a model that more accurately predicts the unit sales for thousands of items sold at different Favorita stores. 
You'll practice your machine learning skills with an approachable training dataset of dates, store, and item information, promotions, and unit sales.

## Dataset Description

In this competition, you will predict sales for the thousands of product families sold at Favorita stores located in Ecuador. The training data includes dates, store and product information, whether that item was being promoted, as well as the sales numbers. Additional files include supplementary information that may be useful in building your models.

### File Descriptions and Data Field Information

#### train.csv

- The training data, comprising time series of features store_nbr, family, and onpromotion as well as the target sales.
- store_nbr identifies the store at which the products are sold.
- family identifies the type of product sold.
- sales gives the total sales for a product family at a particular store at a given date. Fractional values are possible since products can be sold in fractional units (1.5 kg of cheese, for instance, as opposed to 1 bag of chips).
- onpromotion gives the total number of items in a product family that were being promoted at a store at a given date.

#### test.csv

- The test data, having the same features as the training data. You will predict the target sales for the dates in this file.
- The dates in the test data are for the 15 days after the last date in the training data.

#### sample_submission.csv

- A sample submission file in the correct format.

#### stores.csv

- Store metadata, including city, state, type, and cluster.
- cluster is a grouping of similar stores.

#### oil.csv

- Daily oil price. Includes values during both the train and test data timeframes. (Ecuador is an oil-dependent country and it's economical health is highly vulnerable to shocks in oil prices.)

#### holidays_events.csv

- Holidays and Events, with metadata
- NOTE: Pay special attention to the transferred column. A holiday that is transferred officially falls on that calendar day, but was moved to another date by the government. A transferred day is more like a normal day than a holiday. To find the day that it was actually celebrated, look for the corresponding row where type is Transfer. For example, the holiday Independencia de Guayaquil was transferred from 2012-10-09 to 2012-10-12, which means it was celebrated on 2012-10-12. Days that are type Bridge are extra days that are added to a holiday (e.g., to extend the break across a long weekend). These are frequently made up by the type Work Day which is a day not normally scheduled for work (e.g., Saturday) that is meant to payback the Bridge.
- Additional holidays are days added a regular calendar holiday, for example, as typically happens around Christmas (making Christmas Eve a holiday).

#### Additional Notes

- Wages in the public sector are paid every two weeks on the 15 th and on the last day of the month. Supermarket sales could be affected by this.
- A magnitude 7.8 earthquake struck Ecuador on April 16, 2016. People rallied in relief efforts donating water and other first need products which greatly affected supermarket sales for several weeks after the earthquake.

## EDA 

Explore each files. Before I merge all files to one dataframe, I modified few things.

- I can find out the time the store was closed from `transaction` files. I found the timeline and deleted the times when the stores were closed.
- For date, I seperated Month, Day, and Year and saved as numerical variables.

Then I merged all files to one dataframe.

After merging to one dataframe, I check few things.

- Any missing values?
- Any duplicate values?

When precentage of missing values are more than 50%, I deleted those features. If there is any duplicated rows, I dropped the duplicated.

Then, I ask few questions to the dataframe. 

#### 1. Does the type of stores affect the store sales?

Test with ANOVA (Analysis of Variance) with p = 0.05 

- Null Hypothesis: $H_0$ = there is no effect between type of stores and the store sales  
- Althenative Hypotheis: $H_1$ = there is effect  

Anova result: p = 0 which is less than 0.05. Reject $H_0$. 

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/df37e18a-c69d-404b-9586-ab6d0fdc0447)

#### 2. Which family is having the highest sales?

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/874e37cb-c64b-4618-b80c-4c195e4d63ab)

#### 3. Is any relationship between promotion and sales?

Pearson correlation test to determine the relationship between promotion and slaes with p = 0.05. 

- Null hypothesis: $H_0$ = no relationship between promotion and sales
- Althernative hypothesis: $H1$  = there are relationships between promotion and sales

**Result**: Reject $H_0$
Pearson correlation coefficient: 0.4279232048121204 
p-value: 0.0 

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/bf78065d-140a-48d9-b087-68b791d5cd86)

#### 4. Sales distribution by cities

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/2d1a4151-9724-4696-8570-a1c54ec45905)

#### 5. Total sales by store

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/26f9e6b9-8bc0-481c-83fb-4589494cfc25)

#### 6. Monthly Sales Trend

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/f22470ef-2db9-4ec4-b298-edd000d7ba6d)

Then, I checked autocorrelation and partial autocorrelation.

![image](https://github.com/kh4vv/Data-Science-Project/assets/47800500/2a7c3633-e53d-4ef3-90b4-fe54aff080f1)

Then, I added new features (columns) for lags features, rolling mean features, and exponential moving average.

## Model

I used XGBoost to train the dataset. 


