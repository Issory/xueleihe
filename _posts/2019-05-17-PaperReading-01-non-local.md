---
layout: post
title: Understanding of "Non-local Block"
tags: [paper,no-local,deep learning]
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---
# Feature of Non-local operation[1](#1)
- capture long-range dependency
- efficinet and achieve the best restuls in few layers
- easy to combine with other operation

# Backgroud and Related Work[1](#1)
- 2D or 3D convolutional networks
- Non-local means for image denoising (imporved as BM3D)
- graphical model such as CRF.
- similar to self attention
- Video classfication:

| Architectures | Reference | Advantages |
| :------ |:--- | :--- |
| CNN+RNN | [2](#2),[3](#3) | Learning Sequential Dynamics, Learning Whole Video  |
| C3D | [4](#4),[5](#5),[6](#6),[7](#7) | Combined Spatio and Temporal Features |
| Optical Flow | [8](#8) | Separate Spatial and Temporal Stream|
| Trajectories | [9](#9),[10](#10) | Combined Handcraft and DeepLearning features |

## Notification
{: .box-note}
**Note:** The Comparsion of different architectures [[7](#7)].
![Fig1](https://github.com/Issory/issory.github.io/blob/master/img/2019-05-17-PaperReading-01/Fig1.jpg?raw=true)

# Formulation[1](#1)
$$\mathbf{y}_ i=\frac{1}{\mathcal{C}(x)}\sum\limits_{\forall j}{f(\mathbf{x}_ i,\mathbf{x}_ j)g(\mathbf{x}_ j)}$$
- $f(\mathbf{x}_ i,\mathbf{x}_ j)$ is the affinity matrix between $i$ and $j$.
- $g(\mathbf{x}_ j)$ is the input of position $j$
- $\mathcal{C}(x)$ is the normlization factor

# Variant of Non-local operation
- Generalized Compact Non-Local Module [[11](#11)].([See in Github]())

# Implementation through keras
- The non-local block layers.([See in Github](https://github.com/Issory/non-local-block/blob/master/non-local-layer/non_local.py))
- 

# Reference
1. <span id="1">Xiaolong Wang and Ross Girshick and Abhinav Gupta and Kaiming He. Non-local Neural Networks. In Computer Vision and Pattern Recognition (CVPR), 2018.</span>
The author's project. [See in Github](https://github.com/facebookresearch/video-nonlocal-net) 
2. <span id="2">J. Donahue, L. Anne Hendricks, S. Guadarrama, M. Rohrbach, S. Venugopalan, K. Saenko, and T. Darrell. Long-term recurrent convolutional networks for visual recognition and description. In Computer Vision and Pattern Recognition (CVPR), 2015.</span>
3. <span id="3">J. Yue-Hei Ng, M. Hausknecht, S. Vijayanarasimhan, O. Vinyals, R. Monga, and G. Toderici. Beyond short snippets: Deep networks for video classification. In Computer Vision and Pattern Recognition (CVPR), 2015.</span>
4. <span id="4">S. Ji, W. Xu, M. Yang, and K. Yu. 3d convolutional neural networks for human action recognition. In International Conference on Machine Learning (ICML), 2010.</span>
5. <span id="5">D. Tran, L. Bourdev, R. Fergus, L. Torresani, and M. Paluri. Learning spatiotemporal features with 3d convolutional networks. In International Conference on Computer Vision (ICCV), 2015.</span>
6. <span id="6">C. Feichtenhofer, A. Pinz, and R. Wildes. Spatiotemporal residual networks for video action recognition. In Neural Information Processing Systems (NIPS), 2016.</span>
7. <span id="7">J. Carreira and A. Zisserman. Quo vadis, action recognition? a new model and the kinetics dataset. In Computer Vision and Pattern Recognition (CVPR), 2017.</span>
8. <span id="8">K. Simonyan and A. Zisserman. Two-stream convolutional networks for action recognition in videos. In Neural Information Processing Systems (NIPS), 2014.</span>
9. <span id="9">L. Wang, Y. Qiao, and X. Tang. Action recognition with trajectory-pooled deep-convolutional descriptors. In Computer Vision and Pattern Recognition (CVPR), 2015.</span>
10. <span id="10"> N. Watters, A. Tacchetti, T. Weber, R. Pascanu, P. Battaglia, and D. Zoran. Visual interaction networks. In Neural Information Processing Systems (NIPS), 2017.</span>
11. <span id="11"> K. Yue, M. Sun, Y. Yuan, F. Zhou, Compact generalized non-local network. Advances in Neural Information Processing Systems (NIPS). 2018: 6510-6519.</span>
