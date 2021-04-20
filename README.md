# Bank data analysis-Prediction if a bank’s customer will stay or leave the bank
----
## Introduction
Customer attrition is one of the biggest challenges of any organization, in our case it is Bank Customer attrition. Banks knowy that the cost of acquiring new customers is 7 times higher than retaining existing ones, which means losing customers can be very financially detrimental.Throw the Bank dataset we are going to analyze and figure out why a customer leaves and when they leave with reasonable accuracy, so it would help the Bank to make appropriate strategy.

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


For better understanding  the patterns , we tried to explore and visualize our dataset by doing distribution of variables
 <img src="https://user-images.githubusercontent.com/81990864/115442389-3ce9d300-a212-11eb-8f4e-832a0d6c9ae2.jpg" align="center" width="700" height="400">

Customer age in our dataset follows a fairly normal distribution and as we can see it doesn't play a part in churning.More than 70% of the customers are in age range between 36-56 years old, so we are dealing with a clients who may start thinking of their pensions, inheritance, taxes, etc. which means they will emphasize on finding the best deal, regardless of the bank.

![numeric](https://user-images.githubusercontent.com/81990864/115446197-2003ce80-a217-11eb-9a7f-af4f50482b60.jpg)

The attrition class has a lower total transaction count, total count change, total revolving balance, average utilization ratio and total transactions amount compared to the existing customers class, as expected.The bank can make further efforts  to  encourage customers  to increase  transactions amount and  number of transactions .

![categoric](https://user-images.githubusercontent.com/81990864/115446953-33fc0000-a218-11eb-82d8-48537cc1b303.jpg)

Attrition class has a higher proportion of  customers who  were more inactive in the last 12 months . Also customers who hold more products from the same bank stay with the bank while the customers holding fewer products churn

----

## Build Predictive Models and Evaluations
In this phase we performed few steps :
* We generated training and test datasets by dividing dataset into training and test set with an 70%-30% ratio. As mentioned earlier, we also used SMOTE to handle issues with the imbalanced data . The new samples should be generated only in the training set to ensure our model generalizes well to unseen data.
* We tested six different machine learning models to predict customer churn, including, Decision Tree, Random Forest, GaussianNB, K-Nearest Neighbor, Support Vector Machine and XGBoost.
*  After predicting the probabilities, we calculated metric scores , plot confusion matrix  for each classifer and plot the ROC Curve to choose the best classifer.

![compartion](https://user-images.githubusercontent.com/81990864/115448344-e7192900-a219-11eb-8c73-ba89cec54d1b.jpg)

![roc](https://user-images.githubusercontent.com/81990864/115448357-ec767380-a219-11eb-95f5-ca3c39ff60a6.jpg)

For the best performing classifer ( in this case XGB Classifier) we did Hyperparameter  tunning by using  Grid Search, RandomizedSearch  and Manual Search. There was  slight improvement 

----
## Conclusion

It is equally important to not only have an accurate, but also an interpretable model. Oftentimes, apart from wanting to have a model that is successfully predicting which customers are prone to churn, it is very  nice to identifying which variables are important can help us in early detection and maybe even improving the service. As we said before ,it is much cheaper to retain existing clients than to acquire new ones.
However, it is not easy to detect a client's dissatisfaction, and they often stop using  bank’s  services without any previous warning. Some of the many benefits of using machine learning for customer churn prevention are identify company problems and fix them, also increase revenue and reduce the loss of revenue from customer churn. Early detection and forecasting customer behavior can help to make real time response to prevent churning. 

