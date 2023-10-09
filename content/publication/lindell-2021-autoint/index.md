---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/
title: 'AutoInt: Automatic Integration for Fast Neural Volume Rendering'
subtitle: ''
summary: 'A new framework with neural architecture to calculate closed form integrals of functions.'
authors:
- David B Lindell*
- Julien NP Martel*
- Gordon Wetzstein
links:
  - name: Paper (arXiv)  
    url: 'https://arxiv.org/abs/2012.01714'
tags: [ML,Neural Networks, Integration, Volume Rendering, Computed Tomography]
categories: []
date: '2021-06-01'
lastmod: 2020-09-06T21:25:58-07:00
featured: true
draft: false 
    
# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ''
  focal_point: ''
  preview_only: true 

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
publishDate: '2020-09-07T04:25:58.380128Z'
publication_types:
- 2
abstract: 'Numerical integration is a foundational technique in scientific computing and is at the core of many computer 
  vision applications. Among these applications, neural volume rendering has recently been proposed as a new paradigm 
for view synthesis, achieving photorealistic image quality. However, a fundamental obstacle to making these methods 
  practical is the extreme computational and memory requirements caused by the required volume integrations along the
rendered rays during training and inference. Millions of rays, each requiring hundreds of forward passes through
a neural network are needed to approximate those integrations with Monte Carlo sampling. Here, we propose automatic 
  integration, a new framework for learning efficient, closed-form solutions to integrals using coordinate-based neural 
  networks. For training, we instantiate the computational graph corresponding to the derivative of the coordinate-based 
  network. The graph is fitted to the signal to integrate. After optimization, we reassemble the graph to obtain a 
  network that represents the antiderivative. By the fundamental theorem of calculus, this enables the calculation of 
  any definite integral in two evaluations of the network. Applying this approach to neural rendering, we improve a 
  tradeoff between rendering speed and image quality: improving render times by greater than 10× with a tradeoff of 
  slightly reduced image quality.'
publication: '*IEEE/CVF Computer Vision and Pattern Recognition (CVPR 2021)*'
---
## Videos
### Technical Video (7 min)
<iframe width="640" height="480" src="https://www.youtube.com/embed/GYxFYbih0PU" title="YouTube video player" 
frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
allowfullscreen></iframe>

## The AutoInt Framework 
### Principle
After (1) defining an integral network architecture, (2) AutoInt builds the corresponding grad 
network, which is (3) optimized to represent a function. (4) Definite integrals can then be computed by evaluating the 
integral network, which shares parameters with its grad network.
![](a1.png)

### Volume rendering pipeline 
During training, the grad networks representing volume density σ and color c are optimized for a given set of multi-view 
images (top left). For inference, the grad networks’ parameters are reassembled to form the integral networks,
which represent antiderivatives that can be efficiently evaluated to calculate ray integrals through the volume 
(bottom left). A sampling network predicts the locations of piecewise sections used for evaluating the definite 
integrals (right).
![](a2.png)

## Results
### Sparse View Computed Tomography
Left: illustration of the parameterization. Center: sinograms computed with the integral networks using different 
nonlinear activation functions. The ground truth (GT) sinogram is subsampled in angle by 4× (top), 8× (middle), and 16× 
(bottom). The optimized networks are used to interpolate the missing measurements. Using the Swish activation performs 
best in these experiments. Right: 1D scanlines of the sinogram centers shows the interpolation behavior of each method 
for each subsampling level.
![](a3.png)

### Volume rendering 
{{<video autoplay="true" loop="true" src="a4.mp4">}}
{{<video autoplay="true" loop="true" src="a5.mp4">}}
{{<video autoplay="true" loop="true" src="a6.mp4">}}

## On Twitter
{{< tweet 1334943306673922048 >}}
