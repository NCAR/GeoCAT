---
layout: default
title: 2023 Roadmap
output:
  html_document:
    toc: true
    toc_float: true
---


<p style="font-weight:550; font-size:50px"> 
<img align="center" width="10%" height="10%" src="/images/GeoCAT_Final_Logos-03.svg"> 2023 ROADMAP </p> 

* Table of contents
{:toc}

# 1. Overview

This roadmap document defines the broader GeoCAT scope with tasks and 
activities under scope items, then provides a high level schedule that 
GeoCAT will tentatively employ throughout 2023 to achieve the deliverables 
and milestones out of those activities.

## 1.1. Community involvement

GeoCAT welcomes and needs community input and feedback on this roadmap as 
well as development activities throughout the year. That helps us ensure 
we address community needs for geoscience data analysis and visualization.

## 1.2. GeoCAT Scope

The scope of the GeoCAT project is based on three essential objectives of 
the GeoCAT group: 

1. Development of geoscientific data analysis and visualization tools, 
2. Open development & community engagement,
3. Scalability

## 1.3. How to read this roadmap?

Under each objective (i.e. scope item) in section 2, the main tasks on which 
the GeoCAT team will work on are listed (2.1.1, 2.1.2, ...).

For each task, activities are also defined  (i, ii, iii, ...). Deliverables 
and/or milestones are also defined for activities when applicable.

## 1.4. How to give feedback & input to this roadmap?

If you'd like to provide any feedback/input about this roadmap, 
you can always use the [GeoCAT 2023 
roadmap](https://github.com/NCAR/GeoCAT/discussions/60) discussion.

However, some task under GeoCAT objectives might correspond to a 
separate software package or GitHub asset of GeoCAT. Therefore, we will 
also provide links to corresponding GitHub discussions for such tasks  
throughout this document, through which you can let us hear your voice 
about a particular part of GeoCAT. 

That way, we can ensure an open community conversation, virtually about 
anything.

If you are not comfortable with GitHub discussions though, you can also 
reach out to us via our email: geocat@ucar.edu


# 2. Roadmap

## 2.1. Development of geoscientific data analysis and visualization tools

### 2.1.1. Project Raijin

Unless recommended otherwise in the following items, please see the 
[UXarray 2023 Roadmap](https://github.com/UXARRAY/uxarray/discussions/196) 
and put your Raijin inputs, if any.

1. UXarray
   - Milestone: API redesign to satisfy both the usage requirements & 
     specifications and to comply with the Xarray-extension best 
     practices
     - See the [UXarray Redesign Thoughts and 
       Options](https://github.com/UXARRAY/uxarray/discussions/185) 
       discussion for detailed information and your inputs.
   - Analysis operators development
     - See the [Prioritization of Uxarray analysis 
       operators](https://github.com/UXARRAY/uxarray/discussions/46) 
       discussion for detailed information and your inputs.
   - Basic visualization functions development


### 2.1.2. GeoCAT-comp & GeoCAT-f2py

Unless recommended otherwise in the following items, please see the
[GeoCAT-comp & GeoCAT-f2py 2023 
Roadmap](https://github.com/NCAR/geocat-comp/discussions/323)
and put your GeoCAT-comp & GeoCAT-f2py inputs, if any.

1. New functionality
   - Community feature requests
   - [Existing backlog items](https://github.com/orgs/NCAR/projects/42/views/12)
   - Fortran to Python conversion
2. Improvement, maintenance, and quality of life updates
   - Optimization/benchmarking (SIParCS internship)
   - Support for M1/M2 and Windows platforms
   - Documentation improvements
   - Continue to research and match community packaging standards
    
### 2.1.3. GeoCAT-examples & GeoCAT-viz

Unless recommended otherwise in the following items, please see the
[GeoCAT-examples & GeoCAT-viz 2023
Roadmap](https://github.com/NCAR/GeoCAT-examples/discussions/492)
and put your GeoCAT-examples & GeoCAT-viz inputs, if any.

1. New functionality
   - New examples from community requests
   - New examples from ordered list (TBD)
   - Changes to existing examples for clarity
2. Improvement, maintenance, and quality of life updates
   - Support for mesh-based rendering
   - Interactive plots, beginning with support for time step animations
   - Changes to existing examples to keep up with dependencies


### 2.1.4. Project Pythia

1. Leverage Project Pythia outreach efforts to announce releases
2. Contribution reviews
   - Provide reviews for contributions to the Pythia assets (mostly in the 
     form of GitHub pull-requests)
3. Content support   
   - Generate GeoCAT Cookbook(s) that show off new functionalities

### 2.1.5. WRF-Python

1. User support
2. Explore improved Xarray compatibility

### 2.1.6. NCL

1. Conda installation support


## 2.2. Open development & community engagement

1. Pangeo community
   - Retain GeoCAT presence at Pangeo events (e.g. weekly meetings, 
     dev. meetings, etc.)
   - Seek increased Pangeo involvement in Raijin’s UXarray development
2. NSF NCAR’s ESDS (Earth System Data Science)
   - Continue GeoCAT presence at ESDS
   - Continue organizing/supporting ESDS events (e.g. weekly office hours, 
     bi-weekly forums, annual-like tutorials, etc.) 
3. Publications & presentations
   - AGU, AMS presentations
   - GeoCAT updates, talks, tutorials, etc.
4. Project Raijin
   - Continue Raijin & SEATS collaboration on UXarray development
   - Collaboration with NSF NCAR’s SIMA (System for Integrated Modeling of 
     the Atmosphere)
     - NetCDF datasets in UGRID convention
   - Seek new collaborations
5. GeoCAT-comp & GeoCAT-f2py
   - Showcase functionality to community (examples, outreach, 
     cross-posting, talks, etc)
6. GeoCAT-examples & GeoCAT-viz
   - Assisting SIParCS internships for Virginia Do
   - Provide content and presentations for educational content throughout 
     the year
7. Project Pythia
   - Contribute to Project Pythia outreach efforts such as Python tutorials, 
    etc.


## 2.3. Scalability

1. Dask (GeoCAT-comp & UXarray)
   - Ensure compatibility & apply best practices (GeoCAT-comp SIParCS 
     internship)
     - Investigate the existing function implementations to check if they 
       were implemented with Dask best practices
     - Ensure it for new implementations
   - Performance analysis
     - Investigate the performance of the existing function implementations 
       with Dask
2. GPU programming (GeoCAT-comp & UXarray)
   - Explore




