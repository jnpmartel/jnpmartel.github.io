---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: 'Neural Sensors: Learning Pixel Exposures for HDR Imaging and Video Compressive
  Sensing with Programmable Sensors'
subtitle: ''
summary: 'We optimize the shutter function of a programmable sensor for each pixel individually to produce coded 
snapshots that can be reconstructed into HDR images and high-speed videos.'
authors:
- Julien NP Martel
- Lorenz Mueller
- Stephen J Carey
- Piotr Dudek
- Gordon Wetzstein
links:
  - name: Paper (publisher)  
    url: 'https://ieeexplore.ieee.org/document/9064896'
tags: [Machine Learning, Deep Learning, Vision Sensor, Focal Plane Sensor Processor, HDR, Compressive Sensing, High 
Frame Rate, SCAMP]
categories: []
date: '2020-07-01'
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
publishDate: '2020-09-03T01:10:31.867701Z'
publication_types:
- 2
abstract: 'Camera sensors rely on global or rolling shutter functions to expose an image. This fixed function approach 
severely limits the sensors’ ability to capture high-dynamic-range (HDR) scenes and resolve high-speed dynamics. 
Spatially varying pixel exposures have been introduced as a powerful computational photography approach to optically 
encode irradiance on a sensor and computationally recover additional information of a scene, but existing approaches
rely on heuristic coding schemes and bulky spatial light modulators to optically implement these exposure functions. 
Here, we introduce neural sensors as a methodology to optimize per-pixel shutter functions jointly with a differentiable
image processing method, such as a neural network, in an end-to-end fashion. Moreover, we demonstrate how to leverage 
emerging programmable and re-configurable sensor–processors to implement the optimized exposure functions directly on 
the sensor. Our system takes specific limitations of the sensor into account to optimize physically feasible optical 
codes and we demonstrate state-of-the-art performance for HDR and high-speed compressive imaging in simulation and with 
experimental results.'
publication: '*IEEE Transactions on Pattern Analysis and Machine Intelligence*'
---

## Videos
### ICCP talk (12 min)
<iframe width="640" height="480" src="https://www.youtube.com/embed/tTYHoxA2RVg"
title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write;
encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## System overview
![System Overview](system.png)
### Illustration of our end-to-end neural sensor framework.
The exposure program of a sensor (physical layer) is learned end-to-end with a decoder (digital layer) for applications 
like video compressive sensing. Here, we show a single coded exposure captured with our prototype camera and several 
frames of the high-speed video reconstructed from this image showing an exploding balloon.

### Hardware Setup
<table style="table-layout: fixed; border: none;" width="788">
<tbody>
<tr style="border: none;">
<td style="border: none; vertical-align: top;"><img src="hardware.png"></td>
<td style="border: none; vertical-align: middle;">Real captures of the coded images using the optimized shutter functions 
are performed with SCAMP-5, a programmable sensor processor.</p>
<p>SCAMP-5 is a 256&#215;256 pixel array in which each pixel is equipped with a small processor and a few registers.</td>
</tr>
</tbody>
</table>

## Results: real captures
<table style="padding: 1px 1px 1px 1px;" width="788">
<tbody>
<tr>
<th style="text-align: center;">Coded Exposure Image</th>
<th style="text-align: center;">Reconstructed Video</th>
</tr>
<tr>
<td style="text-align: center;" colspan="2"><strong>Water Droplet </strong><em>(video contains 64 total frames from 4 coded frames)</em></td>
</tr>
<tr>
<td style="text-align: center;"><img src="c1.png"></td>
<td style="text-align: center;"><img src="r1.gif"></td>
</tr>
<tr>
<td style="text-align: center;" colspan="2"><strong>Rotating Fan</strong> <em>(video contains 64 total frames from 4 coded frames)</em></td>
</tr>
<tr>
<td style="text-align: center;"><img src="c2.png"></td>
<td style="text-align: center;"><img src="r2.gif"></td>
</tr>
<tr>
<td style="text-align: center;" colspan="2"><strong>Jumping Frog </strong><em>(video contains 64 total frames from 4 coded frames)</em></td>
</tr>
<tr>
<td style="text-align: center;"><img src="c3.png"></td>
<td style="text-align: center;"><img src="r3.gif"></td>
</tr>
<tr>
<td style="text-align: center;" colspan="2"><strong>Oscilloscope </strong>(<em>video contains 16 total frames from 1 coded frame)</em></td>
</tr>
<tr>
<td style="text-align: center;"><img src="c4.png"></td>
<td style="text-align: center;"><img src="r4.gif"></td>
</tr>
<tr>
<td style="text-align: center;" colspan="2"><strong>Balloon</strong> <em>(video contains 32 total frames from 2 coded frames)</em></td>
</tr>
<td style="text-align: center;"><img src="c5.png"></td>
<td style="text-align: center;"><img src="r5.gif"></td>
<tr>
</tr>
</tbody>
</table>

## On Twitter
{{< tweet 1291411126538743809 >}}


