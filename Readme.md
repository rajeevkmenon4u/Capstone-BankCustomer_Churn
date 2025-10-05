# Capstone Project : Classification  Problem
**Overview**: The objective of the project is to develop a classification model that predicts which bank customers are likely to close their accounts. Additionally, the study aims to identify and analyze the key factors contributing to customer attrition.  
### Problem 1: Understanding the Data
To gain a better understanding of the data, Analysing the data and performing EDA.
### Data Details
Input variables:

| Column            | Non-Null Count | Dtype   |
|-------------------|----------------|---------|
| id                | 165034         | int64   |
| CustomerId        | 165034         | int64   |
| Surname           | 165034         | object  |
| CreditScore       | 165034         | int64   |
| Geography         | 165034         | object  |
| Gender            | 165034         | object  |
| Age               | 165034         | float64 |
| Tenure            | 165034         | int64   |
| Balance           | 165034         | float64 |
| NumOfProducts     | 165034         | int64   |
| HasCrCard         | 165034         | float64 |
| IsActiveMember    | 165034         | float64 |
| EstimatedSalary   | 165034         | float64 |


Output variable (desired target):

| Column            | Non-Null Count | Dtype   |
|-------------------|----------------|---------|
| Exited            | 165034         | int64   |


### Exploratory Data Analysis
### Hypothesis & Observation After performing EDA

1. `CreditScore` ranges from 350 to 850. More than 75% of the customers score is 710 and less. 50% of the cusomer score is less than 660. ##### which is Normal
2. `Age` -- Average Customer base is 38 Years. 75 % of the cusotomers are 42 and less than that. Max is 92 % . it is Right skewed 
3. `Tenure` -- 50% of the customer stays for 5 Years- Mean is 5 Years. Also more than 75% of the customer has tenure of 7 years or less. Max is 10.
   Tenure is fairly evenly distributed between 1 to 9 years.
4. `EstimatedSalary` -- 50% of the customer hold a salary of 117K . Average - 112K- Max of 200K. 75% of the cusomers salary is 155K . which is right skewed.
5. `Balance` -- Max is 250K. But 50% of the customer has 0 balance.
6. `NumOfProducts` - 75% of the customers have 2 products.
7. Customers are almost evenly split between inactive and active members.
8. Majority of customers are from France (57%), followed by Spain (21%) and Germany (20%).
9. The dataset has more male customers (56.4%) than female customers (43.5%).
    
##  Target Variable Analysis - 'Exited' 
1. 78% of the data consists of customers who stayed and only 21% of the data has details of customers who has exited.
2. Data is `** Not Balanced **` 
 
##  Univariate , Bivariate  & Multivariate Analysis ( With / with our Target)
1. The dataset has more male customers (56.4%) than female customers (43.5%).
2. Younger customer stayed while older customer exixted.
3. Female Customer Exited by 27% compared to Male 15%
4. when compared to the Geography 
   - **Germany Female** - 46% exited when compared to 22% for France & Spain
   - **Germany Male** - 30 % Exited when compared to 12% and 13 % for France & spain
5. `Age` and `Balance` are positively correlated (0.06)
6. `Age` and `CreditScore` are negatively correlated 
7. Customers with 3 or more NumOfProducts exited than with 2 or less products.
8. Creditscore Range of all the geography is faily similar . Score betwen 600- 700 exited and stayed as well.
9. Customer with more credit score exited by large

## Outlier Detection Observation  
1. CreditScore, Tenure,Balance, HasCrCard, IsActiveMember , EstimatedSalary all Columns are with in the Range
2. `Age` & `NumOfProducts` Has Outliers
3. Age Range should be between 6 To 70
4. `NumOfProducts` Range should be -0.5 to 3.5
5. After Analysis it looks like age greater than 70 looks valid.
6. Customers with 4 products exited majority of them - Initial Analysis.
   - Majority of the data is of the customers with 1 & 2 products (46% & 51%) 
   - Remaining 3 % of data is distrubvuted between 3 & 4 Products.
   - 76% of the customer with 1 product Exited and that decreases when customer has 2 products ( stayed - 60%).
- **Both Outlier `Age` & `NumOfProducts` looks normal after detail analysis**


### Graphical Representation of Categorical Columns
<img width="991" height="772" alt="image" src="https://github.com/user-attachments/assets/1c0117e6-6c0e-464e-9086-3a1967b54c80" />

### Graphical Representation of Univariate , Bivariate  & Multivariate Analysis ( With / with our Target)

<img width="1076" height="405" alt="image" src="https://github.com/user-attachments/assets/d20c309f-30b3-4378-acda-d447273d50be" />
<img width="635" height="476" alt="image" src="https://github.com/user-attachments/assets/676c5d13-2a0f-428c-81ab-3b0b53b199c4" />
### HeatMap
<img width="655" height="523" alt="image" src="https://github.com/user-attachments/assets/3d662274-b8a3-458e-afa0-6a701ba49a4d" />

### Sample Logistic Regression Model
<img width="652" height="472" alt="image" src="https://github.com/user-attachments/assets/d73fba39-0041-4407-9764-e155fd99f201" />

## Observation

| Result            | Score          | 
|-------------------|----------------|
| Accuracy          | 0.83539        |
| precision_score   | 0.69623        |
| recall_score      | 0.38820        |
| f1_score          | 0.49847        |

1. Accuracy is high because of the data imbalance (most customers did not exit).
2. Model Predicted 69% correct ( Precision > Recall is conservative)
3. Model Predicted fewer - 38.8% (who actually exited)
4. Closer to recall here, showing recall is the bottleneck.

### Made data more Balanced using SMOTE & class_weight='balanced' in Logistic Regression Model
<img width="1222" height="497" alt="image" src="https://github.com/user-attachments/assets/41df7aa2-f5e9-44e8-adda-75efb5a927cc" />

## Observation - (class_weight='balanced') Better
1. Accuracy got reduced to 75% as data got balanced
2. Model Predicted 44% correct ( Not conservative)
3. Model Predicted more customer who got exited - 74% (who actually exited)
