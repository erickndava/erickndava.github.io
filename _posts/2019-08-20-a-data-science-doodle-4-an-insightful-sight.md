---
layout: post
title: "4. An Insightful View"
date: 2019-08-20 13:07:42 +0200
summary:  Data Science
comments: true
sharing: true
categories: hands-on
thumbnail: idea
tags:
 - data wrangling
 - data science
 - qgis
 
---
###### [A Data Science Doodle]
#### Map Like A Pro

So at this stage the data is somewhat spatially ready and to scratch the itch of how the Service Requests look like on the ground I went for [Kepler.gl](https://kepler.gl/)

>Kepler.gl is a powerful open source geospatial analysis tool for large-scale data sets.

Any of QGIS, Tableau, CARTO, etc would be up for the task but, I chose Kepler.gl because of one major capability - dealing with many many points and that it is an open source 'App'. (*At the time of this writing, it is under [active development](https://github.com/keplergl/kepler.gl/wiki/Kepler.gl-2019-Roadmap) with many capabilities being added each time.*)

Since this exercise was not prompted by an existing 'business question', though the data is real, the questions to answer have to be hypothetical. The data at this stage has been cleaned and trimmed ready to use with Kepler. The ready to use CSV of the data can be gotten from [here](https://drive.google.com/open?id=1BQFwW8q6oGrRWpWce59FKKA6F8ztTfIh).

 Note that this is not the entire data set of the 2011 service requests but it's a pretty good sample. The CSV is the portion which had atleast a suburb name attached to it. viz was 'geocodedable'.

#### Spatial EDA (Exploratory Data Analysis)

By turning the right knobs in Kepler.gl, one is offered the tools to do some quick EDA on the data. Some of the questions that can be quickly answered are 

- Which is the most demanding suburbs?
- What was the busiest month of the year?

among many others. Let's answer these in turn

##### 1. A Demanding Suburb
The obvious way of looking at demand would be to inspect the dots but, that can be overwhelming when looking at 800 000+ points. A better approach is to add a Hexbin Layer based on the service requests points, Add a height dimension for visual effect and size the hexagon appropriately (to satisfaction), then enable the 3D Map in Kepler.gl 

<p align="center"><img src="/images/demand_hexbins.png" alt="Demand Hexbins"/></p>

The areas with high service demand become apparent.- Samora Machel, Parow, Kraaifontein Area.

To explore the interactive visual follow [this link](https://kepler.gl/demo/map?mapUrl=https://dl.dropboxusercontent.com/s/bi6pp06cxn5w3xe/keplergl_mgp6tp.json).

##### 2. The Busy Months

Human have this special ability to identify spatial patterns, couple that with time and we can identify patterns over time. By applying a time filter in Kepler.gl we can scroll through time and truly and get a glimpse of where and when requests activity is highest.

Follow [this link](https://kepler.gl/demo/map?mapUrl=https://dl.dropboxusercontent.com/s/ipff0n6aehm39pq/keplergl_clmc8os.json) to get to the visualisation. Zoom to FISANTEKRAAL - Top-Right quarter of the Map. I have set the 'windows' of time to one month and the speed of motion by 10.

You can zoom out to explore other areas, for instance 

*These questions can be answered with some SQL - but where is the eye candy in that?*

These are just the few of the many questions one can answer in Kepler.

#### Punching Holes Into A Hypothesis

***Getting the boundaries wrong*** ~ The power of map visualisations give one that extra dimensional look at the data. During the data cleaning and processing stage, [**1. The Data - Service Requests**](https://erickndava.github.io/hands-on/2019/06/20/a-datascience-doodle-1-the-data/), one primary aim was to have suburb names conform to a narrow set of names separately sourced. The knowledge of local geography revealed immediately that the definition of suburb '*Athlone*' was skewed.


<p align="center"> <img src="/images/athlone_defined.PNG" alt="Athlone Boundaries"/></p>

The short-stem 'T' cluster of points, to the right in the image, is *Athlone* as assigned in the dataset. By the looks of it though and local knowledge, the suburbs, yellow labels in the image all belong to Athlone (*except the bottom-left quadrant*). This then would require a revisit of the methodology when the 'random' points where generated.

A similar pattern is revealed for *Khayelitsha*. All the places of the 'hanging-sack', represent Khayelitsha and not just the slanted rectangular cluster of points.

<p align="center"> <img src="/images/khayelitsha_defined.PNG" alt="Khayelitsha Boundaries"/></p>

You can have a look at this scenario by opening the link [here](https://kepler.gl/demo/map?mapUrl=https://dl.dropboxusercontent.com/s/h8urfshotkzctnc/keplergl_um94ar8.json). Zoom to an area by scrolling the mouse wheel or 'Double-Click' for a better perspective.

This scenario becomes apparent when one turns on "Layer Blending" to additive in Kepler.gl

This is just a brief of how one can quickly explore data in a spatial context



### #Postscript

I haven't tried to visualise the data in any of the other 'mapping' softwares to see/ evaluate the best for this exercise.
