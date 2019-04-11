---
layout: post
title: Predicting Crop Yield - Part I
---

![Treatments]({{ site.url }}/assets/sugar_cane.png){:height="200px" width="200px"} 

### Introduction

Here I'm sharing a series of posts that document my experience with a two-year USDA grant study. The project considered how low-cost vegetation indices like NDVI might be a useful addition to a sugarcane farmer's overall nitrogen management strategy. The study was motivated by 1) yearly nitrogen input represents a significant cost to farmers; 2) excessive nitrogen in the environment alters ecosystems and may potentially harm human health. Thus, learning to manage N application better is motivated by the economics of sugarcane agriculture as well as by a need to address an environmental issue. Some of what follows will include reference to the software packages used along with code developed in deriving our results.   

### Background

Our crop is sugarcane (*Saccharum officinarum*). First introduced into Louisiana in 1751 it is the highest valued row-crop in the state. While recent decades have seen a decline in Louisiana sugarcane acreage, crop values have remained stable due to increases in yield. Increased sucrose yield is attributable mainly to the addition of nitrogen fertilizer. Thus, how we manage nitrogen application is relevant to farmers (the economics) and to everyone else (the environment). 
 
### Goals
Our primary goal was to determine whether low-cost aerial NDVI and other indices would correlate with variable N rates when applied to sugarcane. A secondary goal was to determine if such analysis might be useful for predicting the yield potential of a future crop. In addition, our work was carried out with the intention of revealing techniques that are affordable, accessible and, most of all, *effective*.

We asked two questions:

* Can variable nitrogen rates be correlated with multi-spectral imagery?

* Are models of acquired multi-spectral imagery predictive of yield?


 To that end our study area was planted and harvested over two successive seasons. We used a Latin Square design divided into 30 sections over an area of 1200 by 60 ft. Here is a overview of the area.

![Study Area]({{ site.url }}/assets/study-area.png){:height="200px" width="850px"} 

As indicated below five levels of nitrogen fertilization (0, 40, 80, 120 and 180 kg·N·ac−1) were applied in a trial setup with six replicates. This gave us 30 plots (100 × 20 sq ft each) making a total trial size of ~1.5 acres.
<br />  
![Treatments]({{ site.url }}/assets/treatment-grid.png){:height="200px" width="850px"} 
<br />  

Creating a vegetation index requires getting a camera into the air and as we progressed we used kites, then balloons and ultimately an unassisted aerial drone (UAV). We [created our own multi-spectral cameras](https://publiclab.org/wiki/near-infrared-camera) along with the rigs needed to reproducibly fly them. Ultimately we got some help from the folks at Micasense and used their multi-spectral camera, the Sequoia:

![NGR Highlight]({{ site.url }}/assets/parrot-sequoia-camera.png){:height="225px" width="225px"}

The Sequoia is about the size of a GoPro. It’s lightweight enough to serve as payload on a consumer-style drone such as the one we selected (a 3DR Solo). Flying the camera over a field allowed us to collect light reflected from the stalks and leaves of sugarcane in a very specific way. As the image indicates the Sequoia collects light in the Green, Red, Near-infrared and [RedEdge](https://en.wikipedia.org/wiki/Red_edge). By manipulating these separate bands we were able to create different kinds of vegetation indices, one of which is known as an NRG index. While most are familiar with *RGB* images in an NRG image the RGB colors (Red-Green-Blue) are swapped for a different set, NIR (Near-infrared), the Red and the Green.

![NGR Highlight]({{ site.url }}/assets/NGR-highlight-scale.png){:height="275px" width="425px"}

The image above shows a composite NRG taken on a clear day in late April, 2018. It's composed of many smaller images in a process known as image-stitching. The two rectangles in yellow are test plots. The green square highlights my white Jetta and me. The image below (from 2016) show the result of stitching a dozen or so images from a balloon flight. We got better at it over time! 

![NGR Highlight]({{ site.url }}/assets/map-stitch.gif){:height="275px" width="425px"}
<br />  

While the work of this grant involved long days in a cane field gathering data it also required time in front of a computer screen to make sense of it. The following is a snippet of code used to separate each band of light from an original 'raw' data file produced by the Sequoia camera. This is part of a larger image-processing pipeline developed to automate the work.
<br />  

<!-- {% highlight python %} {% endhighlight %} -->
<script src="https://gist.github.com/geraldmc/1d3f059a33a30caf73a7f0446892f76f.js"></script>
<br />  

The process of stitching together hundreds of small images, separating the individual bands and running simple computational methods results in an image of the full study area (below). This image (acquired on July 28th, 2017) shows the complete grid of test plots as an NRG index at the height of the growing season. I recall it was plenty hot that day!

![NGR Full]({{ site.url }}/assets/NGR-full-view.png){:height="200px" width="850px"} 

Two things to notice: my car appears twice in the image - once in the upper-left and again at the far-right. Since the area was too long (1200ft) to be covered by a single flight it had to be flown twice for each capture - once for the left half and once for the right. I would set up one side, fly the mission over half, pack everything up and drive to the other side. Consumer drones drain batteries too fast!

A more interesting thing revealed are the shades of red in different parts of the grid. Earlier I mentioned how we treated separate sections of the area (each about 100 ft by 20 ft, where a single row is roughly 6 feet wide) with a different amount of N fertilizer. The shades of red signify different intensities of near-infrared light reflected from each section. The treatment of 0 kg·N·ac−1 (#1 in the colored grid at the start of this post) appears as a pattern and that pattern is visible here. The image reveals that differing amounts of nitrogen fertilizer applied to different sections are discernable in terms of the amount of NIR light they reflect. In the next post I'll explain why.    

<br />  
![CIR Section 001]({{ site.url }}/assets/2017-04-25_001_3_CIR.png){:height="50px" width="200px"} 

Before moving on I show an image of a single treated section. After going to the trouble of accurately stitching hundreds of images we cut that larger one up precisely into smaller samples. The section above represents a single treatment gathered on a specific day during the sugarcane growing season from late April to mid-November. Ultimately more than a dozen useable samples per treatment from this field were captured, each spaced as evenly as weather permitted beginning at one week prior to fertilizing up until four days before harvest.