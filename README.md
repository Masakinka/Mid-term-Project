# Mid-Term Project: Predicting Bank Term Deposit Subscriptions

## Overview

This project is focused on building a machine learning model to predict whether a client will subscribe to a term deposit at a bank. The dataset used for this project comes from direct marketing campaigns (phone calls) of a Portuguese banking institution. The goal is to create a model that can effectively classify whether a client will subscribe to a term deposit based on various features provided in the dataset.

## Dataset Source

- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/222/bank+marketing)
- **Description:** The dataset includes 41,188 records with 21 attributes. The data is related to direct marketing campaigns (phone calls) conducted by a Portuguese banking institution. The classification goal is to predict if the client will subscribe (yes/no) to a term deposit.
  
### Key Features:
- **Numerical Features:** age, duration, campaign, pdays, previous, emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed
- **Categorical Features:** job, marital, education, default, housing, loan, contact, month, day_of_week, poutcome
- **Target Variable:** y (whether the client subscribed to a term deposit)

## Exploratory Data Analysis (EDA)

A thorough Exploratory Data Analysis was conducted to understand the distribution of the data, relationships between features, and the target variable. 

### Key Insights from the EDA:
- **Class Imbalance:** The target variable is highly imbalanced, with the majority of the records labeled as 'no' for term deposit subscription.
- **Important Features:** Features such as duration, nr.employed, emp.var.rate, and poutcome_success were found to have significant importance in predicting the target variable.

## Feature Engineering

To enhance the dataset, two custom transformers were created:

- **FeatureCreationTransformer:** This transformer created additional features such as `balance_per_duration` and `contacts_total`, which were found to be significant.
- **PreprocessingTransformer:** This transformer handled rare categories and detected outliers using the Interquartile Range (IQR) method.

## Modeling

We trained several models and compared their performance:

1. **Logistic Regression**
2. **Decision Tree**
3. **k-Nearest Neighbors (kNN)**
4. **XGBoost**

### Hyperparameter Tuning

For the XGBoost model, hyperparameter tuning was performed using two methods:

- **Randomized Search:** Resulted in an F1 Score of 0.915.
- **Hyperopt:** Resulted in an F1 Score of 0.835.

### Model Performance

| **Model**               | **Train Precision** | **Train Recall** | **Train F1** | **Test Precision** | **Test Recall** | **Test F1** |
|-------------------------|---------------------|------------------|-------------|--------------------|-----------------|-------------|
| Logistic Regression      | 0.90                | 0.91             | 0.90        | 0.90               | 0.91            | 0.90        |
| Decision Tree            | 1.00                | 1.00             | 1.00        | 0.89               | 0.89            | 0.89        |
| k-Nearest Neighbors (kNN) | 0.92               | 0.93             | 0.93        | 0.89               | 0.90            | 0.89        |
| XGBoost                  | 0.96                | 0.96             | 0.96        | 0.90               | 0.91            | 0.91        |

### Feature Importance

The XGBoost model highlighted the most significant features:

- **Duration:** The length of the last contact is the most influential feature.
- **Number of Employees (nr.employed):** Reflects the economic environment.
- **Employment Variation Rate (emp.var.rate):** A measure of economic conditions.

### Error Analysis

We analyzed the records where the model made errors:

- **False Positives:** Cases where the client was predicted to subscribe but did not. These cases typically had longer contact durations.
- **False Negatives:** Cases where the client was predicted not to subscribe but did. These cases often had shorter contact durations.

## Conclusion

The XGBoost model provided the best performance, balancing precision and recall effectively. However, the model still has room for improvement, particularly in reducing false negatives. Future work could involve exploring more sophisticated feature engineering and experimenting with other boosting algorithms like LightGBM or CatBoost.

## Future Work

- **Feature Engineering:** Experiment with additional interaction terms and polynomial features.
- **Modeling:** Try other advanced algorithms like LightGBM and CatBoost.
- **Imbalance Handling:** Use techniques like SMOTE or balanced class weights to handle the class imbalance better.
