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

Maybe there wasn’t NA’s values but we detect many columns  filled with unknown information. In order not to lose this data we decided to  make replacement of this values with 'most frequent' method. By doing basic statistic we reveal some data oscillations and prior outliers detection in one of the features with some bouncing (unrealistic) values and did outlier treatment by replacing  with median values(not using mean values as they are affected by outliers). Another step  in this phase  was dealing with skew data by doing some log transformations.
Also Machine Learning algorithms can typically only have numerical values as their independent variables so our categorical variable are dealt with Cat Boost Encoder .

----
## Exploratory Data Analysis (EDA)

This analysis focuses on the behavior of bank customers who are more likely to leave the bank .We want to find out the most striking behaviors of customers through Exploratory Data Analysis and later on use some of the predictive analytics techniques to determine the customers who are most likely to churn.
First of all, we are dealing with an imbalanced classification problem(Existing Customers 84% and Attrited Customers 16%) . Machine learning algorithms work well when the number of instances of each class is roughly equal so we utilized  SMOTE technique when creating the models to create balanced classification. 

![class](https://user-images.githubusercontent.com/81990864/115439830-4c1b5180-a20f-11eb-9f7d-9ead22c3605d.jpg)

For better understanding  the patterns , we tried to explore and visualize our dataset by doing distribution of variables
![age](https://user-images.githubusercontent.com/81990864/115442389-3ce9d300-a212-11eb-8f4e-832a0d6c9ae2.jpg)

Customer age in our dataset follows a fairly normal distribution and as we can see it doesn't play a part in churning.More than 70% of the customers are in age range between 36-56 years old, so we are dealing with a clients who may start thinking of their pensions, inheritance, taxes, etc. which means they will emphasize on finding the best deal, regardless of the bank.

![dist](https://user-images.githubusercontent.com/81990864/115441345-08c1e280-a211-11eb-9b56-9329ad9af78e.png)
