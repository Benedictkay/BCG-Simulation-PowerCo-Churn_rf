# Predicting Customer Churn for PowerCo Using Machine Learning
## Project Overview
--- 
This project focuses on analyzing customer churn for PowerCo, a major energy provider. The objective is to test whether customer churn is driven by price sensitivity, identify other key churn drivers, and build a predictive machine learning model to estimate- churn probabilities.
The work follows the complete BCG Data Science workflow from data understanding and EDA to feature engineering, model training, evaluation, and insights.
## Business Problem
---
PowerCo is concerned about rising churn among its SME energy customers. Leadership believes that price sensitivity may be a primary driver, but a comprehensive data-driven assessment is required.
The key business questions are:
1.	What factors drive customer churn most strongly?
2.	To what extent do price changes influence churn?
3.	Can we accurately predict which customers are likely to churn?
4.	How can PowerCo reduce churn and improve retention?
## Data Sources
---
The following datasets were provided:
### 1.	Customer Data
o	Industry
o	Tenure
o	Subscribed power
o	Historical consumption
o	Contract type
o	Sales channel
o	Churn indicator
### 2.	Historical Price Data
o	Peak, mid-peak, off-peak prices
o	Monthly price schedules
### 3.	Final Consolidated Dataset
o	data_for_predictions.csv (post-feature-engineering dataset)
### EXPLOLATORY DATA ANALYSIS
--- 
•	The visualization provided shows how many companies churned vs. how many companies did not churn. We can see from this that the churn rate is approximately 10%. This is actually a very good churn rate – the closer the rate is to 0%, the better.
•	The next series of visualizations were created in an attempt to dive deeper into how churn changes based on other factors (using other columns). This is useful for us to investigate because it may help us to understand factors that drive churn.
•	In the notebook we visualize churn vs. sales channel, contract type, number of products, number of years and origin/contract offer.
For example:
•	We see that for sales channel; there are some sales channels that yield customers churning but there are also other sales channels that have no customers churning.
•	For contract type, we see quite an even split for customers churning. This is interesting because this may suggest that contract type is not a driving factor towards churn rate.
We look at the distribution of consumption, subscribed power and forecast in the notebook. 
For example:
•	We notice that the distribution of consumption is very skewed, this is called a positive skew since it is biased towards lower values on the x axis.
•	This is interesting because you may decide to transform this column to reduce the skewness later on during feature engineering. In addition, you may want to check for outliers in this column.
•	To investigate outliers, we use a boxplot. From the boxplot we can see that with the column as it is there are definitely some outliers. Once again, this is interesting because we may choose to remove some of these outliers later.
### FEATURE ENGINEERING
Here is some context around the additional features that have been engineered. First, we have the average price changes across periods. This is a measure of the average price change by company between peak, mid-peak and off-peak periods. 
•	We then take this idea one step further by creating another similar feature but instead of looking at the average price difference, we look at the maximum price difference across periods and months. This gives another way to look at the price changes across months.
•	The reason why these 2 features could be useful is because they are another way of representing the variance of prices throughout the year. Imagine, if your utilities bill massively increased over winter, as a consumer you’d be annoyed and want to find a better deal!
•	After this we continue feature engineering with some more concepts, including transformation of columns.
•	To make predictions with a statistical or machine learning algorithm, all of the data must be converted to numeric data types.
•	Therefore, we convert date into months and remove the raw date column, as we cannot use it in its original form.
•	We also convert Boolean columns into binary values.
•	And we convert categorical columns into dummy variables. A dummy variable is a binary flag that indicates when a row matches the value from the categorical column that it was created from.
As we saw during exploratory data analysis, the distribution of some columns was skewed. This is important to identify because when modeling data for prediction, based on the technique or algorithm that we use, there are sometimes assumptions within the data that we should follow.
•	One common assumption is that the columns within the data are normally distributed. Hence, if we find that columns are not normally distributed, we should treat these columns to try and transform them into a distribution that is more normal.
Therefore, the next thing we do is transform some columns to have a closer to normal distribution. We do this using the logarithm function. As you can see from the visualizations, the newly transformed columns are much closer to a normal distribution than they were earlier.
Finally, we plot correlations of all the columns to see if we can identify any columns to remove. Columns that have very high correlations indicate an area to look out for. In this case, you may want to remove one of the columns, since they are likely both holding very similar information.
### MODEL EVALUATION
A few notes on model evaluation:
•	It was left for you to decide how to evaluate the performance of the model. In general, you want to use metrics that reflect honestly how well the model has performed.
•	In the example notebook we use 3 metrics, accuracy, precision and recall.
•	The reason why we are using these three metrics is because a simple accuracy measure (what percentage was predicted correctly) is not always a good measure to use when there isn't an equal split between categories (e.g., churn is the category we care most about but is only 10% of the data).
•	After calculating the 3 metrics, we can see that we’re able to accurately identify clients that do not churn, but not so accurately identify clients that will churn. Our model is predicting a high percentage of clients to not churn, when in fact they did!
•	This suggests that more work needs to be done on feature engineering and model tuning to reduce the number of false negatives in our predictions.

Finally, we produce a feature importance chart to visualize which features were indeed useful within the model and which ones weren’t.
•	We can see that net margin and consumption over 12 months were important predictors of churn.
•	However, the price sensitivity features are scattered around and do not shine through as a main driver for churn in their current form.
NEXT STEPS
1.	Hyperparameter tuning (GridSearchCV)
2.	Try alternative models (XGBoost, Logistic Regression, Gradient Boosting)
3.	Add behavioral/logging data
4.	Expand price elasticity calculations
5.	Build a churn dashboard for business users

