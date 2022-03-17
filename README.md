## mZIrqnwEKrQGYbbr

# TermDepositSubscription

## Project Overview:
The goal of this project is to build a model for predicting if a customer will bu a investment product or not. To solve this problem the data consists of multiple feature providing information about different customers. The metrics used are 

i.  age : age of customer (numeric)

ii. job : type of job (categorical)

iii. marital : marital status (categorical)

iv. education (categorical)

v. default: has credit in default? (binary)

vi. balance: average yearly balance, in euros (numeric)

vii. housing: has a housing loan? (binary)

viii. loan: has personal loan? (binary)

ix. contact: contact communication type (categorical)

x. day: last contact day of the month (numeric)

xi. month: last contact month of year (categorical)

xii. duration: last contact duration, in seconds (numeric)

xiii. campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

The data set consists of multiple binary, categorical and numeric features. The goal of the project will be to learn from all the features provided and predict if the customer will subscribe to product or not.  The response/result variable y has two responses yes or no. 



# Exploratory Data analysis Findings:


Based on the exploratory data analysis done I have found below facts about the data set<br>


i. The dataset is extremely unbalanced with 7.2% positive(yes) and 92.8% negative labels(no). <br>
ii. Numerical feature have outliers, and removing outliers reduces positive labels to apps 3%.  <br>
iii. Categorical features day and month, housing and month seems to have a positive correlation. <br>

# Machine Learning model used:

To search for best machine learning model I have relied on PyCaret library and have performed. Then I have performed multiple permutation combinations of classification algorithms and class weight parameters, and no of iterations.  <br>
Along with different model combinations I have performed some feature engineering as well on the original dataset. Below is the summary report of all the models tested . <br>



|Model Name|Accuracy Score|roc_auc score|Class Weight|Classifier optimization param|Param Optimization|
|---|---|---|---|---|---|
11|LGBMClassifier(Features Binned\#8)|0\.909667|0\.951285|balanced|auc|Yes|
|1|LGBMClassifier|0\.887417|0\.884991|balanced|auc|No|
|4|SVC Linear Kernel|0\.856000|0\.870000|balanced|none|Yes|
|0|LogisticRegressionCV|0\.937146|0\.867344|balanced|roc_auc|No|
|5|LogisticRegressionCV|0\.937000|0\.867000|balanced|roc_auc|Yes|
|3|LGBMClassifier(iter\#1500)|0\.75725|0\.862765|balanced|auc|Yes|
|2|LGBMClassifier(iter\#2000)|0\.745167|0\.855194|balanced|auc|Yes|
|10|LGBMClassifier(Features Binned\#500)|0\.703667|0\.840194|balanced|auc|Yes|
|6|StackingClassifier|0.\678250|0\.814363|--|--|No|
|7|XGBClassifier|0\.962333|0\.747744|--|aucpr|Yes|
|9|LGBMClassifier(Features removed)|0\.480917|0\.717434|balanced|auc|Yes|
|8|XGBClassifier(Features removed)|0\.941333|0\.613068|balanced|roc_auc|Yes|



LGBMClassifier with binned features ( month and day) is the best performing model for the problem at hand.  The model achieved 90.9% accuracy and 95.12% precision-recall AUC, the model is able to identify positive labels with 100% accuracy ( perfect recall ).  <br>

 <br>
The code for the model can be found in below notebook <br>
notebook link : https://nbviewer.org/github/jsJyo/TermDepositSubscription/blob/main/Term_Deposit_Subscription.ipynb

# Conclusion:

Based on the feature importance analysis of best performing model, below are the findings <br>

i. duration followed by balance, followed by age and the campaign are the most important predictors.<br>
ii. People who were contacted in the second half of the month were more inclined to subscribe.<br>
iv. People with secondary education are most likely to subscribe as compared to other education levels.<br>
v. people in blue color jobs are most likely to subscribe as compared to people in other professions.
<br>



Based on Customer segmentation performed for subscriber data below are the findings<br>


For cluster 0(majority segment ) , Customers shared below mentioned traits<br>
i. marital status is married (followed by single)<br>
ii. have secondary education level<br>
iii. are in Blue-Collar jobs<br>
iv. have no personal loan and never defaulted<br>
v. have housing loan<br>
vi. were contacted for less than 300 seconds<br>
vii. have balance less than 3000 and are between age group 32-55 years<br>
are the most likely going to subscribe to the product.<br>


Profile 2 for customers <br>
For cluster 1(second largest cluster) , we can say customers whose<br>
i. marital status is single(followed by married)<br>
ii. have tertiary education level<br>
iii. are in management jobs<br>
iv. have no personal loan, no housing loan and never defaulted<br>
v. were contacted for less than 300 seconds<br>
vi. have balance less than 3000 and are between age group 32-55 years <br>

Profile 3 for Subscribing customers <br>
For cluster 2(smallest cluster) , we can say customers whose<br>
i. marital status is married<br>
ii. have secondary education level<br>
iii. are retired(followed by technician job)<br>
iv. have no personal loan, no housing loan and never defaulted<br>
v. were contacted for less than 400 seconds<br>
vi. have balance less than 2000 and are between age group 33-60 years<br>
are the most likely going to subscribe to the product.<br>




