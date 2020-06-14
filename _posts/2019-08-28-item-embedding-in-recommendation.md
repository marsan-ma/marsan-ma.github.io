---
layout: post
title:  "Item Embedding in Recommendation with Item2vec & Siamese-CNN"
date:   2019-08-28
excerpt: "Item Embedding is the new standard for recommend-system. Here I'm gonna introduce how I use both Item2vec and Siamese Network to build recommendation models learn from both item content and user behavior."
project: true
tag:
- recommend system
- siamese network
- item2vec
- nlp
- deep learning
- neural network
- cnn
feature: assets/img/blog/reco1.png
comments: true
---

## Intro

This is a post about one of my favorite project: a deep learning recommendation system learn from both user-behavior and item context. The main credit of this system is that: 
1. It's a single system learn from both user behavior & item context, thus good in both accuracy and recall, and immune from cold-start.
2. To predict with MM level itemXuser combinations, we designed a special architecture to make online prediction super cheap by leveraging ANN (approximate nearest neighborhood).

Here's the slide:

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/1n6XYyMVCxqdc3" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/marsanmars/universal-job-embedding-in-recommendation-public-ver-211934555" title="Universal job embedding in recommendation (public ver.)" target="_blank">Universal job embedding in recommendation (public ver.)</a> </strong> from <strong><a href="//www.slideshare.net/marsanmars" target="_blank">Marsan Ma</a></strong> </div>
</center>


## Architecture

The whole architecture is like this. It looks fancy, and took me quite a lot of effort struggling through whole bunch of infra troubles, LOL.

![Architecture][reco1]


## Key concept
1. Learn user behavior through a graph model: [item2vec with global context][ref1], which is the 2018 best paper proposed by AirBnb.
2. Extend this template converting user session to binary classification, use [siamese-network][siamese1] to learn from item context.
3. On production for predicting on the fly, we use cached item-embeddings and user-embeddings calculated offline to do the prediction, this largely reduced the computing complexity, making neural network model results could be used online for millions users x millions items scale product.


## Item2Vec

This model actually comes from word2vec, just treat the user session as a sentence and each item visited as a work token, then you could apply the skip-gram model like work2vec.

After all, the item2vec helped us transfering the recommendation problem into a binary classification problem. The training process is actually a way to formulate the item embeddings and define the "distance" among items.

![Item2vec][reco2]

Airbnb improved this model by introducing the idea of "global context", which enable us to treat clicks event and paying event in different weight. Since this two kinds of user behavior is having very different level of interest to the item.  


![Item2vec with Global Context][reco3]


## Siamese Network

Finally, with the help of item2vec concept, we could switch the binary classification with siamese-network, so we could also incorporate with item context into our model. That's how we learn from both user-behavior and item-context in a model, end-to-end.

![Siamese][reco4]

Here I use cnn as the encoder, since its fast and having good performance. Feel free to switch the encoder to any fancier stuff if you have enough budget for the extra computing power :p


[a1]: https://www.kdd.org/kdd2018/accepted-papers/view/real-time-personalization-using-embeddings-for-search-ranking-at-airbnb
[siamese1]: https://en.wikipedia.org/wiki/Siamese_neural_network

[reco1]: /assets/img/blog/reco1.png
[reco2]: /assets/img/blog/reco2.png
[reco3]: /assets/img/blog/reco3.png
[reco4]: /assets/img/blog/reco4.png