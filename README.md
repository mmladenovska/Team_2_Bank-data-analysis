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

 <img src="https://user-images.githubusercontent.com/81990864/115435526-39eae480-a20a-11eb-9b70-81586c43b819.jpg" width="700" height="300">

Maybe there wasn’t NA’s values but we detect many columns  filled with unknown information. In order not to lose this data we decided to  make replacement of this values with 'most frequent' method. Another step  in this phase  was identifying outliers with interquartile range (IQR) in one of the features with some bouncing values and outlier treatment by replacing outliers (the extreme values) with median values(not using mean values as they are affected by outliers).
Also Machine Learning algorithms can typically only have numerical values as their independent variables so our categorical variable are dealt with Cat Boost Encoder .
