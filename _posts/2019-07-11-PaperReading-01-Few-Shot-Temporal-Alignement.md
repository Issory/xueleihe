---
layout: post
title: Understanding of "Few-shot Video Classification via Temporal Alignment"
tags: [paper,temporal,deep learning,few shot]
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---
# Objective
Classify a previous unseen video

# Problem
1. few-shot learning framework
2. leverages the temporal ordering information

# Proposed
1. Temporal Alignment Module

# Method
1. Embedding Module
    - frame sampling
    - the sampled video is encoded into features
2. Distance Measure with Temporal Alignment Module(TAM)
    - Compute the frame-level distance matrix as 
    $$D_{l,m}=1-\frac{f_{\varphi}(S_i)_ l \cdot f_{\varphi}(S_j)_ m}{\|f_{\varphi}(S_i)_ l\|\|f_{\varphi}(S_j)_ m\|}$$
    where $S_i$ and $S_j$ are sampled videos, $f_{\varphi}$ is embedding function with $\varphi$ learnable parameters, and $l,m$ are the index of frames.
    - the best alignment 
    $$W^*=\arg\min\nolimits_{W\in B}\langle W,D(f_{\varphi}(S_i),f_{\varphi}(S_j))\rangle$$, where B is the binary alignment matrix.
    - Dynamic Time Warping 
    $$\gamma(i,j)=D_{ij}+\min\{\gamma(i-1,j-1),\gamma(i-1,j),\gamma(i,j-1)\} $$
    - Relaxation $\min(x_1,x_2,\cdots,x_n)\approx-\lambda\log\sum\nolimits_{i=1}^n e^{-x_i/\lambda}$

![Fig1](https://github.com/Issory/issory.github.io/blob/master/img/2019-07-11-PaperReading-01-Few-Shot-Temporal-Alignement/Fig1.png?raw=true)

