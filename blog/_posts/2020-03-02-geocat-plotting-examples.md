---
layout: post
title: "GeoCAT Plotting Examples"
description: ""
tags: []
---
{% include JB/setup %}

NCL users frequently cite NCL's extensive [documentation and examples
website](https://ncl.ucar.edu/Applications)
as a resource that helped them learn NCL and keeps them coming back. A common
concern we hear from these users regarding learning Python is that the Python
scientific programming community is too fragmented and that there's a burden on
new users to understand how the many separate modules interact (NumPy, Xarray,
Dask, Matplotlib, Cartopy to name a few). With this perspective in mind, the
GeoCAT team has started a new ongoing project called
"[GeoCAT Examples](https://geocat-examples.readthedocs.io/en/latest/)". The goal
of the GeoCAT Examples project is to provide a gallery of example Python scripts
that correspond to existing NCL examples to be used as a starting point for new
Python programmers.

The GeoCAT team recently led a highly successful two-day plotting hackathon. The
goal of the hackathon was to convert a broad sampling of NCL example plots into
Python using Matplotlib and Cartopy. These efforts were aimed at better
informing the GeoCAT team regarding the rumored gaps between NCL and
Matplotlib/Cartopy plotting capabilities, as well as to provide training tools
for the user community demonstrating how to generate NCL-like plots in Python.
26 example scripts were successfully converted and are now available from a new
gallery on the GeoCAT web site in both Python script and Jupyter Notebook form
[here](https://geocat-examples.readthedocs.io/en/latest/).

In addition to the example plots themselves, a set of utility functions was
developed that greatly facilitates annotating plots in a manner appropriate for
geospatial data, and consistent with NCL style annotation. We have begun
collecting these utility functions into a new GeoCAT project called
[GeoCAT-viz](https://github.com/NCAR/geocat-viz).

Two of the significant findings of this exercise are:
* Most of the NCL plotting capabilities can be easily replicated with
Matplotlib/Cartopy. One notable exception is NCL's "curly vector" plots, for
which there is no analogue in Matplotlib. This is a capability that could
potentially be contributed upstream to Matplotlib in the future.
* With the help of the new annotation convenience functions in most cases Python
plots can *easily* be generated that are indistinguishable from their NCL
counterparts.

The GeoCAT team is continuing to assess the best path forward for supporting
plotting of geoscience data, and is committed to ensuring that the plotting
needs of the community are met. The results of these findings suggest that with
the addition of a handful of convenience functions the combination of Matplotlib
and Cartopy may go a long way toward meeting these needs. We'd love to hear the
community's thoughts on this matter and welcome your comments to this blog.


Here's a quick look at some of our new Python example plots (left) along side
their NCL equivalents (right). The complete set of example Python plots, along
with the scripts used to generate them, is available from the GeoCAT example
repository here.



#### conLev_4:
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Contours/NCL_conLev_4.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_conLev_4_001.png" width="49%" alt="Python"></a>
<a href="https://ncl.ucar.edu/Applications/contourLev.shtml#ex4"><img src="https://www.ncl.ucar.edu/Applications/Images/conLev_4_lg.png" width="49%" alt="NCL"></a>

#### mask_1:
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Masking/NCL_mask_1.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_mask_1_001.png" width="49%" alt="Python"></a>
<a href="https://ncl.ucar.edu/Applications/mask.shtml#ex1"><img src="https://www.ncl.ucar.edu/Applications/Images/mask_1_2_lg.png" width="49%" alt="NCL"></a>
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Masking/NCL_mask_1.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_mask_1_002.png" width="49%" alt="Python"></a>
<a href="https://ncl.ucar.edu/Applications/mask.shtml#ex1"><img src="https://www.ncl.ucar.edu/Applications/Images/mask_1_1_lg.png" width="49%" alt="NCL"></a>

#### panel_3:
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Panels/NCL_panel_3.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_panel_3_001.png" width="49%" alt="Python"></a>
<a href="https://ncl.ucar.edu/Applications/panel.shtml#ex3"><img src="https://www.ncl.ucar.edu/Applications/Images/panel_3_lg.png" width="49%" alt="NCL"></a>

#### vector_1:
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Vectors/NCL_vector_1.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_vector_1_001.png" width="49%" alt="Python"></a>
<a href="https://ncl.ucar.edu/Applications/vector.shtml#ex1"><img src="https://www.ncl.ucar.edu/Applications/Images/vector_1_lg.png" width="49%" alt="NCL"></a>

#### xy_18:
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Vectors/NCL_xy_18.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_xy_18_001.png" width="49%" alt="Python"></a>
<a href="https://ncl.ucar.edu/Applications/xy.shtml#ex18"><img src="https://www.ncl.ucar.edu/Applications/Images/xy_18_lg.png" width="49%" alt="NCL"></a>









<!--
![alt-text-1](https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_conLev_4_001.png "title-1"){:height="49%" width="49%"} ![alt-text-2](https://www.ncl.ucar.edu/Applications/Images/conLev_4_lg.png "title-2"){:height="49%" width="49%"}
<a href="https://geocat-examples.readthedocs.io/en/latest/gallery/Contours/NCL_conLev_4.html"><img src="https://geocat-examples.readthedocs.io/en/latest/_images/sphx_glr_NCL_conLev_4_001.png" width="100%" style="width: 800px; height:654px; object-fit:cover;" alt="Python"></a>
-->
