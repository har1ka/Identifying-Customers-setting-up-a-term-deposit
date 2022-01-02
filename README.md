# Identifying-Customers-setting-up-a-term-deposit
Identifying the potential customers that are likely to set up a term deposit at a Portuguese banking institution along with the key characteristics that add value to the marketing campaign.  After preprocessing the data, that includes treating the imbalanced class through sampling techniques, we have evaluated the performance of several classification models such as Logistic regression, Decision Trees, Random Forests, Gradient Boosting Classifier, K-NN and SVM. Random Forest ended up as the best performing model among all of them, where F1-Score has been chosen as the evaluation criteria.

## Summary
Banks use depositor’s money to make loans. Term deposits which are deposits in a financial institution with a specific maturity rate are one of the major sources for a bank which they can use to make loans. Banks follow various marketing strategies like email marketing, SMS/Phone call marketing, advertisements etc. to reach out to the customers. Phone call campaigning is one of the traditional forms of marketing and, when done suitably, can have the best results. Most of the businesses follow a priority queue where they shortlist the customers, they believe are likely to convert. Organizations allot a huge number of resources towards organizing such campaigns which makes the task of identifying potential customers a crucial one. Our aim was to identify such potential customers that the bank could target and help banks make optimal usage of their resources.

## How to classify the customers?
For instance, if the duration of call made to a customer is long, then the customer is likely to set up a term deposit. In addition to this, if the outcome of the previous marketing campaign of a customer was a success, there are higher chances that the customer would convert this time as well i.e., set up a term deposit. Along with these, if the customer has a high consumer confidence index, the probability of conversion might be higher. All such relevant features were identified, and the customers were classified accordingly using suitable classification algorithms.

## Exploratory Data Analysis
The EDA revealed some interesting and useful results. Majority of the customers reached out by the Bank were in the age range of 25-50 years. Moreover, there was an increase in numbers of subscribers to term deposits as the age increased. Similar trend was observed with the duration of the call. Higher subscriptions to term deposits were observed with longer durations of phone call. The longer a customer talks on the call, more interested he is in setting up a term deposit.

Visualizations for Socioeconomic factors indicated that Lower Consumer Price Index and higher Consumer Confidence Index is more favorable for a positive outcome. Moreover, the Bank received comparatively more positive responses from the customers who were a part of some previous campaign run by the Bank.

Variables such as no. of employees, euribor3m, consumer price index and employment variation rate are strongly correlated. We have removed them from the training data as highly correlated features may negatively impact the model efficiency. The target variable ‘y’ has a strong correlation with the no. of employees and duration.

We also performed chi square tests with the categorical variables. We took the alpha value as 0.05 and performed hypothesis tests, during which it was revealed that p value for Loan variable is greater than alpha and it was not included for training.

## Preprocessing
Before training the models on our data, we properly cleaned and preprocessed the data so that we can remove any bias that is already present in the data. Most of the features had very few unknown values which were dropped, but the variables education and job had almost 4% and 1% unknowns respectively. The unknown values in education variable were imputed by inferring the values from the job variable. The unknown values in job variable where age was >60 were considered retired and the rest were dropped.

### Dealing with class imbalance
The dataset at hand is a highly imbalanced dataset with 89% negative and 11% positive responses. Having an imbalanced dataset, leads to bias towards the majority class in the trained model, which may lead to decreased performance. In order to deal with this problem, we used the Synthetic Minority Oversampling Technique (SMOTE) to make the dataset balanced. This is a statistical technique that makes the dataset balanced by sampling new instances from the feature space of the minority class.

Following the balancing of the dataset, we have encoded all the categorical variables to make them suitable for training the classification models.

## Modeling
Given the information about a customer, we are using a classification algorithm to predict whether a customer would set up a term deposit account or not. We have preprocessed all the data and split it into train and test datasets in the ratio 80:20. We have used 10-fold cross validation on the training data to estimate the performance of the training data. We have used different suitable classification algorithms to identify the best model that can capture all the variation in the data. 

For most of the algorithms, there are multiple hyperparameters to choose from and identifying the optimal hyperparameters to attain an optimal model is a challenge. We have performed grid search for each of the algorithms limited to certain specific hyperparameters rather than extensive grid search on all hyperparameters and all combinationsdue to hardware and time constraints. We have used average f1 score as the evaluation metric during 10-fold cross validation. Logistic regression was implemented using step wise AIC in R while all the other algorithms were implemented using the sklearn library in python.

We have achieved the best results on the test data, using Random Forest as the classification model. Logistic regression is a fast but simple classifier. Although, it has achieved good accuracy and precision , it has attained the least recall and f1-score. Duration of the call has achieved the highest feature importance according to the random forest classifier, which is in line with the insights generated during EDA. Similarly, the insights from EDA are consistent with the 3-month Euribor interest rate and month of the year, w.r.t having high importance in predicting whether a customer would set up a term deposit or not.


