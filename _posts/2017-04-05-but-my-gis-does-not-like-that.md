---
layout: post
title: "But My GIS Doesn't Like That"
date: 2017-04-05 05:06:42 +0200
summary:  Map data from spreadsheet
comments: true
sharing: true
categories: thoughts
thumbnail: table
tags:
 - map
 - dataprocessing
---

### Make Me A Map
Oft in my day job I get requests to map data contained in spreadsheets. I must say I prefer 'seeing' my (*now not*) spreadsheets in a GIS Software environment - *TableView*. So I quickly want to move any data I get to that place. The path to such and eventually the cartographic output is rarely straight forward, springing from the fact that:

* Most data cells are merged to make the spreadsheet look good.
* Column (field) names are rarely database friendly. (*Remember the Shapefile/ DBF >10 characters limit?*)
* Something is bound to happen when exporting the data to an intermediate format  - *CSV* - for manipulation. (*Data cells formatting.*) 
* Not forgetting the [unnecessary decimal](http://uxblog.idvsolutions.com/2013/11/silly-geographic-precision.html) places at times. 

The map requester often wonder why I'm taking so long to have their maps ready. In the meantime I have to deal with a plethora of issues as I wrangle the data:

* Discovering that some field names chosen by the client are reserved words in "*My* GIS" - [ **size**, ESRI File Geodatabase ]
* The tabular data can't be joined to the spatial component straight-on because:
    * A one-to-one relationship doesn't exist cleanly because the supplied data contains spatial duplicates but unique attribute data. (*What to retain?*)
    * The supposed **common** (join) field of the source data doesn't conform to the format of my reference spatial dataset.
    * Some entries of the **common** field from the master data, contain data that does not fall within the domain of the spatial  - e.g a street address such as 101 Crane Street, where evidently street numbers are only 1 - 60. (*and 01,10 and 11 exist in the database - in case you're thinking about a transcribing error.*)  
  
Frustration from the Client is understandable. The integrity of their data has come under scrutiny by the **Let-The-Data-Speak** dictate of data processing and cleaning. Unfortunately they have to wait a bit longer for their map. The decision on how to deal with the questionable data lies with them. I simply transform, as best as I can, to a work of map art.

### Database Again Please

 >... entry level Data Scientists earn $80-$100k per year. The average US Data Scientist makes $118K. Some Senior Data Scientists make between $200,000 to $300,000 per year... 
 
~ datascienceweekly.org, Jan 2017

Working with and in geodatabases makes me somewhat feel like I'm getting closer to being a data scientist. So as I resolved for year 2017 -  more SQL (*...and Spatial SQL*) and databases. 

Importing spreadsheets to an ESRI's Geodatabase has major advantages but isn't straightforward either. The huge plus being able to preserve field names from source and do data check things. Good luck importing a spreadsheet without first tweaking a field or two to get out of the way 'Failed To Import' errors.

<img align="centre" src="/images/import_to_geodatabase.PNG" alt="Import To Geodatabase">

Comma Separated Values (CSV) always wins but, beware of formatting within the spreadsheet. If wrongly formatted...Garbage In! But once the import is neatly done, I can comfortably clean data for errors and check integrity better in My GIS environment. As a bonus I get to learn SQL too. Cant' resist that pretty window!

<img align="centre" src="/images/import_to_spatialite.PNG" alt="Import To Spatialite">

#### #postscript

The above are just a few matters highlighting what goes behind the scenes in transforming a spreadsheet to a map. The object to show the non GIS user it takes more than a few clicks to come up with a good map.
