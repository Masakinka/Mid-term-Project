Mid-Term Project: Predicting Term Deposits Subscription
Overview
This project aims to predict whether a client will subscribe to a term deposit based on data from a bank's direct marketing campaigns. The data was collected from a Portuguese bank and contains various client attributes and their responses to previous marketing efforts.

Exploratory Data Analysis (EDA)
We performed an in-depth exploratory data analysis to understand the distribution of the target variable and the features. Key insights include:

Class Imbalance: The dataset is highly imbalanced, with the majority class being clients who did not subscribe to a term deposit.
Important Features: Duration of the last contact, employment variables, and previous marketing outcomes are some of the most influential factors.
Feature Engineering
Two custom transformers were created to enhance the dataset:

FeatureCreationTransformer: This transformer created additional features such as balance_per_duration and contacts_total, which were found to be significant.
PreprocessingTransformer: This transformer handled rare categories and detected outliers using the Interquartile Range (IQR) method.
Modeling
We trained several models and compared their performance:

Logistic Regression
Decision Tree
k-Nearest Neighbors (kNN)
XGBoost
Hyperparameter Tuning
For the XGBoost model, we performed hyperparameter tuning using two methods:

Randomized Search: Resulted in an F1 Score of 0.915.
Hyperopt: Resulted in an F1 Score of 0.835.
Model Performance
Model	Train Precision	Train Recall	Train F1	Test Precision	Test Recall	Test F1
Logistic Regression	0.90	0.91	0.90	0.90	0.91	0.90
Decision Tree	1.00	1.00	1.00	0.89	0.89	0.89
kNN	0.92	0.93	0.93	0.89	0.90	0.89
XGBoost	0.96	0.96	0.96	0.90	0.91	0.91
Feature Importance
The XGBoost model highlighted the most significant features:

Duration: The length of the last contact is the most influential feature.
Number of Employees (nr.employed): Reflects the economic environment.
Employment Variation Rate (emp.var.rate): A measure of economic conditions.

Error Analysis
We analyzed the records where the model made errors:

False Positives: Cases where the client was predicted to subscribe but did not. These cases typically had longer contact durations.
False Negatives: Cases where the client was predicted not to subscribe but did. These cases often had shorter contact durations.

Conclusion
The XGBoost model provided the best performance, balancing precision and recall effectively. However, the model still has room for improvement, particularly in reducing false negatives. Future work could involve exploring more sophisticated feature engineering and experimenting with other boosting algorithms like LightGBM or CatBoost.

Future Work
Feature Engineering: Experiment with additional interaction terms and polynomial features.
Modeling: Try other advanced algorithms like LightGBM and CatBoost.
Imbalance Handling: Use techniques like SMOTE or balanced class weights to handle the class imbalance better.
