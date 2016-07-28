---
layout: post
title: Data Science of Connectomes
---

A `connectome` is a wiring diagram of connections between neurons ranging in scale from a limited set of cells and synapses to larger structural and functional points of connectivity between regions of the brain. Broadly speaking, the term `connectomics` describes the effort to map and ultimately comprehend the vast organizational complexity of neural interactions in the brain. The terms connectome and connectomics were first coined by [Olaf Sporns](https://en.wikipedia.org/wiki/Olaf_Sporns) in 2005.

### Pennies from Heaven

The human brain holds roughly <strong>$${10^{11}}$$</strong> or 100 billion neurons. Each has on average 7,000 synapses making the number of potential links between elements on the order of $${10^{15}}$$ or`one quadrillion`. To give an idea of what a quadrillion looks like:

![1 quadrillion]({{ site.url }}/assets/quadrillion_pennies.jpg){:height="350px" width="370px"}

This is a cube of copper pennies 2,730 feet long on each side. The smaller cube (next to the Empire State Building) represents 1 trillion pennies. (See [The MegaPenny Project](http://www.kokogiak.com/megapenny/default.asp)). 

Current estimates of brain connectivity often fail to take into account the brain's mercurial makeup. The brain possesses an extraordinary ability to modify its own structure and function in response to change, both as the result of external events and in accordance with the organism's innate developmental blueprint. 

Mapping networks at the level of connections got its start way back in the 70s with the study of the roundworm`C.Elegans`. More recently the field of connectomics has seen rapid rise in part due to computational advances that allow for the semi-automated collection and analysis of previously unheard of volumes of data. Here I describe some of the challenges that arise when managing and modeling connectome data.

---

### Elegant Worms 

![C.Elegans]({{ site.url }}/assets/CrawlingCelegans.gif) [![C.Elegans]({{ site.url }}/assets/by-sa.png){:height="15px" width="45px"}](http://labs.bio.unc.edu/Goldstein/movies.html)

_Caenorhabditis elegans_ is a nematode roundworm, generally slender and circular in cross section. It is non-pathogenic and grows to about 1 mm in length. While C. elegans is about as primitive an organism as can be, it shares many essential characteristics relevant to the study of human biology, in particular to human neurobiology.

By far the most complex organ in _C. elegans_ is its nervous system. Of a total of 959 cells, 301 in _C. elegans_ are neuronal. 20 of these are located in the organism's pharynx (which has its own nervous system). The remaining 281 make up its various head and tail ganglia along with additional ganglia running along its main longitudinal axis.

As a species, _C. elegans_ is remarkably consistent in terms of anatomical structure, especially with regard to the number and placement of its neurons. That is to say, the neurons of any one instance of _C. elegans_ is functionally identical to that of any other. Such consistency has allowed researchers to amass a large and increasingly accurate portrait of _C. elegans_ systems biology over time. Furthermore, all of this information is available to whomever is interested  (though you have to look for it).

Constancy of cell number and of cell position from individual to individual is an attribute known as `eutely`. Eutelic organisms have a fixed number of somatic cells when they reach maturity, the exact number of which is constant for any individual of the species.

Enough talk, let's have a look at the data. 

![adjacency matrix]({{ site.url }}/assets/adjmatrix.png){:height="350px" width="370px"}

<script src="https://gist.github.com/geraldmc/71606541f4e2983d562d353321080a13.js"></script>

![Figure 1]({{ site.url }}/assets/fig2.png){:height="350px" width="370px"}


![Figure 2]({{ site.url }}/assets/fig3.png){:height="500px" width="770px"}




---

<!-- <pre>
       src   dest category  weight
0     ADAL   ADEL       EJ       1
1     ADAL   ADFL       EJ       1
2     ADAL   AVDR       EJ       2
3     ADAL   PVQL       EJ       1
4     ADAL   AIAL       Sp       1
5     ADAL   AIBL        R       1
6     ADAL   AIBR       Rp       2

</pre>

-->
