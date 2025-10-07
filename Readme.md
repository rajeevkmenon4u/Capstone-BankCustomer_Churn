# Capstone Project : Classification  Problem ( Bank Customer Churn)
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

### Baseline Dummy Model
<img width="792" height="531" alt="image" src="https://github.com/user-attachments/assets/0eefac6d-5ef9-4e9f-bae3-aa85690a6edc" />

## Observation

| Result            | Score          | 
|-------------------|----------------|
| Accuracy          | 0.789          |
| precision_score   | 0.0            |
| recall_score      | 0.0            |
| f1_score          | 0.0            |

1. Accuracy is high because of the data imbalance (most customers did not exit).
2. DummyClassifier not able to predict as it goes with the majority of the data

### Made data more Balanced using SMOTE & Strategy - 'stratified' in Dummy classifier Model
<img width="747" height="523" alt="image" src="https://github.com/user-attachments/assets/71044e99-7589-465d-bb1f-93083b19c882" />

## Observation - (Strategy - 'stratified') Better
1. Accuracy got reduced to 49% as data got balanced
2. The model started predicting both classes, but since the dataset is imbalanced, accuracy alone doesn’t mean much.

### Model Comparison [Logistic,KNN,Decision Tree,Random Forest,Gradient Boosting,AdaBoost,XGBoost]
1. As the data is not balanced we are focussing on the best AUC value the model the generate
2. `DecisionTree`, `Randon Forest` , `Gradient Boosting` & `Adboost` all have an AUC Value of `87%-88%`
3. SVM took the longest time to execute, hence it was ignored for further analysis.
4. As this is a Real work Problem `XGboost` is tried and it is has an AUV laue of `89%`

 |              Model|  Accuracy  | Precision|   Recall  | F1-score| auc_value|  Train Time |
 |-------------------|------------|----------|-----------|---------|----------|-------------|
 | LogisticRegression|  0.835399  | 0.696235 | 0.388210  |0.498477 |  0.818049|    0.305593 |
 |                KNN|  0.847517  | 0.673591 | 0.536161  |0.597070 |  0.829963|   20.130846 |
 |      Decision Tree|  0.858121  | 0.728021 | 0.521495  |0.607690 |  0.873008|    0.357273 |
 |                SVM|  0.862100  | 0.738143 | 0.523515  |0.607690 |  0.000000| 1064.110000 |
 |      Random Forest|  0.850183  | 0.803625 | 0.382459  |0.518266 |  0.880979|    8.907527 |
 |  Gradient Boosting|  0.866271  | 0.751435 | 0.545938  |0.632412 |  0.889899|   24.185884 |
 |           AdaBoost|  0.860878  | 0.740387 | 0.523221  |0.613142 |  0.878964|    9.335133 |
 |      XGBClassifier|  0.868058  | 0.747902 | 0.563911  |0.643004 |  0.891581|    5.106956 |


<p align="center">
  <b>Models with Confusion Matrix & ROC graph for classifier’s performance</b></br>
  <b>DecisionTree, Randon Forest , Gradient Boosting & Adboost all have an AUC Vaue of 87%-88%</b></br>
  <b>Neural Network model was tried as well and results was similar to other models </b></br>
  <b>XGboost the best among all the models and stand out with an value of 89%</b>
</p>

![Logistic-Knn](https://github.com/user-attachments/assets/30e9a5ed-1f03-4df0-a09b-b240e318379a)
![Decision-Random](https://github.com/user-attachments/assets/99f1dea9-2425-4dfe-b6c9-74a3f7649513)
![Gradient-Adaboost](https://github.com/user-attachments/assets/521aa21c-9046-4da3-816e-b44793c72932)

![XGBC](https://github.com/user-attachments/assets/86e443e3-c49e-4672-96f6-2283c5ecfd65)

### Hyperparameter Tuning for XGBC classifier
1. The model was able to predict more True Positives & True Negatives
2. As the True Negatives is also increasing the model is trading precision for recall
3. As Recall improves (miss fewer actual churners) which is good but on the flip slide we would be targeting people wouldnt leave.
4. So further Analyis to see the business Impact with some assumptions.
   
<img width="558" height="796" alt="image" src="https://github.com/user-attachments/assets/6c257483-b081-439b-834f-13fe76cad02b" />

### Business Impact $$$ Value for each model - Analysis
1. Revenue per customer - $100 -- Revenue
2. Marketing Expense ( Retention Cost) -$5 -- Cost
3. Percentage of Customer will Stay based on the Marketing - (5%) --- Percentage
4. Based on the above assumptions Impact on the model would be

| Description       | Impact          | 
|-------------------|-----------------|
| TP - Gain         | (0.5* 100) -10  |
| TN - No impact    | 0.0             |
| FP - Loss         | $5 -PerCustomer |
| FN - Loss         | $100-PerCustomer|
 
### Conclusion - Business Impact $$$ Value for each model 

| Model             |  Rentention%    | Profit-Margin  | 
|-------------------|-----------------|----------------|
|Logistic Regression|         0.5     | -309890.0      | 
|Random Forest      |         0.5     | -313050.0      | 
|Gradient Boosting  |         0.5     | -168215.0      | 
|XGBoost            |         0.5     | -133420.0      |
|XGBoost-hyperparam |         0.5     | -74100.0       | 

1. In all the Models Based on the assumption the business is making loss.
2. But the loss is getting reduced considerably.  
3. It clear indicates that The impact of the business is only $74K when compared to in XGBoost which is $133K.
4. **The best Model is XGBoost after hyper parameter Tuning.**
    
