---
layout: single
title: "Introduction to LiDAR Data"
excerpt: "."
authors: ['Leah Wasser', 'NEON Data Skills']
lastModified: 2016-12-30
category: [course-materials]
class-lesson: ['class-lidar-r']
permalink: /course-materials/earth-analytics/week-3/lidar-chm-dem-dsm/
nav-title: 'CHM, DSM, DEM'
week: 3
sidebar:
  nav:
author_profile: false
comments: false
order: 2
---


<div class='notice--success' markdown="1">

## <i class="fa fa-graduation-cap" aria-hidden="true"></i> Learning Objectives

After completing this tutorial, you will be able to:

*

### Things You'll Need To Complete This Lesson

You need `R` and `RStudio` to complete this tutorial. Also you should have
an `earth-analytics` directory setup on your computer with a `/data`
directory with it.

* [How to Setup R / RStudio](/course-materials/earth-analytics/week-1/setup-r-rstudio/)
* [Setup your working directory](/course-materials/earth-analytics/week-1/setup-working-directory/)
* [Intro to the R & RStudio Interface](/course-materials/earth-analytics/week-1/intro-to-r-and-rstudio)

### R Libraries to Install:

* **ggplot2:** `install.packages("ggplot2")`
* **dplyr:** `install.packages("dplyr")`

</div>

As we discussed in the previous lesson, LiDAR or **Li**ght **D**etection **a**nd
**R**anging is an active remote sensing system that can be used to measure
vegetation height across wide areas.


<figure>
   <a href="{{ site.url }}/images/course-materials/earth-analytics/week-3/lidarTree-height.png">
   <img src="{{ site.url }}/images/course-materials/earth-analytics/week-3/lidarTree-height.png" alt="example of a tree profile after a lidar scan."></a>
   <figcaption>Digital Surface Model (DSM), Digital Elevation Models (DEM) and
   the Canopy Height Model (CHM) are the most common raster format lidar
   derived data products. One way to derive a CHM is to take
   the difference between the digital surface model (DSM, tops of trees, buildings
   and other objects) and the Digital Terrain Model (DTM, ground level). The CHM
   represents the actual height of trees, buildings, etc. with the influence of
   ground elevation removed. Graphic: Colin Williams, NEON
   </figcaption>
</figure>