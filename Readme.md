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

<img width="1106" height="721" alt="image" src="https://github.com/user-attachments/assets/63c9925c-2e1d-4a1e-b323-bca1ada29a7e" />
<img width="1378" height="680" alt="image" src="https://github.com/user-attachments/assets/174b25e9-43a0-439d-9c8e-048747486205" />
<img width="927" height="542" alt="image" src="https://github.com/user-attachments/assets/3ce02c40-77be-407d-b503-66d6a2106958" />

  
##  Target Variable Analysis - 'Exited' 
1. 78% of the data consists of customers who stayed and only 21% of the data has details of customers who has exited.
2. Data is `** Not Balanced **`

<img width="1122" height="547" alt="image" src="https://github.com/user-attachments/assets/3d708f6d-9597-4fe4-b1aa-e53565e862f2" />


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

<img width="1375" height="485" alt="image" src="https://github.com/user-attachments/assets/edc3e378-b540-4073-b11a-8faebc1ef263" />
<img width="953" height="541" alt="image" src="https://github.com/user-attachments/assets/9618ee94-5b97-49e9-8db6-c9ea355ec26b" />
<img width="712" height="512" alt="image" src="https://github.com/user-attachments/assets/1928ae23-6f80-47bf-97e8-b620df5c9402" />
<img width="733" height="517" alt="image" src="https://github.com/user-attachments/assets/3e3f3442-5fe2-4d45-9af7-d4d0b485cad6" />
<img width="1382" height="456" alt="image" src="https://github.com/user-attachments/assets/b6f1cc4e-99a7-41ec-a1e9-69ec1a4d380d" />
<img width="1368" height="457" alt="image" src="https://github.com/user-attachments/assets/173d2ba7-2161-4a7a-ad99-7b06698d8ed1" />
<img width="1383" height="452" alt="image" src="https://github.com/user-attachments/assets/dcde7ed2-1c01-40ae-bb9b-47f20f65d4db" />
<img width="820" height="532" alt="image" src="https://github.com/user-attachments/assets/8fc07c4d-7919-4e51-b70b-60bcb4d71d28" />
<img width="722" height="546" alt="image" src="https://github.com/user-attachments/assets/59f5dd84-599b-4ae5-863e-023494fcb65d" />
<img width="925" height="688" alt="image" src="https://github.com/user-attachments/assets/8708e9a0-1bbb-4f59-9aed-500d4f963516" />



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

<img width="698" height="530" alt="image" src="https://github.com/user-attachments/assets/ac6d25af-b357-4cc3-a1f6-5dee324be4ec" />
<img width="743" height="508" alt="image" src="https://github.com/user-attachments/assets/cb5b9af4-1913-41b2-8b0f-e4492e64154c" />
<img width="1188" height="483" alt="image" src="https://github.com/user-attachments/assets/fda9c539-7ac8-4104-a32a-b40ddb255ce9" />

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
