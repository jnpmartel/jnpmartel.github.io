---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/
title: 'Implicit Neural Representations with Periodic Activation Functions'
subtitle: ''
summary: 'A neural signal representation for images, audio, shapes, and wavefields.'
authors:
- Vincent Sitzmann*
- Julien NP Martel*
- Alexander W Bergman
- David B Lindell
- Gordon Wetzstein
links:
  - name: Paper (publisher) 
    url: 'https://arxiv.org/abs/2006.09661'
  - name: Code Repository
    url: 'https://github.com/vsitzmann/siren'
  - name: Colab Notebook 
    url: 'https://colab.research.google.com/github/vsitzmann/siren/blob/master/explore_siren.ipynb'
  - name: Tensorflow Playground
    url: 'https://dcato98.github.io/playground/#activation=sine&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.17014&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false'
  - name: Data
    url: 'https://drive.google.com/drive/u/1/folders/1_iq__37-hw7FJOEUK1tX7mdp8SKB368K'
tags: [Machine Learning, Deep Learning, Implicit Representation, Boundary Value Problems]
categories: []
date: '2020-12-01'
lastmod: 2020-09-02T18:10:31-07:00
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
publishDate: '2020-09-03T01:10:31.778674Z'
publication_types:
- 1
abstract: ' Implicitly defined, continuous, differentiable signal representations parameterized by neural networks have 
emerged as a powerful paradigm, offering many possible benefits over conventional representations. However, current 
network architectures for such implicit neural representations are incapable of modeling signals with fine detail, and 
fail to represent a signal’s spatial and temporal derivatives, despite the fact that these are essential to many 
physical signals defined implicitly as the solution to partial differential equations. We propose to leverage periodic 
activation functions for implicit neural representations and demonstrate that these networks, dubbed sinusoidal 
representation networks or SIREN, are ideally suited for representing complex natural signals and their derivatives. 
We analyze SIREN activation statistics to propose a principled initialization scheme and demonstrate the representation 
of images, wavefields, video, sound, and their derivatives. Further, we show how SIREN s can be leveraged to solve 
challenging boundary value problems, such as particular Eikonal equations (yielding signed distance functions), the 
Poisson equation, and the Helmholtz and wave equations. Lastly, we combine SIREN with hypernetworks to learn priors over 
the space of SIREN functions. '
publication: '*Neural Information and Processing Systems (NeurIPS 2020)*'
---
## Videos
### Technical video (10:30 min)
<iframe width="640" height="480" src="https://www.youtube.com/embed/Q2fLWGBeaiI" title="YouTube video player" 
frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
allowfullscreen></iframe>

### NeurIPS talk (10:30 min)

## Using SIRENs to represent signals
### Representing images
A Siren that maps 2D pixel coordinates to a color may be used to parameterize images. Here, we supervise Siren directly
with ground-truth pixel values. Siren not only fits the image with a 10 dB higher PSNR and in significantly fewer 
iterations than all baseline architectures, but is also the only MLP that accurately represents the first- and second
order derivatives of the image.
{{<video src="s1.mp4">}}
{{<video src="s1bis.mp4">}}

### Representing audio
A Siren with a single, time-coordinate input and scalar output may parameterize audio signals. Siren is the only
network architecture that succeeds in reproducing the audio signal, both for music and human voice. 
<div class="row justify-content-left">
            <div class="col-sm-3">
                <h5>Ground truth</h5>
                <img src="audio/gt_bach.png" style="width:100%">
                <audio
                        controls
                        src="audio/gt_bach.wav"
                        class="media-left"
                        style="width:100%">
                    Your browser does not support the
                    <code>audio</code> element.
                </audio>
            </div>
            <div class="col-sm-3">
                <h5>ReLU MLP</h5>
                <img src="audio/relu_bach.png" style="width:100%">
                <audio
                        controls
                        src="audio/relu_bach.wav"
                        class="media-left"
                        style="width:100%">
                    Your browser does not support the
                    <code>audio</code> element.
                </audio>
            </div>
            <div class="col-sm-3">
                <h5>ReLU P.E.</h5>
                <img src="audio/relu_pe_bach.png" style="width:100%">
                <audio
                        controls
                        src="audio/relu_pe_bach.wav"
                        class="media-left"
                        style="width:100%">
                    Your browser does not support the
                    <code>audio</code> element.
                </audio>
            </div>
            <div class="col-sm-3">
                <h5>Siren</h5>
                <img src="audio/siren_bach.png" style="width:100%">
                <audio
                        controls
                        src="audio/siren_bach.wav"
                        class="media-left"
                        style="width:100%">
                    Your browser does not support the
                    <code>audio</code> element.
                </audio>
            </div>
            <div class="row justify-content-left">
                <div class="col-sm-3">
                    <img src="audio/gt_counting.png" style="width:100%">
                    <audio
                            controls
                            src="audio/gt_counting.wav"
                            class="media-left"
                            style="width:100%">
                        Your browser does not support the
                        <code>audio</code> element.
                    </audio>
                </div>
                <div class="col-sm-3">
                    <img src="audio/relu_counting.png" style="width:100%">
                    <audio
                            controls
                            src="audio/relu_counting.wav"
                            class="media-left"
                            style="width:100%">
                        Your browser does not support the
                        <code>audio</code> element.
                    </audio>
                </div>
                <div class="col-sm-3">
                    <img src="audio/relu_pe_counting.png" style="width:100%">
                    <audio
                            controls
                            src="audio/relu_pe_counting.wav"
                            class="media-left"
                            style="width:100%">
                        Your browser does not support the
                        <code>audio</code> element.
                    </audio>
                </div>
                <div class="col-sm-3">
                    <img src="audio/siren_counting.png" style="width:100%">
                    <audio
                            controls
                            src="audio/siren_counting.wav"
                            class="media-left"
                            style="width:100%">
                        Your browser does not support the
                        <code>audio</code> element.
                    </audio>
                </div>
        </div>
    </div>

### Representing videos
A Siren with pixel coordinates together with a time coordinate can be used to parameterize a video. Here, Siren is 
directly supervised with the ground-truth pixel values, and parameterizes video significantly better than a ReLU MLP. 
{{<video src="s2.mp4">}}
{{<video src="s3.mp4">}}

## Using SIRENs to solve PDEs
### Poisson equation 
By supervising only the derivatives of Siren, we can solve Poisson's equation. Siren is again the only architecture
that fits image, gradient, and laplacian domains accurately and swiftly. 
{{<video autoplay="true" loop="true" preload="true" src="s4.mp4">}}
{{<video autoplay="true" loop="true" preload="true" src="s4bis.mp4">}}

### Eikonal equation: representing shapes
We can recover an SDF from a pointcloud and surface normals by solving the Eikonal equation, a first-order boundary 
value problem. SIREN can recover a room-scale scene given only its pointcloud and surface normals, accurately 
reproducing fine detail, in less than an hour of training. In contrast to recent work on combining voxel grids with 
neural implicit representations, this stores the full scene in the weights of a single, 5-layer neural network, with 
no 2D or 3D convolutions, and orders of magnitude fewer parameters. Zoom in to compare fine detail! Note that these 
SDFs are not supervised with ground-truth SDF / occupancy values, but rather, are the result of solving the above 
Eikonal boundary value problem. This is a significantly harder task, which requires supervision in the gradient domain 
(see paper). As a result, architectures whose gradients are not well-behaved perform worse than SIREN.
<script type="module" src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"></script>
<div class="container">
            <div class="row align-items-center">
                <div class="col-md-6 padding-0 canvas-row">
                    <h4>Room - Siren</h4>
                    <model-viewer
                            alt="Room Siren"
                            src="room_siren.glb"
                            style="width: 100%; height:300px; background-color: #404040"
                            exposure=".8"
                            camera-orbit="0deg 75deg 105%"
                            auto-rotate
                            camera-controls>
                    </model-viewer>
                </div>
                <div class="col-md-6 padding-0 canvas-row">
                    <h4>Room - ReLU</h4>
                    <model-viewer
                            alt="Room ReLU"
                            src="room_relu.glb"
                            style="width: 100%; height: 300px; background-color: #404040"
                            exposure=".8"
                            auto-rotate
                            camera-controls>
                    </model-viewer>
                    <!--                            poster="https://uploads-ssl.webflow.com/51e0d73d83d06baa7a00000f/5e7e6db2d75a9b467eee4111_legomesh_cover.png"-->
                </div>
            </div>
            <div class="row align-items-center">
                <div class="col-md-4 padding-0 canvas-row">
                    <h4>Statue - Siren</h4>
                    <model-viewer
                            alt="Statue Siren"
                            src="statue_siren.glb"
                            style="width: 100%; height: 600px; background-color: #404040"
                            exposure=".8"
                            camera-orbit="0deg 75deg 20%"
                            auto-rotate
                            camera-controls>
                    </model-viewer>
                </div>
                <div class="col-md-4 padding-0 canvas-row">
                    <h4>Statue - ReLU Pos. Enc.</h4>
                    <model-viewer
                            alt="Statue Positional Encoding"
                            src="statue_relu_pe.glb"
                            style="width: 100%; height: 600px; background-color: #404040"
                            exposure=".8"
                            camera-orbit="0deg 75deg 20%"
                            auto-rotate
                            camera-controls>
                    </model-viewer>
                </div>
                <div class="col-md-4 padding-0 canvas-row">
                    <h4>Statue - ReLU</h4>
                    <model-viewer
                            alt="Statue ReLU"
                            src="statue_relu.glb"
                            style="width: 100%; height: 600px; background-color: #404040"
                            exposure=".8"
                            camera-orbit="0deg 75deg 20%"
                            auto-rotate
                            camera-controls>
                    </model-viewer>
                </div>
            </div>
        </div>

### Hemlmholtz equation
Here, we use Siren to solve the inhomogeneous Helmholtz equation. ReLU- and Tanh-based architectures fail entirely to 
converge to a solution. 
{{<video autoplay="true" loop="true" src="s5.mp4">}}

### Wave equation
In the time domain, Siren succeeds to solve the wave equation, while a Tanh-based architecture fails to discover the 
correct solution.
{{<video autoplay="true" loop="true" src="s6.mp4">}}

## On Twitter
{{< tweet 1273409377395859456 >}}
{{< tweet 1273686900285603843 >}}
{{< tweet 1274692264611196934 >}}
