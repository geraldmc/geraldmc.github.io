---
layout: post
title: Predicting Crop Yield - Part I
---

![Treatments]({{ site.url }}/assets/sugar_cane.png){:height="200px" width="200px"} 

### Introduction

Here I'm sharing a series of posts that document my experience managing a two-year USDA grant study. This project considers how low-cost vegetation indices like NDVI can be useful additions to a sugarcane farmer's overall nitrogen management strategy. The study was motivated by 1) yearly nitrogen input represents a significant cost to farmers; 2) excessive nitrogen in the environment alters ecosystems and can potentially harm human health. Learning to better manage N application is motivated by the economics of sugarcane agriculture as well as by a need to address environmental issues.  

### Background

Our crop is sugarcane (*Saccharum officinarum*). First introduced into Louisiana in 1751, it is the highest valued row-crop in the state. While recent decades have seen an overall decline in Louisiana sugarcane acreage, crop values have remained stable due to increases in yield. Increased sucrose yield is attributable mainly to the addition of nitrogen fertilizer. Thus, how we manage nitrogen application is relevant both to sugarcane farmers and to everyone else. 
 
### Goals
Our primary goal was to determine to what extent low-cost aerial NDVI and other vegetation indices might correlate with variable N rates applied to sugarcane. A secondary goal was to determine if our analysis might be useful in predicting the yield potential of a future sugarcane crop.

We asked two questions:

* Can variable nitrogen rates be correlated by multi-spectral imagery?

* Are models of acquired multi-spectral imagery predictive of yield?


Our study area was planted and harvested over two successive growing seasons. We used a Latin Square design divided into 30 sections over an area of 1000 by 60 ft. Here is a overview of the study area.

![Study Area]({{ site.url }}/assets/study-area.png){:height="200px" width="850px"} 

As indicated below five levels of nitrogen fertilization (0, 40, 80, 120 and 180 kg·N·ac−1) were applied in a trial setup with six replicates. This gave us 30 plots (100 × 20 sq ft each) making a total trial size of ~1.5 acres.

![Treatments]({{ site.url }}/assets/treatment-grid.png){:height="200px" width="850px"} 

Our study goals 

![NGR Highlight]({{ site.url }}/assets/NGR-highlight-scale.png){:height="225px" width="325px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

<!-- {% highlight python %} {% endhighlight %} -->
<script src="https://gist.github.com/geraldmc/1d3f059a33a30caf73a7f0446892f76f.js"></script>

![NGR Full]({{ site.url }}/assets/NGR-full-view.png){:height="200px" width="850px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![CIR Section 001]({{ site.url }}/assets/2017-04-25_001_3_CIR.png){:height="50px" width="200px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![NDVI Section 001]({{ site.url }}/assets/2017-04-25_001_3_NDVI.png){:height="200px" width="850px"} 


Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.