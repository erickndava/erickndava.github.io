---
layout: post
title: "Arcg! My Data!"
date: 2018-03-26 09:49:42 +0200
summary:  Data Wrangling 
comments: true
sharing: true
categories: thought
thumbnail: map
tags:
 - idea
 - mapping
 
---

### Arc who?

I am a fan of the file geodatabase. Somehow I feel I own the thing and can fire up Q and ogle in there with Open FileGeodatabase. But, enterprise geodatabase, I'm not too sure. While I edited some point data, well, point SDE Feature Class in an *ArcSDE Geodatabase. The machine froze and the software struggled to show selected features. By some stroke of luck I managed to save my edit and exit the program. Relaunch and errr....Where are my points?

Instead of 
```
18.519822, -33.941942
```
I get
```
19.000168, -0.000308
```

I commenced in no strategic order troubleshooting why the data was showing all the way up there. The projection, extend and orientation all looked correct. Recalculate extend, Check geometry - No change.

I exported the data to shapefile (yes, back to basics right?). Delete .prj, redefine the projection, still 'wrong place'. I was still curious to know where on earth, literally, the points fell, if not outer-space. 

EPSG_Polygons_Ver_9.2.1.shp from [epsg.org](http://www.epsg.org/EPSGDataset/DownloadDataset.aspx) was my destination for a projection galore.
>The IOGP’s EPSG Geodetic Parameter Dataset is a collection of definitions of coordinate reference systems and coordinate transformations which may be global, regional, national or local in application.

<img align="center" src="/images/lostpoints_collection.PNG" alt="Coords of Lost Points">

Congo? Jumping all the way up to the Equator, past the Tropic of Capricorn. 

I added/ calculated the X,Y fields on the shapefile. The coordinates were as expected but still the points displayed at the 'wrong place'. Exported the tabular data to the magical csv. Add to the gis software, 'Display X,Y'. Tada!! Back home.

I imported the data back to the multiuser environment for a trouble free feature class for my team members.

How, why the data behaved this way I am still to know. But, a chase by the hands of time didn't permit a thorough investigation nor Googling for the right way to fix such an anomaly.

### #Postscript

Oftimes QGIS is my go to app for alternative behaviour. This time around nothing was auto-fixed. Imports, exports and tens of arctools in my preferred filegeodatabase sandbox didn't get this anomaly resolved. It was good remembering that first principles get things done - the x,y coordinate pair is at the heart of geo.
