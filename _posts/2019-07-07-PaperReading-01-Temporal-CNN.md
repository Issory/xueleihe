---
layout: post
title: Understanding of "Design Light-Weight 3D Convolutional Networks"
tags: [paper,temporal,deep learning,fast]
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---
# Objective
Deep 3D CNN for spatio-temporal information fusion ability

# Problem
1. The constraint of the memory
2. The constraint of the computing power

# Proposed
1. two-stage fully separable block
2. temporal residual gradient
3. hybird Fast Algorithm 

# Advantage
1. compress the model sizes
2. improve the performance of compress model
3. decrease the computing workload

# Method
1. Fully separable block
    - Stage One
        - temporal pixel for temporal features $(\alpha N,C,K,1,1)$
        - 2D convolution kernels for spatial features 
    - Stage Two
        - convolution in single channel $(\alpha N,1,1,R,S)$
        - $1\times1\times1$ kernels at last $(N, \alpha N,1,1,1)$
    - Memory cost $\alpha NCK +\alpha NRS +\alpha N^2$
    ![Fig1](https://github.com/Issory/issory.github.io/blob/master/img/2019-07-07-PaperReading-01-Temporal-CNN/Fig1.png?raw=true)
{: .box-note} **Note that**
    - The input $N(Channel)\times C(Batch Size)\times T(Thick) \times H(Height) \times W(weight)$
    - The kernel $(N(Channel),C(Batch Size),K,R,S)$
    - Traditional memory cost $N\times C\times K\times R\times S$


2. Temporal residual gradient
    - In single channel, $T$ time steps has $T-1$ temporal residual gradient in pixel.
    - Mean of $T$ time steps is added for statistical distribution
    ![Fig2](https://github.com/Issory/issory.github.io/blob/master/img/2019-07-07-PaperReading-01-Temporal-CNN/Fig2.png?raw=true)

3. Fast Algorithm[1](#1)
    - Core:
        - 1D 
            - Traditional Multiplicatoins for Convolution: Kernel size $(m,r)->(m\times r)$ 
            - Fast Algorithms: $(m,r)->(m+r-1)$
        - 2D
            - Traditional Multiplicatoins for Convolution: Kernel size $(m\times m,r\times r)->(m^2\times r^2)$ 
            - Fast Algorithms: $(m,r)->(m+r-1)^2$

# Reference

1. <span id="1">Lavin, Andrew, and Scott Gray. "Fast algorithms for convolutional neural networks." Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2016.</span>
