---
layout: post
title: Data Science of Connectomes
---

A `connectome` is a wiring diagram of connections between neurons ranging in scale from a limited set of cells and synapses to larger structural and functional points of connectivity between regions of the brain. Broadly speaking, the term `connectomics` describes the effort to map and ultimately comprehend the vast organizational complexity of neural interactions in the brain. The terms connectome and connectomics were first coined by [Olaf Sporns](https://en.wikipedia.org/wiki/Olaf_Sporns) in 2005.

### Pennies from Heaven

The human brain holds roughly <strong>$${10^{11}}$$</strong> or 100 billion neurons. Each has on average 7,000 synapses making the number of potential links between elements on the order of $${10^{15}}$$ or`one quadrillion`. To give an idea of what a quadrillion looks like:

![1 quadrillion]({{ site.url }}/assets/quadrillion_pennies.jpg)

This is a cube of copper pennies 2,730 feet long on each side. The smaller cube (next to the Empire State Building) represents 1 trillion pennies. (See [The MegaPenny Project](http://www.kokogiak.com/megapenny/default.asp)). 

Current estimates of brain connectivity often fail to take into account the non-static nature of the brain's functional makeup. The brain possesses an extraordinary ability to modify its  structure and function in response to change, both as the result of external events and in accordance with the organism's innate developmental blueprint. 

Mapping networks at the level of connections got its start way back in the 70s with the study of the roundworm`C.Elegans`. More recently the field of connectomics has seen rapid rise in part due to computational advances that allow for the semi-automated collection and analysis of previously unheard of volumes of data. Here I describe some of the challenges that arise when managing and modeling connectome data and provide suggestions for how to manage these.

---

### Elegant Worms 

![C.Elegans]({{ site.url }}/assets/CrawlingCelegans.gif) [![C.Elegans]({{ site.url }}/assets/by-sa.png){:height="15px" width="45px"}](http://labs.bio.unc.edu/Goldstein/movies.html)

_Caenorhabditis elegans_ is a nematode roundworm, generally slender and circular in cross section. It is non-pathogenic and grows to about 1 mm in length. While C. elegans is about as primitive an organism as can be, it shares many essential characteristics relevant to the study of human biology, in particular to human neurobiology.

By far the most complex organ in C. elegans is its nervous system. Of a total of 959 cells, 301 in C. elegans are neuronal. 20 of these are located in the organism's pharynx (which has its own nervous system). The remaining 281 make up its various head and tail ganglia along with additional ganglia running along its main longitudinal axis.

As a species, C.elegans is remarkably consistent in terms of its anatomical structure, especially with regard to the number and placement of neurons in its nervous system. That is to say, the neurons of one particular C. elegans is remarkably consistent - is in fact identical - to that of any other C. elegans. Such consistency has allowed researchers to amass a large and increasingly accurate portrait of C. elegans systems biology over time. Furthermore, all of this information is available to whomever is interested in it (though you still have to search for it).

Constancy of cell number and of cell position from individual to individual eutely

---
