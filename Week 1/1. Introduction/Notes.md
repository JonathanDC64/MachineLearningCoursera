# Introduction

- [Introduction](#introduction)
  - [**Supervised Learning**](#supervised-learning)
  - [**Unsupervised Learning**](#unsupervised-learning)

**Machine Learning**: 

The field of study that gives computers the ability 
to learn without being explicitly programmed.

A computer program is said to learn from experience
E with respect to some task T
and some performance on T, as measured by P,
imporves with exprerience E.

Example: playing checkers.

E = the experience of playing many games of checkers

T = the task of playing checkers.

P = the probability that the program will win the next game.

---

**Machine learning algorithms**:

- Supervised Learning
- Unsupervised Learning
- Reinforcement Learning
- Recommender Systems

## **Supervised Learning**

> "Right Answers" given. AI must get that answer for positive learning

In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

Supervised learning is categorized into:

> <ins>**Regression**</ins>: Predict continuous valued output (price for example).

and

> <ins>**Classification**</ins>: Discrete valued output (0 or 1 for example)

**Example**:
You’re running a company, and you want to develop learning algorithms to address each of two problems. 

> **Problem 1**:You have a large inventory of identical items. You want to predict how many of these items will sell over the next 3 months.

> **Problem 2**: You’d like software to examine individual customer accounts, and for each account decide if it has been hacked/compromised. Should you treat these as classification or as regression problems?

<ins>**_Answer_**</ins>: Treat problem 1 as a regression problem, problem 2 as a classification problem.

## **Unsupervised Learning**

> Don't give the algorithm any information in advance other than input data

Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure from data where we don't necessarily know the effect of the variables.

We can derive this structure by clustering the data based on relationships among the variables in the data.

With unsupervised learning there is no feedback based on the prediction results.

**_Example_**:

Clustering: Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.

Non-clustering: The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a cocktail party).