---
layout: post
title: Predicting Crop Yield From The Sky
---

![Treatments]({{ site.url }}/assets/sugar_cane.png){:height="200px" width="200px"} 

### Introduction

I'm sharing a series of posts that document my experiences running a two-year agricultural research grant. This project was funded through the Sustainable Agriculture Research and Education (SARE) section of USDA and considered the application and use of low-cost vegetation indices such as NDVI (more on that later). It was motivated by two important issues in sugarcane farming: 1) seasonal nitrogen input represents a significant cost to farmers; 2) excess nitrogen in the environment alters ecosystems and potentially harms human health. Learning how to manage nitrogen application better is thus motivated by the economics of sugarcane agriculture as well as by the need to address an ongoing environmental issue. For all you agri-geeks out there some of what follows includes reference to the software and code we used to develop and derive our results.

### Background

Our crop is sugarcane (*Saccharum officinarum*). First introduced in the Americas in 1751 it is the highest valued row-crop in the state of Louisiana. While recent years have witnessed a decline in overall sugarcane acreage, crop values have remained generally stable due to increases in yield. Increased yield is attributable mainly to the addition of nitrogen fertilizer. Thus, how we manage N application is relevant to farmers (in terms of the economics) and to everyone else (in terms of the environment). 
 
### Goals
During our study the goal was to determine whether low-cost aerial NDVI and other indices like it could accurately correlate with variable N rates when applied to sugarcane. A secondary goal was to determine if such analysis was useful in predicting the yield potential of a future crop. Our work was carried out with the intention of revealing techniques that are affordable, accessible to ordinary farmers and, most importantly, *effective*.

We asked two questions:

* Can variable nitrogen rates be correlated with multi-spectral imagery?

* Are models of acquired multi-spectral imagery predictive of yield?


 To answers these questions a study area was set aside, planted and harvested over two successive seasons. We used a Latin Square design divided into 30 sections over an area of 1200 by 60 ft. Here is a overview of the area located on our farm in Houma, LA.

![Study Area]({{ site.url }}/assets/study-area.png){:height="200px" width="850px"} 

As indicated below five levels of nitrogen fertilization (0, 40, 80, 120 and 180 kg·N·ac−1) were applied in a trial setup with six replicates. This gave us 30 individual plots (100 × 20 sq ft each) making a total trial size of ~1.5 acres.
<br />  
![Treatments]({{ site.url }}/assets/treatment-grid.png){:height="200px" width="850px"} 
<br />  

### Tools

Creating a vegetation index requires getting a camera into the air and keeping it there. As we progressed we used kites, balloons and ultimately an unassisted aerial vehicle (a drone). We [created our own multi-spectral cameras](https://publiclab.org/wiki/near-infrared-camera) along with rigs needed to reproducibly fly them. Ultimately we got help from the folks at [Micasense](https://www.micasense.com/) and used their multi-spectral camera, the Sequoia:

![NGR Highlight]({{ site.url }}/assets/parrot-sequoia-camera.png){:height="225px" width="225px"}

The Sequoia is about the size of a GoPro. It’s a lightweight payload for a consumer-style drone such as the one we selected (a 3DR Solo). Flying this camera over a field allowed us to collect light reflected from sugarcane in a variety of specific ways. The Sequoia collects light in the Green, Red, Near-infrared and [RedEdge](https://en.wikipedia.org/wiki/Red_edge) bands. By manipulating these bands we were able to create different vegetation indices, one of which is known as the NRG. Most are familiar with RGB images but in an NRG image the RGB colors (Red-Green-Blue) are swapped for a different set: NIR (Near-infrared), Red and the Green. Here is an example NRG image.

![NGR Highlight]({{ site.url }}/assets/NGR-highlight-scale.png){:height="275px" width="425px"}

The image above is a composite NRG taken on a clear day in late October, 2018. It's made up of many smaller images in a process involving orthorectification and image-stitching. The two yellow rectangles are test plots. The green square highlights my white Jetta (and me). 

### Data

The work of this grant involved long days in a cane field gathering data but it also required time in front of a computer making sense of that data. The following is a snippet of code used to separate each band of light from an original 'raw' data file produced by the Sequoia camera. This is part of a larger image-processing pipeline developed to automate the work.
<br />  

<!-- {% highlight python %} {% endhighlight %} -->
<script src="https://gist.github.com/geraldmc/1d3f059a33a30caf73a7f0446892f76f.js"></script>
<br />  

The process of stitching together hundreds of smaller images, separating the individual bands, and running computational methods over the results ultimately provides an image of the full study area (below). This image (acquired on July 28th, 2017) shows the complete grid of test plots as an NRG at the height of the growing season.

![NGR Full]({{ site.url }}/assets/NGR-full-view.png){:height="200px" width="850px"} 

A funny thing to notice: my car appears twice in the image - once in the upper-left and again at the far-right. The study area was too long (1200ft) to be covered by a single flight thus it had to be flown twice during each capture - once for the left half and once for the right. I would set up one side, fly the mission, pack everything up and drive to the other side.

A more interesting observation is revealed in shades of red over different parts of the grid. Earlier I mentioned how we treated separate sections of the area (each about 100 ft by 20 ft, where a single row is roughly 6 feet wide) with a different amount of N fertilizer. The varying shades of red signify different intensities of near-infrared light reflecting from each section. The treatment of 0 kg·N·ac−1 (#1 in the colored grid at the start of this post) appears as a pattern and that pattern is visible here. The image reveals that differing amounts of nitrogen fertilizer applied to different sections are discernable in terms of the amount of NIR light they reflect. In the next post I'll explain why.    

### Datum

![CIR Section 001]({{ site.url }}/assets/2017-04-25_001_3_CIR.png){:height="50px" width="200px"} 

Before moving on I show an image of a single treated section. After going to the trouble of  stitching hundreds of images we needed to cut that larger image up into smaller samples. The section above represents a single treatment sample gathered on a specific day during the sugarcane growing season (from late April to mid-November). Ultimately, more than a dozen useable samples per treatment from this field were captured. Each is spaced in time as evenly as weather permitted, starting one week prior to fertilization and ending four days before harvest.