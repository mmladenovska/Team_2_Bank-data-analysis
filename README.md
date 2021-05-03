# Bank data analysis-Prediction if a bank’s customer will stay or leave the bank
----
## Introduction
Customer attrition is one of the biggest challenges of any organization, in our case it is Bank Customer attrition. Bank's are well informed that the cost of acquiring new customers is 7 times higher than retaining existing ones, which means losing customers can be very financially detrimental. Through the Bank dataset, we are going to analyze and figure out why a customer leaves and when they leave with reasonable accuracy, so it would help the Bank to make appropriate strategy.

The goal of our project is to create a robust classifier and use the data, so we build a model that will recognize whether specific client will leave/unsubscribe the bank services. The project is made up of few phases:
  * Data Loading and Preprocessing
  * Exploratory Data Analysis (EDA)
  * Build Predictive Models and evaluations
  * Conclusion
----
## Data Loading and Preprocessing
The dataset contains 10127 rows and 21 columns with no missing values in the dataset. We need to take care of missing values before we compare and select a model.

 <img src="https://user-images.githubusercontent.com/81990864/115435526-39eae480-a20a-11eb-9b70-81586c43b819.jpg" width="700" height="300">

Maybe there wasn’t NA’s values but we detect many columns filled with "unknown" information. In order to avoid losing this data, we decided to make replacement of the unknown values with 'most frequent' method. By doing basic statistics we reveal some data oscillations and prior outliers detection in one of the features with some bouncing (unrealistic) values/ Also we did an outlier treatment by replacing  with median values (not using mean values as they are affected by outliers). Another step in this phase was dealing with skew data by doing some log transformations.
Also Machine Learning algorithms can typically only have numerical values as their independent variables, so in order to adopt our categorical variables we are using Cat Boost Encoder.

----
## Exploratory Data Analysis (EDA)

This analysis focuses on the behavior of bank customers who are more likely to leave the bank. 
We want to find out the most striking behaviors of customers through Exploratory Data Analysis and later on use some of the predictive analytics techniques to determine the customers who are most likely to churn.
First of all, we are dealing with an imbalanced classification problem (Existing Customers 84% and Attrited Customers 16%). 
Machine learning algorithms work well when the number of instances of each class is roughly equal so we utilized SMOTE technique when creating the models with balanced classification. 

![class](https://user-images.githubusercontent.com/81990864/115951104-3348bf80-a4df-11eb-943c-7bd78c3200b3.jpg)


For better understanding  the patterns, we tried to explore and visualize our dataset by doing distribution of variables:
 <img src="https://user-images.githubusercontent.com/81990864/115442389-3ce9d300-a212-11eb-8f4e-832a0d6c9ae2.jpg" align="center" width="700" height="400">

The distribution of customer age is similar between churned and not-churned customers. We can conclude that customer age does not seem to be an important factor in customer churn.More than 70% of the customers are in age range between 36-56 years old, so we are dealing with customers which may start thinking of their pensions, inheritance, taxes, etc., meaning they will emphasize on finding the best deal, regardless of the bank.

We used boxplots to check the distribution of variables and separate them based on attribution flag.

Based on the obtained, we saw significant differences in some of the variables, such as total transaction count and total transactions amount.The attrition class has a lower total transaction count and total transactions amount compared to the existing customers class, as expected. The bank can make further efforts to encourage customers to increase transactions amount and number of transactions.

![numericboxctam](https://user-images.githubusercontent.com/81990864/115952355-ba009b00-a4e5-11eb-9ca0-bcc8d7dddab4.jpg)

Some significant differences between the classe could be noticed in the variables such as total Revolving Balance and Avg Utilization Ratio. In credit card terms, a revolving balance is the portion of credit card spending that goes unpaid at the end of a billing cycle.Credit utilization ratio is how much you owe on all your revolving accounts, such as credit cards, compared with your total available credit — expressed as a percentage. It's important because it's one of the biggest factors in your credit score.Experts suggest using no more than 30% of your limits, and less is better. Charging too much on your cards, especially if you max them out, is associated with being a higher credit risk. Its clear that this feature distribution is lower for Churned customer when compared to the Exisiting customers. Churning customers most of them have lower Revolving Balance and  Avg Utilization Ratio under 30%, so mabye over-indebted isn't the reason for leaving.

![numericboxblavg](https://user-images.githubusercontent.com/81990864/115952659-94749100-a4e7-11eb-921d-1f12fa67935b.jpg)

Additional findings are that the bank has contacted the churning customers more frequently than the no churn cusotmers.
Also attrition class has a higher proportion of customers which were more inactive in the last 12 months. There is a relation between the number of inactive months and customer churn. Тhe churn rate increases as the number of inactive months increases (excluding the categories with very few customers).
Total_Relationship_Count (Total no. of products held by the customer) also shows that customers that holds more products from the same bank, usually stay with the bank while the customers that are holding fewer products, churn.

![catogW](https://user-images.githubusercontent.com/81990864/115953604-c3413600-a4ec-11eb-8686-93e1b6b82974.png)

----

## Build Predictive Models and Evaluations

In this phase we performed few steps :
* We generated training and test datasets by dividing dataset into training and test set with an 70%-30% ratio. As mentioned earlier, we also used SMOTE to handle issues with the imbalanced data. The new samples should be generated only in the training set to ensure our model generalizes well to unseen data.

![smote](https://user-images.githubusercontent.com/81990864/115955296-f0461680-a4f5-11eb-9cb9-e3fec4d0f2b3.jpg)

* We tested six different machine learning models to predict customer churn:
  - [X] DecisionTree
  - [X] RandomForest
  - [X] KNN
  - [X] Gaussian
  - [X] Support Vector Machine
  - [X] XGBoost
 
*  After predicting the probabilities, we calculated metric scores, plot confusion matrix for each classifer and plot the ROC Curve to choose the best classifer.

| Classifier | Accuracy_score | Precision_score | Recall_score | F1_score | Mean_score |
|------------|----------------|-----------------|--------------|----------|------------|
| DecisionTreeClassifier| 	0.951300|	0.809237|	0.883772|	0.844864	|0.872293|
| SVM| 0.905890|		0.666667|	0.745614|	0.703934	|0.755526 |
| RandomForestClassifier| 0.975979 |	0.915401|			0.925439| 0.920393	| 0.934303|
| KNeighborsClassifier|0.839750|		0.479250 |	0.785088 |		0.595179 |	0.674817|
| GaussianNB| 0.879895 |	0.575707	 |0.758772|	0.654683|	0.717264 |
| XGBClassifier| 0.977295	|0.917927	| 0.932018 |	0.924918	|	0.938039 |

![roc](https://user-images.githubusercontent.com/81990864/115448357-ec767380-a219-11eb-95f5-ca3c39ff60a6.jpg)

For the best performing classifer ( in this case XGB Classifier) we did Hyperparameter tunning by using  RandomizedSearch and Manual Search. There was a slight improvement so we saved the best performing classifer for further prediction .

| Classifier | Accuracy_score | Precision_score | Recall_score | F1_score | Mean_score |
|------------|----------------|-----------------|--------------|----------|------------|
| XGBClassifier_Manual_Tuning| 0.980586 |	0.932462 |	0.938596 |	0.935519	| 0.946791 |

----
## Conclusion

It is equally important not only to have an accurate, but also an interpretable model. Apart from building a model that can successfully predict which customers are prone to churn, it is very useful to identify which variables are important that could help us in early detection and even in improving service. As we said before, it is much cost-effective to retain existing clients than to acquire new ones.
However, it is not easy to detect a customers's dissatisfaction, so they often stop using  bank’s services without any previous warning. 
Some of the benefits of using machine learning for customer churn prevention are identify company problems and fix them, also increase revenue and reduce the loss of revenue from customer churn. Early detection and forecasting customer behavior can help to make real time response and prevent churning. 

