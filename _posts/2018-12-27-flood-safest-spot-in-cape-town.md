---
layout: post
title: "Cape Flood Safe"
date: 2018-12-27 08:56:42 +0200
summary:  Data Wrangling 
comments: true
sharing: true
categories: hands-on
thumbnail: map
tags:
 - opendata
 - analysis
 - relief
 
---

##### SCT Part 3

### (18.42281, -33.95947)

So, those are the numbers to keep and punch into the satellite navigator in the unlikely event of the Atlantic Ocean bursting its Cape Town shores. If you stay in Cape Town, the first place that comes to mind when you hear 'Flood Survival' is likely Table Mountain and rightly so. But, which spot exactly can one stand longest on solid earth?

##### Cut To The Chase: [The Safe Strip](https://erickndava.github.io/cape-cbd-dem/)

## How To DEM

### Get Data

Relief maps always get my attention. The mystery of attempting to model reality on the computer enthuses me. There are plenty tutorials on the net on how to do this so here's my version.

I got some vector base data (Metro Boundary, Suburbs, Roads, Railway Line, Building Footprints and a DEM - Digital Elevation Model ) off City of Cape Town's [Open Data Portal](http://web1.capetown.gov.za/web1/opendataportal/Default) or [here](https://odp-cctegis.opendata.arcgis.com/). The vector data I loaded into a geopackage. [How?](https://erickndava.github.io/hands-on/2018/06/01/in-with-the-new-geopackage/) Of special interest was the DEM, described as *"Digital model (10m Grid) depicting the elevation of the geographical surface (Bare Earth Model) of the Cape Town municipal area."* The Open Data Portal has the data stored as *10m_Grid_GeoTiff.zip*.

### Style Terrain

After extracting the compressed elevation data, I loaded it in QGIS.
1. Load 10m_BA, 
2. Style the 'relief map' in Properties --> Style

<img align="center" src="/images/Pseudo_Coloured_DEM_Settings.png" alt="Pseudo Coloured DEM Settings">

The raster would then look as shown below

<img align="center" src="/images/Pseudo_Coloured_DEM.PNG" alt="Pseudo Coloured DEM">

3. Now to create a hillshade. Do Raster --> Analysis -->DEM (Terrain Models)...

   With the settings shown below create a Hillshade DEM

<img align="center" src="/images/Hillshade_DEM_Creation_Settings.png" alt="Hillshade DEM Creation Settings">

This gives us a hillshade ...

<img align="center" src="/images/Hillshade_DEM.PNG" alt="Hillshade DEM">

4. To get us a Terrain Map. Set transparency in the Relief Map (10M_BA). RightClick --> Properties --> Transparency

<img align="center" src="/images/Pseudo_Coloured_DEM_Settings_Transparency.PNG" alt="Pseudo Coloured DEM Settings Transparency">

5. Now a combined view of The Relief and Hillshade ...

<img align="center" src="/images/Relief Map - Combined Relief and Hillshade.PNG" alt="Relief Map - Combined Relief and Hillshade">

6. Now Load the other support vector layers
    - Metro Boundary (Flood Plane)
    - Suburbs
    - Roads 
    - Railway Line
    - Building Footprints
    
<img align="center" src="/images/all_layers_loaded.PNG" alt="All Layers Loaded">

### Getting 3D

To get started with 3D Terrain. Load and activate the [Qgis2threejs Plugin](https://github.com/minorua/Qgis2threejs).(Read [more](https://qgis2threejs.readthedocs.io/en/docs/)). (This is one approach to getting 3D in QGIS. At the time of writing this post, 3D comes native with QGIS. Read ([more.](https://www.lutraconsulting.co.uk/blog/2018/03/01/working-with-qgis-3d-part-1/))

The Qgis2threejs Plugin is unique in that it bootstraps the process to have a web ready 3D model to play with.

1. Launching the Plugin for the first time should give something like this ...

<img align="center" src="/images/dem_Safe_spot_flooding_level.PNG" alt="Qgis2threejs First Launch">

2. Zoom to Cape Town CBD and include all of the table of Table Mountain.

<img align="center" src="/images/focus_area_for_export.PNG" alt="DEM focus area">

Now, to prepare for exporting the subject area, emulate the following series of settings paying attention to the parts
World, DEM, Roads, 

<img align="center" src="/images/settings_1.PNG" alt="Export Settings">

<img align="center" src="/images/settings_2.PNG" alt="Export Settings">

<img align="center" src="/images/settings_3.PNG" alt="Export Settings">

<img align="center" src="/images/settings_4.PNG" alt="Export Settings">

<img align="center" src="/images/settings_5.PNG" alt="Export Settings">

<img align="center" src="/images/settings_6.PNG" alt="Export Settings">

<img align="center" src="/images/settings_7.PNG" alt="Export Settings">

The Surburbs Layer is used mainly for labelling purposes in the final export. We are not interested in showing the Suburbs boundaries for now.

Through Trial and Error and guided by the absolute height of the DEM,  we get the optimum height value, 1 060m, to use for our Flood Plane (Which initially is just a polygon covering all of our area of interest - Metro Boundary in this case).

### Export To Web

In order to have an interactive 3D Map simulating a flood. 

1. Ensure **3DViewer(dat-gui).html** is chosen under the *Template file* in the Qgis2threejs Plugin.

2. Choose the appropriate path and name for the *index* html for the visualisation. In this case CCTerrain.html is chosen.

3. Export and Qgis2threejs will generate the necessary style sheets and other files for the export.

4. Now using a text editor, edit parts of the exported html file (*CTTerrain.html*) to reflect what the project is about and put in some usage information.

A Preview below - full screen [here](https://erickndava.github.io/cape-cbd-dem/)

<iframe width="100%" height="520" frameborder="0" src="https://erickndava.github.io/cape-cbd-dem/" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>


### #PostScript  - Find The Safe Spot

Click around the map to turn on/off the layers.

