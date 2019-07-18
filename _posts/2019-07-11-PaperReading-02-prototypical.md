---
layout: post
title: Understanding of "Prototpical Networks for Few-shot Learning"
tags: [paper,deep learning,few shot]
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---
# Objective
few-shot classification

# Proposed
1. Prototpical Networks

# Advantage
1. learn a metric space

# Method
1. Compute mean features of support set samples as prototyical feature
    $${c_k=\frac{1}{\left |S_k\right |}\sum\nolimits_{(x_i,y_i)\in S_k} f_{\phi}(x_i)}$$, where $c_k$ is the prototype representation, $f_{\phi}$ is the embedding function and $\phi$ is the learnable parameters
2. loss is the euclidean distance between prototyical features and test features
    - $${p_{\phi}(y=k|x) = \frac{\exp(-d(f_{\phi}(x)),c_k)}{\sum_{k'}\exp(-d(f_{\phi}(x)),c_{k'})}}$$
    where $d$ is the distance function.
    - $\arg\min J(\phi)=-\log p_{\phi}(y=k|x)$
![Fig1](https://github.com/Issory/issory.github.io/blob/master/img/2019-07-11-PaperReading-02-prototypical/Fig1.png?raw=true)

# Keras Implementation
[See in Github](https://github.com/issory/prototypical-network) 