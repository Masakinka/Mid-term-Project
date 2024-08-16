Mid-term Project: Predicting Bank Term Deposit Subscriptions
Overview
This project is focused on building a machine learning model to predict whether a client will subscribe to a term deposit at a bank. The dataset used for this project comes from direct marketing campaigns (phone calls) of a Portuguese banking institution. The goal is to create a model that can effectively classify whether a client will subscribe to a term deposit based on various features provided in the dataset.

Dataset
Source: UCI Machine Learning Repository
File: bank-additional-full.csv
Description: The dataset includes 41,188 records with 21 attributes. The data is related to direct marketing campaigns (phone calls) conducted by a Portuguese banking institution. The classification goal is to predict if the client will subscribe (yes/no) to a term deposit.
Key Features:
Numerical Features: age, duration, campaign, pdays, previous, emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed
Categorical Features: job, marital, education, default, housing, loan, contact, month, day_of_week, poutcome
Target Variable: y (whether the client subscribed to a term deposit)
Exploratory Data Analysis (EDA)
A thorough Exploratory Data Analysis was conducted to understand the distribution of the data, relationships between features, and the target variable. Key insights from the EDA include:

Class Imbalance: The target variable is highly imbalanced with a majority of the records labeled as 'no' for term deposit subscription.
Important Features: Features such as duration, nr.employed, emp.var.rate, and poutcome_success were found to have significant importance in predicting the target variable.
Modeling
Four machine learning models were developed and evaluated:

Logistic Regression
Decision Tree
k-Nearest Neighbors (kNN)
XGBoost (Extreme Gradient Boosting)
Model Performance
The models were evaluated using metrics such as Precision, Recall, F1-Score, and Confusion Matrix. XGBoost outperformed the other models in terms of accuracy and generalization to the test set.

Hyperparameter Tuning
Hyperparameter tuning was performed using two methods:

Randomized Search (Sklearn)
Bayesian Optimization (Hyperopt)
The tuned XGBoost model with Randomized Search achieved the highest F1-Score.

Results
Best Model: XGBoost with hyperparameters tuned via Randomized Search
F1-Score: 0.9153 (on test data)
Key Features: duration, nr.employed, emp.var.rate, poutcome_success, and previous
Conclusion
The project successfully built a predictive model for bank term deposit subscriptions using machine learning. XGBoost was the most effective model, especially after hyperparameter tuning. The analysis also highlighted the importance of certain features like duration of the last contact, which strongly influences the client's decision.

Future Work
Handling Class Imbalance: Explore advanced techniques for handling class imbalance.
Feature Engineering: Investigate additional feature engineering techniques to improve model performance.
Model Deployment: Consider deploying the model using a framework like Flask or FastAPI.
Repository Structure
Mid_term_Project.ipynb: Jupyter notebook containing all the code, analysis, and results.
README.md: Overview of the project and key findings (this file).
Getting Started
To replicate this project:

Clone this repository:
bash
Copy code
git clone https://github.com/yourusername/Mid-term-Project.git
Open the Mid_term_Project.ipynb in Jupyter Notebook or Google Colab.
Run the cells to reproduce the analysis.
