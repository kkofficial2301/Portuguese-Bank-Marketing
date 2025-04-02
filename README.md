
# Portuguese Bank Marketing
The purpose of the analysis is to how the bank runs a marketing campaign to bring customers on board with the term deposits.

## Data Analysis Report

### Data Overview
- Number of rows: 41188
- Number of columns: 21
- Featues: Age, Duration, Campaign, Pdays, Previous, Emp.var.rate, Cons.price.idx, Cons.conf.idx, Euribor3m, Nr.employed, Job, Martial, Education, Default, Housing, Loan, Contact, Month, Day_of_week, Poutcome, y(Target.)
- Target Variable : y(Bank Term Deposit Subrcription).
### Data Preprocessing and feature engineering
- Handling Missing Values : The dataset contains no missing values, ensuring data completeness and consistenc.
- Handling categorical data : For the categorical features like Job, Marital, Education, Default, Housing, Loan, Contact, Month, Day_of_week, Poutcome, and y (Target) in the Portuguese bank data, a combination of one-hot encoding and label encoding was applied based on real-world hierarchies and domain understanding. One-hot encoding was used for features without inherent order, such as Job, Martial, Contact, Month, Day_of_week, Poutcome. Meanwhile, label encoding was applied to ordinal features like Education and Default, Housing and Loan, reflecting their natural ranking to improve model interpretability and performance. And for target variable(y) manual encoding was done. This balanced approach captures both nominal and ordinal relationships effectively
- Outliers : Handling outliers was crucial for improving model accuracy, but in some cases, extreme values might represent valid customer behaviors, so after careful analysis. The data includes records of students under 18, which is unrealistic for opening a bank term deposit or obtaining loans like housing or personal loans. Therefore, removing these values is a logical step to ensure data relevance and accuracy. In the Campaign feature lot of data lies after 75th percentile so it would make no sense to those values, it is significant from the box plot above as well. So we removed the extreme value 56
- Feature Transformation: MinMax scaling was applied to the features Age, Campaign, Pdays, Emp.var.rate, Cons.price.idx, Cons.conf.idx, Euribor3m, and Nr.employed because the data was not normally distributed, making standard scaling less appropriate. By using MinMaxScaler, the features were scaled to a range of 0 to 1, preserving the original distribution of the data while normalizing the feature values. This ensures that no feature disproportionately influences the model due to diffrent scales.
### Exploratory Data Analysis (EDA)
- Age vs Subscription: Older customers and younger ones (20-30) tend to subscribe more frequently than middle-aged customers (30-40), who have lower subscription rates.
- Job vs Subscription: Job types like "admin", "blue-collar", and "technician" have higher subscription rates, while other workers have lower subscription rates.
- Duration vs Subscription: Longer call durations are positively correlated with higher subscription rates. Calls lasting over 300 seconds (5 minutes) are more likely to result in a subscription.
- Education vs Subscription: Customers with higher levels of education (tertiary) tend to subscribe more frequently than those with lower levels of education (primary).
- Previous Campaign Outcome vs Subscription: If the customer had a successful outcome in the previous campaign, they are much more likely to subscribe again.
- Default and loan vs Subscription: People without loans tend to subscribe more frequently.
- Demographic Variables: Variables like age, job, and education are strong indicators of whether a customer will subscribe. Younger, highly educated customers with professional jobs are more likely to subscribe..

## Performance Report for Flight Price Prediction Models
### Overview of Models Evaluated
After creating multiple classification models, Both RandomForest and GradientBoosting performed well in their base models, achieved overall scores as below.

#### Random Forest Classifier
Performance Metrics:
- Precision (Class 1): 0.46
- Recall (Class 1): 0.40
- Accuracy: 0.88
- F1 Score: 0.42

#### Gradient Boosting Classifier 
Performance Metrics:
- Precision (Class 1): 0.53
- Recall (Class 1): 0.44
- Accuracy: 0.88
- F1 Score: 0.48


### Model Tuning Summary
Models tuning was done on Random Forest (RF) and Gradient Boosting (GB) to improve their performance.
#### Tuning Process
- In this tuning process, RandomForest and GradientBoosting classifiers were subjected to hyperparameter tuning in an effort to improve the model's performance, particularly for the minority class (class 1). Despite tuning, the recall scores for class 1 (indicating the model's ability to correctly identify positive instances) showed little to moderate improvement in both models. For RandomForest, recall slightly increased from 40% to 43%, and for GradientBoosting, recall decreased from 53% to 37% as boosting focuses on best balance between precision, recall and overall performance
- To further improve the results, Recursive Feature Elimination (RFE) was applied to Logistic Regression, Gradient boosting where the goal was to enhance the recall for class 1. This method yielded a significant improvement, achieving a recall of 70% for class 1 in Logistic Regression although at the cost of some accuracy in the overall classification.

### Conclusion
The tuning efforts for RandomForest and GradientBoosting provided marginal improvements in recall for class 1, but they still struggled to correctly predict the minority class. By switching to Logistic Regression combined with Recursive Feature Elimination (RFE), a much better recall was achieved for class 1, improving from 58% to 70% and accuracy of 75. This suggests that RFE with Logistic Regression can be a more effective approach when the primary objective is to improve recall for the minority class, especially in imbalanced dataset.

### Technologies Used
- Python
- Jupyter Notebook: Interactive environment
- Pandas, Numpy: Data manipulation and analysis
- Scikit-Learn: Machine learning modeling
- Matplotlib, Seaborn: Data visualization
