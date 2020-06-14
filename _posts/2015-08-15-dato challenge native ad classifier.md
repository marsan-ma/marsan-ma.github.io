---
layout: post
title:  "Dato Challenge: native ad classifier"
date:   2015-08-15
excerpt: "It's my code doing the Data Kaggle challenge. In this challenge, we are requested to develop a system predicting whether an article is a native advertisement. It’s involves lots of natural language processing tricks, like boilerplate removing, topic modeling and embedding techniques."
project: true
tag:
- machine learning
- logistic regression
- random forest
- svm
- blending model
- kaggle
- dato
feature: https://kaggle2.blob.core.windows.net/competitions/kaggle/4493/media/dato_banner3.png
comments: true
---

# "Truly Native?" 

My code doing the [Data Kaggle challenge](https://www.kaggle.com/c/dato-native): Here is the [Github repository](https://github.com/Marsan-Ma/tnative) of this work.


### Briefing

In this challenge, we are requested to develop a system predicting whether an article is a native advertisement. It’s involves lots of natural language processing tricks, like boilerplate removing, topic modeling and embedding techniques. My final model is a blending of several bagging logistic regression, two gradient boost trees, and two field-aware factorized machine, which achieved 0.974 AUC in private board. (while 1st prize winner achieves 0.998). 


### Code Hierarchy

The entry script is [go_parse.sh](https://github.com/Marsan-Ma/tnative/blob/master/go_parse.sh) and [go_train.sh](https://github.com/Marsan-Ma/tnative/blob/master/go_train.sh), every thing start with these two. While the former is used to parse data into mongodb and latter do the model training and evaluation. 

There are a couple of different models to choose, and feature selection, blending, hyperparameter searching experiments which you could choose the function and tune the setting in [main.py](https://github.com/Marsan-Ma/tnative/blob/master/main.py).


### About dataflow

Here I tried to separate data pipelines into independent stages. Like, you could change input data format without refactoring the learning models or evaluation stages, and vice versa. Senior Kagglers might find this project get an overkill big structure, that's because this framework try to become a generic framework for any kinds of data science products.
