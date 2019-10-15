---
layout: post
title:  "Binomial Logistic Regression"
subtitle: "Predict whether a person makes over 50K per year using the Census Income Data Set"
date:   2019-10-15 10:45:13 -0500
background: '/img/posts/06.jpg'
---

I found a Census Income data set with information about age and income.

Logistic regression is a classification algorithm, which means that it predicts which class, or group, a data point is likely to fall into. 

There can be two classes (binomial logistic regression), or more than two classes (multinomial logistic regression). 

In this case, I am finding a relationship between age and monthly income. I’m assuming that older people have a higher income than younger people who are newer to the job market and have less experience.

In this dataset, the only information I have about people’s yearly income is whether it’s less than or equal to 50,000, or greater than 50,000.

If I had an exact income for each person, I would run a linear regression model that would show that there was a positive relationship between age and income, which could help to predict a person’s monthly income based on their age.

However, since I only have to two classes, “<=50K” and “>50K”, I’ll run a binary logistic regression model to predict whether a person is more likely to make over 50K per year. 

If the income variable were continuous, linear regression would be a good fit, however since income is a binary variable, it is better suited for a logistic regression.
In a logistic regression the outcome, or dependent variable, takes a value between 0 and 1, which can be interpreted as a probability. 

The probability that a person’s income is greater than 50K is the probability that a person’s income is equal to 1.

Evaluation

I evaluated my model using the AUC metric. My model has an AUC of .68, which means it has a 68% accuracy rate. It’s useful for predicting whether a person makes over 50K.

AUC and ROC
AUC (Area Under the Curve) refers to the area under the ROC (Receiver Operating Characteristic) curve, which graphs the tradeoff between the true positive rate (TPR) and false positive rate (FPR) of the classification model. 
The AUC compares the model’s TPR and its FPR, indicating the usefulness of a classification model.


TPR and FPR
The TPR is the rate at which the model’s predicted outcome is the actual outcome.

The FPR is the rate at which the model’s predicted outcome is not the actual outcome. It’s a false alarm, or a type 1 error (rejecting the hypothesis when it’s true). 

TPR and FPR are based on a confusion matrix.

A great way to understand TPR and FPR is credit card fraud. 
Your bank declines your card because it predicts that someone else is using your card. If someone else is actually using your card, that is a true positive. The bank predicted fraud when there was fraud.

When your card declines in front of everyone when you’re out at a restaurant, it’s a false positive, because the bank predicted fraud when there was no fraud.

The positive is the bank’s guess that there was fraud and declining the card, the “true“ or “false” is whether the that guess was right or wrong.

Key Ideas
When training a model, it is ideal that the ROC curve will hug the upper left corner of the graph, because that would maximize the Area Under the Curve (AUC). The greater the AUC, the more accurate the model.

An AUC of 1 means that the model’s prediction is accurate 100% of the time, and an AUC of .5 means that the the model is accurate 50% of the time. A 50% accuracy rate is useless because the probability of TPR is equal to the probability of FPR. The model is wrong 50% of the time. It is like random guessing, or a coin flip, it’s useless to have a model that is only correct 50% of the time. 

Why would your credit card be useful if it declines every other time you use it?
You would want more true positives (benefits) and less false positives (costs). 

A 45 degree angle line on the graph helps to visualize how close the AUC is to 50% accuracy— or equal rates of true positives and true negatives. 

The 45 degree angle line serves as a divider, or threshold for TPR and FPR. Moving the threshold changes the AUC so that the model is more or less sensitive to detection.


