---
layout: post
title:  "Binomial Logistic Regression"
subtitle: "Predict whether a person makes over 50K per year using the Census Income Data Set"
date:   2019-10-15 10:45:13 -0500
background: '/img/posts/06.jpg'
---

I found a Census Income [dataset](https://archive.ics.uci.edu/ml/datasets/census+income) extracted from the 1994 Census database. It includes information about about age, income, work status, education level, marital status, occupation, relationship status, race, sex, hours worked/week, and country of origin. I chose this dataset because I wanted to see if age could be a predictor of annual income. 

My [hypothesis (Ha)](https://en.wikipedia.org/wiki/Alternative_hypothesis) is that older people have a higher income than younger people who are newer to the job market and have less experience. I want to reject the status quo, or [Null hypothesis(H0)](https://en.wikipedia.org/wiki/Null_hypothesis), that age has no significant effect on income.

If I had each person's exact income, I would use a linear regression model to show that there is a positive relationship between age and income.

However, the income variable isn't continous, it's categorical because I only have two responses throughout the dataset, “<=50K” and “>50K”. Since each data point falls into either "<=50K" or ">50k", I consider them groups, or classes. I would have to use a classification algorithm to predict which class a person is more likely to fall into based on their age.

I couldn't answer the question, "What is the income of person X given her age?", but I could answer the question, "Is person X likely to make more than $50,000/year given her age?". 

I decided to use logistic regression to analyze the effect that age has on income.

See the entire project here: [Using Logistic Regression to Predict Income](https://github.com/zhaben/Logistic-Regression-Predict-Income). 

Logistic regression is a classification algorithm, which means that it predicts which class, or group, a data point is likely to fall into. There can be two classes (binomial logistic regression), or multiple classes (multinomial logistic regression). 

In a logistic regression, while the predictor (independent variable) remains continuous, the outcome (dependent variable) takes on a value between 0 and 1, which can be interpreted as a probability. 

The probability that a person’s income is over 50K is the probability closer to 1.
The probability that a person’s income is 50K or below is the probability closer to 0.

For example, a probabilty of .5 would mean that there is a 50% chance that her income is over 50K.

The "model" is the equation of the curve intended for prediction.

# Evaluation


#### Test Dataset

After creating a model, I evaluated its performance using the test dataset, a part of the original dataset set aside to test the model's performance. Evaluating model performance with the data used for training is not acceptable in data science because it can easily generate overoptimistic and overfitted models.

I vizualized the results, and the curve looked similar to the training dataset's curve.


## AUC and ROC Curves Metric

I evaluated my model using the AUC metric. My model has an AUC of .68, which means that it successfully classified 68% of people.

AUC (Area Under the Curve) refers to the area under the ROC (Receiver Operating Characteristic) curve, which graphs the tradeoff between the true positive rate (TPR) and false positive rate (FPR) of the classification model. The AUC compares the model’s TPR and its FPR, indicating the model's usefulness.


#### TPR and FPR

The TPR is the rate at which the model’s predicted outcome is the actual outcome.

The FPR is the rate at which the model’s predicted outcome is not the actual outcome. It’s a false alarm, or a type 1 error (rejecting the null hypothesis when it’s true). 

TPR and FPR come from the concept of a [confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix).

A great way to understand TPR and FPR is credit card fraud. 

Imagine that someone is splitting the bill at a fancy restaurant with your credit card. The bank declines the payment because it predicts that someone else is using your card. 

If it's you at the fancy restaurant-- that is a true positive. The bank predicted fraud when there was fraud.

If it's not you, and your card declines in front of everyone-- that is a false positive, because the bank predicted fraud when there was no fraud.

The positive is the bank’s guess that there was fraud, declining the card. The “true“ or “false” is whether the that guess was right or wrong.


#### ROC Graph

When training a model, it is ideal that the ROC curve will hug the upper left corner of the graph, because that would maximize the Area Under the Curve (AUC). The greater the AUC, the more accurate the model.

An AUC of 1 means that the model’s prediction is accurate 100% of the time, and an AUC of .5 means that the the model is accurate 50% of the time. A 50% accuracy rate is useless because the probability of TPR is equal to the probability of FPR. The model is wrong 50% of the time. It is like random guessing, or a coin flip, it’s useless to have a model that is only correct 50% of the time. 

Why would your credit card be useful if it declines every other time you use it?
You would want more true positives (benefits) and less false positives (costs). 

A 45 degree angle line on the graph helps to visualize how close the AUC is to 50% accuracy— or equal rates of true positives and true negatives. 

The 45 degree angle line serves as a divider, or threshold for TPR and FPR. Moving the threshold changes the AUC so that the model is more or less sensitive to detection.
