---
title: "Chapter 4: Classification"
date: 2025-11-25
draft: false
series: ["ISLP"]
tags: [statistics]
---
As we all know, there are two main types of data: quantitative and qualitative. The linear regression models in previous chapters help us to predict quantitative responses. But what about qualitative ones? 

The task of predicting qualitative responses is known as *classification*. In this chapter, we will walk through the base idea of classification and some of the most basic and common classification models.

Some examples of classification problems include:
- A person arrives at the emergency room with a set of symptoms that could possibly be attributed to one of three medical conditions. Which of the three conditions does the individual have?
- An online banking service must be able to determine whether or not a transaction being performed on the site is fraudulent, on the basis of the user’s IP address, past transaction history, and so forth.
- On the basis of DNA sequence data for a number of patients with and without a given disease, a biologist would like to figure out which DNA mutations are deleterious (disease-causing) and which are not.

In this chapter, we will illustrate the concept of classification using the simulated Default data set. We are interested in predicting whether an individual will default on his or her credit card payment, on the basis of
annual income and monthly credit card balance.

# Why not use linear regression?
There are two main problems with using linear regression for classification.

First is how to encode the qualitative response variable. For example, if we are trying to classify three types of diseases : stroke, drug overdose, and epileptic seizure. How should we encode them? If we use 1 for stroke, 2 for drug overdose, and 3 for epileptic seizure, then we are accidentally implying that drug overdose is somehow "twice" as severe as stroke, and epileptic seizure is "three times" as severe as stroke.

Second, even if we could find a reasonable way to encode the qualitative response, for example, in email classification, we could use 0 for "not spam" and 1 for "spam", there is still problems. In classification, to determine whether or not one response belongs to a certain class, we usually base on the probability of the response belonging to that class. For example, if the probability of an email being spam is greater than 0.5, we classify it as spam; otherwise, we classify it as not spam. So the out come of the model we need is a probability value between 0 and 1. However, linear regression does not guarantee that the predicted values will fall between 0 and 1. In fact, it is very possible to get predicted values less than 0 or greater than 1, which makes no sense in classification problems.

# Logistic Regression
Consider the Default data set, where the response default falls into one of two categories, Yes or No. We use logistic regression models the probability of default given the predictors balance and income. E.g. the probability of default given balance can be written as:
$$P(Default=Yes|Balance)= \pi (Balance)$$
for any individual for whom p(*balance*) > 0.5, we predict that the individual will default.
## The logistic model (a.k.a logistic function)
The original idea is to solve to second problem of linear regression model. As you know, the linear regression model is in the form of:
$$p(Y) = \beta_0 + \beta_1 X$$
