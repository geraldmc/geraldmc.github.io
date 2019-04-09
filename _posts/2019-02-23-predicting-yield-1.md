---
layout: post
title: Predicting Crop Yields - Part I
---

![Treatments]({{ site.url }}/assets/sugar_cane.png){:height="200px" width="200px"} 

### Introduction

Here are a series of posts documenting my experiences running a two-year USDA grant which considered how low-cost vegetation indices such as NDVI might serve as a useful addition to a sugarcane farmer's overall nitrogen management strategy. This study was motivated because 1) yearly nitrogen input represents a significant cost to farmers while the 'where and when' of nitrogen application remains a guessing game; 2) excessive reactive nitrogen in the environment alters local and global ecosystems and can potentially harm human health. Thus, learning to better manage N application is an important concern motivated by the economics of sugarcane farming as much as by the need to address an acute environmental issue.  

### Background

Our study crop was sugarcane (*Saccharum officinarum*). First introduced into Louisiana in 1751 by the Jesuits, it is the highest valued row-crop in the state. While recent decades have witnessed a overall drop in Louisiana sugarcane acreage, crop values have remained stable due to increases in yield. Increased sucrose yield is attributable mainly to the addition of nitrogen fertilizer. Thus, how we manage nitrogen application is relevant both to sugarcane farmers and to everyone else. 
 
### Goals
Our primary goal was to determine to what extent low-cost aerial NDVI and other vegetation indices might correlate with variable N rates when applied to sugarcane. A secondary goal was to determine to what extent our analysis might be useful for predicting the yield potential of a future sugarcane crop.

We asked two questions:

* How well may variable nitrogen rates in sugarcane be correlated by multi-spectral imagery?

* Are models of acquired multi-spectral imagery predictive of yield?


Our study area was planted and harvested over two successive growing seasons. An area of 1000 by 60 ft was divided in a Latin Square design into 30 sections.

![Study Area]({{ site.url }}/assets/study-area.png){:height="200px" width="850px"} 

As indicated in the image below five levels of nitrogen fertilization (0, 40, 80, 120 and 180 kg·N·ac−1) were applied in a setup with six replicates. This resulted in 30 plots 100 × 20 sq ft each making a total trial size of 1.5 acres.

![Treatments]({{ site.url }}/assets/treatment-grid.png){:height="200px" width="850px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![Nadir View]({{ site.url }}/assets/nadir-view.png){:height="200px" width="850px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![NGR Highlight]({{ site.url }}/assets/NGR-highlight.png){:height="225px" width="400px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

<!-- {% highlight python %} fofofo {% endhighlight %} -->
<script src="https://gist.github.com/geraldmc/1d3f059a33a30caf73a7f0446892f76f.js"></script>


![NGR Full]({{ site.url }}/assets/NGR-full-view.png){:height="200px" width="850px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![CIR Section 001]({{ site.url }}/assets/2017-04-25_001_3_CIR.png){:height="50px" width="200px"} 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

![NDVI Section 001]({{ site.url }}/assets/2017-04-25_001_3_NDVI.png){:height="200px" width="850px"} 


Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.