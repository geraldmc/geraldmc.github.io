---
layout: post
title: Luigi In Orbit
---

`TL;DR` This post should be split into three or four and eventually will.

Here I'll describe an example of how Luigi can be used to orchestrate a more complex set of tasks. In this case a Luigi pipeline is implemented to coordinate a periodic search and retrieval of [LANSAT 8](http://landsat.usgs.gov/landsat8.php) image data. It prepares the data for upload onto`S3`, runs some [scikit-image](http://scikit-image.org/) analytics, and finally dumps the result so that an API endpoint can serve up the result (through a custom [Flask](https://www.youtube.com/watch?v=px_vg9Far1Y) web app).  I don't expect readers to understand (or care) how all these separate technologies work. *How Luigi glues them all together is the point*. Primarily, I hope to demonstrate that a tool like Luigi can help shield the data engineer from knowing each and every detail regarding how a data pipeline actually functions. Before we open up the hood some background is in order.

### An AWeSome Band
About a year ago Amazon Web Services began providing up-to-date access to Landsat via their (highly reliable) AWS infrastructure. The AWS open data initiative includes an extensive archive of Landsat 8 imagery data - with individual spectral bands not previously available - allowing anyone access to this information via predictable download endpoints. To interact with the service I'm using an open source toolkit for processing Landsat imagery `landsat-util`.

Landsat 8 imagery is an incredibly powerful resource. People from around the world now rely on it for everything from evaluating drought and predicting agricultural yields to tracking conflict.


---

![South Louisiana]({{ site.url }}/assets/LC80220392016185LGN00.jpg){:height="350px" width="350px"}

The above is a capture of southeast Louisiana roughly centered on [Lake Ponchartrain](https://en.wikipedia.org/wiki/Lake_Pontchartrain). Landsat 8 provides moderate-resolution imagery of Earth’s surface, from 15 metres (panchromatic) to 30 metres (multispectral) to 100 metres (thermal) per pixel. The term *per pixel* refers to the ground sample distance or `GSD` which is a way of relating distance between pixel centers (in the image) to actual distances measured on the ground. For example, in an image with a one-meter GSD, adjacent pixel locations are 1 metre apart on the ground. In the above each pixel represents a 15 x 15 m "box", or 2421 square feet (or the average size of a condo in Manhattan).

Landsat 8 operates in the visible, near-infrared, short wave infrared, and thermal infrared spectrums (9 bands total). For the purposes of this project we are interested only the red, green and near-infrared bands. The following chart details several of these with regard to how they capture data from the satellite's Operational Land Imager ([OLI](https://en.wikipedia.org/wiki/Landsat_8)). 

<table>
  <thead>
    <tr>
      <th>Spectral Band</th>
      <th>Wavelength</th>
      <th>Resolution</th>
      <th>Solar Irradiance</th>

    </tr>
  </thead>
  <tfoot>

    <tr>
      <td>Band 8 - Panchromatic</td>
      <td>0.500 – 0.680 µm</td>
      <td>15 m</td>
      <td>1739 W/(m²µm)</td>
    </tr>

  </tfoot>
  <tbody>

    <tr>
      <td>Band 2 - Blue</td>
      <td>0.450 – 0.515 µm</td>
      <td>30 m</td>
      <td>1925 W/(m²µm)</td>	
    </tr>

    <tr>
      <td>Band 3 - Green</td>
      <td>0.525 – 0.600 µm</td>
      <td>30 m</td>
      <td>1826 W/(m²µm)</td>
    </tr>

    <tr>
      <td>Band 4 - Red</td>
      <td>0.630 – 0.680 µm</td>
      <td>30 m</td>
      <td>1574 W/(m²µm)</td>
    </tr>

    <tr>
      <td>Band 5 - Near Infrared</td>
      <td>0.845 – 0.885 µm</td>
      <td>30 m</td>
      <td>955 W/(m²µm)</td>
    </tr>

  </tbody>
</table>

Panchromatic is just a fancy word for visible light, i.e. RGB, or the combination of visible wavelengths normally found in a photograph. The SI unit of irradiance is the watt per square metre (W/m2). 

As it is, Landsat data can be time-consuming to work with. Small and mid-size organizations that stand to benefit most may lack the technical expertise to process such data. It can easily take a novice all day (or a week) to collect, composite, color correct, and sharpen these imagery. The [landsat-util](https://pythonhosted.org/landsat-util/index.html) command line tool makes it easy to work with Landsat data. 

Landsat-util does three things very well:

* Automates Landsat metadata searching.
* Provides a great command line tool for downloading images.
* Helps process the data and prepare it for display.



[Libra](https://libra.developmentseed.org/) is a browser for open Landsat 8 data that can be used to browse, filter, sort, and download satellite imagery.

---
