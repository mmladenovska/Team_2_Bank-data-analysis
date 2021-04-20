# Bank data analysis-Prediction if a bank’s customer will stay or leave the bank
----
## Introduction
Customer attrition is one of the biggest challenges of any organization, in our case it is Bank Customer attrition. Throw the Bank dataset we are going to analyze and figure out why a customer leaves and when they leave with reasonable accuracy, so it would help the Bank to make appropriate strategy.
The goal of our project is to create a robust classifier and use the data, where we will build a model that will recognize whether specific client will leave/unsubscribe the bank services. The project is made up of few phases:
  * Data Loading and Preprocessing
  * Exploratory Data Analysis (EDA)
  * Build Predictive Models and evaluations
  * Conclusion
----
## Data Loading and Preprocessing
The dataset contains 10127 rows and 21 columns and there seems to be no missing values in the dataset. We need to take care of missing values before we compare and select a model.

 <img src="https://user-images.githubusercontent.com/81990864/115435526-39eae480-a20a-11eb-9b70-81586c43b819.jpg" width="700" height="250">

Maybe there wasn’t NA’s values but we detect many columns  filled with unknown information. In order not to lose this data we decided to  make replacement of this values with 'most frequent' method. By doing basic statistic we reveal some data oscillations and prior outliers detection in one of the features with some bouncing (unrealistic) values and outlier treatment by replacing  with median values(not using mean values as they are affected by outliers). Another step  in this phase  was dealing with skew data by doing some log transformations.Also Machine Learning algorithms can typically only have numerical values as their independent variables so our categorical variable are dealt with Cat Boost Encoder .

----
## Exploratory Data Analysis (EDA)

This analysis focuses on the behavior of bank customers who are more likely to leave the bank .We want to find out the most striking behaviors of customers through Exploratory Data Analysis and later on use some of the predictive analytics techniques to determine the customers who are most likely to churn.
