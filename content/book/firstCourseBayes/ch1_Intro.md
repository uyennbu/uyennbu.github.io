---
title: "Chapter 1: Introduction and examples"
date: 2025-11-12
draft: false
series: ["A First Course in Bayesian Statistical Methods"]
tags: [bayesian statistics]
---
# Chapter 1: Introduction and examples
## What is Bayesian Statistics?
- Bayesian inference is the process of **inductive** learning via Bayes' rule.
- Bayes rule does not tell us what our beliefs should be, it tells us how should they change after seeing new information.
## Notation
- parameters: \(\theta\) (we call it parameter because we calculate y from it, in normal cases)
- dataset: \(y\) (sample of the population)
- sample space : \(\mathcal{Y}\) (all possible datasets)
- parameter space : \(\Theta\) (all possible parameters)
- prior distribution: \(p(\theta)\) (for each \(\theta \in \Theta\), \(p(\theta)\) is our belief that \(\theta\) represents the true population chracteristic)
- sampling method: \(p(y|\theta)\) (our belief that \(y\) should be observed if \(\theta\) is known)
- posterior distribution: \(p(\theta|y)\) (our belief that \(\theta\) is the true population characteristic after observing \(y\))
## Bayes' Rule
$$p(\theta|y) = \frac{p(y|\theta)p(\theta)}{\int_\Theta p(y|\tilde{\theta})p(\tilde{\theta})d\tilde{\theta}}$$
## Examples
### Using Bayes inference to estimate posterior probability
### Using Bayes inference to estimate parameter in a predictive model
