# Health-Insurance-Predictions

## Task: predict health insurance owners who will be interested in car insurance

An insurance company provided health insurance to its customers. Now they want a model to predict whether last year's policyholders (customers) will also be interested in the car insurance provided by the company.
Before creating a model, let's explore the dataset and get insights from the data.

# EDA

## Target variable: Response

<img width="461" alt="image" src="https://user-images.githubusercontent.com/57068021/169706444-b7bbb53b-996a-4eb6-94e4-eac45e6d4890.png">

We see here that our data is very unbalanced.

## Gender

<img width="461" alt="image" src="https://user-images.githubusercontent.com/57068021/169706453-e16c6d28-4240-4eea-b6e8-502e2e3452b9.png">

* We have more samples for the male gender.
* It would therefore seem that men are more affected by health problems than women (this information does not allow us to be certain, it would perhaps require a more complete dataset to be sure).

## Age

<img width="833" alt="image" src="https://user-images.githubusercontent.com/57068021/169706463-407f14a6-b31a-4452-bb5e-400d57b06acd.png">

* Young people under 30 are not interested in insurance for their vehicle. The main reasons could be lack of experience, maturity and the fact that they don't own high cost vehicles yet.
* People between 30 and 60 seem to be more interested.

## Driving License

> ***You should always have a driver's license while driving***

* Here too, the majority of observations relate to people with a driving licence.

## Distribution by region

* The meaning of these codes has not been provided.
* Most of the data is collected from people living in the area with the code 28​.

## Previously insured

* Those who already have insurance are not interested. This is a rather obvious result.

## Vehicule Age

<img width="434" alt="image" src="https://user-images.githubusercontent.com/57068021/169706486-75121f12-f6b4-4f89-9fc9-17db7f20b265.png">
<img width="463" alt="image" src="https://user-images.githubusercontent.com/57068021/169706496-e0082c55-f8a7-4043-a4a1-37669f1663df.png">

* More than half of the data (52%) concerns samples whose vehicle age is between 1 and 2 years.
* We cannot tell from the second graph that people with a vehicle age between 1 and 2 years are more interested because the other category “> 2 years” has very few observations.

## Vehicle damage

<img width="463" alt="image" src="https://user-images.githubusercontent.com/57068021/169706502-7f4422ff-566d-44dd-a1b9-51f1749ab8d8.png">

*  Customers who got his/her vehicle damaged in the past is more likely to be interested in insurance. May be because he has first-hand experience of its pros and cons.
* Ah! I want a version of 'Prevention is better than cure' for this situation.

<img width="830" alt="image" src="https://user-images.githubusercontent.com/57068021/169706522-97d965f7-c739-4ba9-8661-d73ba8441717.png">

* I don't think this gives much additional information.
* Outliers may be present here.

<img width="830" alt="image" src="https://user-images.githubusercontent.com/57068021/169706530-cf979ec3-6d60-49aa-8e0e-c6ca6c8e4f26.png">

* This graph looks interesting. But to extract information clearly, we need the meaning of these codes.

<img width="830" alt="image" src="https://user-images.githubusercontent.com/57068021/169706538-277e92d1-152a-4ed8-b2b6-f9df8e7ffd9b.png">

* Our target variable is not very affected by this feature. It can be abandoned.

<img width="629" alt="image" src="https://user-images.githubusercontent.com/57068021/169706543-f57f73a1-ca25-493f-bcf9-7de0cbe68028.png">

I will remove the less correlated features for modeling.

# Classification

To balance this data, we will oversample the minority class using resampling from the sklearn library.
To avoid data leakage, I will first split into train and test subsets and then oversample.

We used different classifiers, but the one that maximises the ROC-AUC is a XGBoost Classifier, with ROC-AUC = 85%.

|         Model       | ROC-AUC |
| ------------------- | ------- |
| Logistic Regression |   61%   |
|    Random Forest    |   81%   |
|    XGBClassifier    |   85%   |
