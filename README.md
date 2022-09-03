# MarketingOffer
Binary classification of whether a customer responded to a marketing campaign offer

### Context

iFood is a Brazilian online food ordering and food delivery platform, operating in Brazil and Colombia. The company holds over 80% market share of the food delivery sector in Brazil. This case assignment/dataset is used for hiring Data Analysts for the iFood Brain team, I decided to have a crack at it for fun.

### Task

The objective of the team is to build a predictive model that will predict whether a customer will respond to a marketing campaign. This is a supervised dataset with response labels for 2240 customer records.

### Data

![Screenshot 2022-09-03 at 17 25 48](https://user-images.githubusercontent.com/56136026/188279679-5b4c11c6-09b5-4479-8afe-fe1310ee84d0.png)

### Data Cleaning and Preparation 

Marital Status: Fixing repetitive values (e.g. single and alone)

Income: Converting from string to float, imputing missing values based on educational mean, and dealing with outliers

Dt_Customer: Converting to datetime

Year Birth: Fixing incorrect values (DOB<1900)

Other: Dropping 4 incorrect entries

### Feature Engineering

Purchase Variables: Total spend, total number of orders, average order value, log transformations of spend variables (all were heavily skewed)

Proportion Variables: Proportion of spend by category, proportion of gold product spend to total

Household Variables: # of kids, total # of people in the household, income divided by # in household

Date/Time Variables: Average time between orders, customer tenure, age, spend to tenure ratio

Categorical Variables: Target encoding 

### Feature Selection

Recursive Feature Elimination, Cross-Validated (RFECV) feature selection. 

RFE works by searching for a subset of features by starting with all features in the training dataset and successfully removing features until the desired number remains. Logistic Regression was used as a base estimator.

![Screenshot 2022-09-03 at 17 22 46](https://user-images.githubusercontent.com/56136026/188279701-1839b572-9d8c-4c9d-b138-746ba0d86c67.png)

![Screenshot 2022-09-03 at 17 47 29](https://user-images.githubusercontent.com/56136026/188280426-0f47b851-2ee3-459a-9b17-4acd8f878a58.png)

### Modelling 

![Screenshot 2022-09-03 at 17 21 51](https://user-images.githubusercontent.com/56136026/188279743-bf41f08d-0159-4497-be95-32d601f53f21.png)

As seen above, the two classes are heavily imbalanced and could cause algorithms to be biased.

Synthetic Minority Oversampling Technique (SMOTE) is a statistical technique for increasing the number of cases in your dataset in a balanced way. The component works by generating new instances from existing minority cases that you supply as input.

The models used were:
- Logitic Regression
- Xgboost
- Adaboost
- Random Forest
- Catboost


![Screenshot 2022-09-03 at 17 22 00](https://user-images.githubusercontent.com/56136026/188279754-1546f9cd-2a57-40e9-b6dd-87d79f04ec40.png)



### Final Results

ROC (Receiver Operating Characteristics) is a probability curve and AUC (Area Under Curve) represents the degree or measure of separability.

It tells how much the model is capable of distinguishing between classes.

The higher the AUC, the better the model is at predicting 0 classes as 0 and 1 classes as 1

Best performing model: Random forest

![Screenshot 2022-09-03 at 17 22 19](https://user-images.githubusercontent.com/56136026/188279730-4fce8695-c3ed-4026-8e07-8d1bfd0c7a98.png)




