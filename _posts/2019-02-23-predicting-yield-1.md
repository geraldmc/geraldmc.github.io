---
layout: post
title: Predicting Crop Yield - Part I
---

![Treatments]({{ site.url }}/assets/sugar_cane.png){:height="200px" width="200px"} 

### Introduction

Here I'm sharing a series of posts that document my experience managing a two-year USDA grant study. This project considers how low-cost vegetation indices like NDVI may be useful additions to a sugarcane farmer's overall nitrogen management strategy. The study was motivated by 1) yearly nitrogen input represents a significant cost to farmers; 2) excessive nitrogen in the environment alters ecosystems and may potentially harm human health. Learning to better manage N application is motivated by the economics of sugarcane agriculture as well as by a need to address an environmental issue. Some posts will include references to the software used and the code developed to derive our final results.   

### Background

Our crop is sugarcane (*Saccharum officinarum*). First introduced into Louisiana in 1751 it is the highest valued row-crop in the state. While recent decades have seen a decline in Louisiana sugarcane acreage, crop values have remained stable due to increases in yield. Increased sucrose yield is attributable mainly to the addition of nitrogen fertilizer. Thus, how we manage nitrogen application is relevant to sugarcane farmers (economics) and to everyone else (environment). 
 
### Goals
Our primary goal was to determine whether low-cost aerial NDVI and related vegetation indices would correlate with variable N rates when applied to sugarcane. A secondary goal was to determine if such an analysis might be useful for predicting the yield potential of a future crop.

We asked two questions:

* Can variable nitrogen rates be correlated with multi-spectral imagery?

* Are models of acquired multi-spectral imagery predictive of yield?


Our study area was planted and harvested over two successive seasons. We used a Latin Square design divided into 30 sections over an area of 1000 by 60 ft. Here is a overview of the study area.

![Study Area]({{ site.url }}/assets/study-area.png){:height="200px" width="850px"} 

As indicated below five levels of nitrogen fertilization (0, 40, 80, 120 and 180 kg·N·ac−1) were applied in a trial setup with six replicates. This gave us 30 plots (100 × 20 sq ft each) making a total trial size of ~1.5 acres.

![Treatments]({{ site.url }}/assets/treatment-grid.png){:height="200px" width="850px"} 

Creating a vegetation index requires first getting a camera into the air and as we progressed we used kites, then balloons and ultimately an unassisted aerial drone (UAV). We [created our own multi-spectral cameras](https://publiclab.org/wiki/near-infrared-camera) along with the rigs needed to reproducibly fly them. Ultimately we got some help from the folks at Micasense and used their multi-spectral camera, the Sequoia:

![NGR Highlight]({{ site.url }}/assets/parrot-sequoia-camera.png){:height="325px" width="325px"}

The Sequoia camera is about the size of a GoPro. It’s lightweight enough to serve as payload on a consumer-style drone such as the one we selected (a 3DR Solo). Flying the camera over a field allowed us to collect light reflecting from the leaves of the field in a very specific way. As the image indicates the Sequoia collects light in the Green, Red, Near-infrared and [RedEdge](https://en.wikipedia.org/wiki/Red_edge) bands. By manipulating these various bands we were able to create different kinds of vegetation index, one of which is known as an NRG index. Most or us are familiar with RGB images but in an NRG image the RGB (Red-Green-Blue) colors are swapped out for a different, the NIR (Near-infrared), the Red and the Green.

![NGR Highlight]({{ site.url }}/assets/NGR-highlight-scale.png){:height="250px" width="300px"}

<!-- {% highlight python %} {% endhighlight %} -->
<script src="https://gist.github.com/geraldmc/1d3f059a33a30caf73a7f0446892f76f.js"></script>

![NGR Full]({{ site.url }}/assets/NGR-full-view.png){:height="200px" width="850px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![CIR Section 001]({{ site.url }}/assets/2017-04-25_001_3_CIR.png){:height="50px" width="200px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![NDVI Section 001]({{ site.url }}/assets/2017-04-25_001_3_NDVI.png){:height="200px" width="850px"} 


Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.