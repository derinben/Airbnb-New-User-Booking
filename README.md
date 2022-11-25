# Airbnb-New-User-Booking

## Summary

In this project, we try to predict the booking destination of a newly onboarded user on Airbnb platform. To evaluate the model's performance, we used NDCG as the metric to improve the degree of relevance and the ranking of the predictions we make. 
With this, Airbnb could potentially 
- Provide personalized experience
- Better forecast demand

### Dataset 

The problem statement and dataset is derived from [Kaggle's - Airbnb New User Bookings Challenge](https://www.kaggle.com/competitions/airbnb-recruiting-new-user-bookings). 
The predictor variables include information about the users (user_id, age, gender etc.) and preliminary session data (actions, action types, session time etc.). 
Our objective would be to predict the country (dependent variable) that the user is most likely to visit.
It is to be noted that only a limited set of users have associated session data and therefore, we merge (inner join) the datasets and proceed for modelling with about 5.5 mil session observations for close to 73k users. 

### Methodology 

In order to produce the results, we performs data preparation, data preprocessing, feature engineering, model building, evaluation and yperparameter tuning.
Some amount of EDA was done to understand the dataset which can be found here. 

Some challenges in this dataset is handling the imbalanced dataset and limited information available.

#### Peek into feature engineering and selection that improved the results to a great extent
<img src = https://user-images.githubusercontent.com/42509638/203994464-830d6531-a790-498d-b73c-1dd2cab48c7e.png width = 700>

#### Features that indicated higher likelihood of even making a booking in the first place 
![image](https://user-images.githubusercontent.com/42509638/203994541-a5cf65c2-d3a6-4b57-ba3e-d23c0262557c.png)

#### Features that indicated lower likelihood of making a booking
![image](https://user-images.githubusercontent.com/42509638/203994591-cb4179bc-a2bc-4f9d-ab07-66f59ba56042.png)


# Modelling

The models we try out are as follows:
Multinomial regression - using Softmax function and L2 regularization applied to help with classifying our target variables beyond the two categories where we apply logistic regression.

Bernoulli Naive Bayes - Bernoulli Naïve Bayes is well suited for discrete data with binary features which was the case after we completed feature engineering.

Decision Trees - highly predictive due to their capability of mapping non-linear relationships well. Results are also easily interpretable within the business context.

XGboost - Allows us to leverage its regularization technique (using both L1 and L2), sparsity awareness (robust learning from missing values) and in-built cross validation. 

![image](https://user-images.githubusercontent.com/42509638/203993655-aaac4f59-9163-4483-8b66-a1d0d95cce2d.png)

Consequently, Xboost gave the best performance of a NDCG score of 88.323. 

## For further improvements

- Airbnb can consider data on detailed user demographics, as well as sessions' data (e.g., session time and data, search queries, etc.)
- Work with relevant stakeholders to further refine feature selection. 
- We can cansider Novelty as a metric for recommending new travel destinations to users 
