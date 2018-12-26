---
layout: post
title: Anything For A Map - Part 0
date: 2016-12-10 19:06:42 +0200
summary:  Mapping a good narrative.
comments: true
sharing: true
footer: true
categories: thought idea
thumbnail: map-marker
tags:
 - hands-on
 - tutorial
---
### On The Heels of The Pioneer Corps
Mapping the footprints of the men who faced the thicket, built drifts across rivers, played the debut soccer and rugby matches in a country.

### Background
<img align="right" src="http://www.memoriesofrhodesia.com/images/newsletters/TULI/P3060015.jpg" alt="Laager"> 

I am enthused by maps and more so good cartography. I will scrounge any document just to map the two or more places mentioned there. Perchance while working with an old topomap of Zimbabwe, I bumped into small crosses that represented features of historic significance. Of special intrigue were locations identified as [Fort](http://en.wikipedia.org/wiki/Fortification) and Laager (pictured above). As I *Google-dug* some more on these, I came across an article, [Pioneer Forts in Rhodesia 1890-1897](http://rhodesianheritage.blogspot.com/2010/02/pioneer-forts-in-rhodesia.html). My interest grew as I read [a gripping account by Horste.](http://www.rhodesia.nl/hoste.htm)[(The Historic Publication)](https://github.com/erickndava/pioneer-column-1890/blob/master/Rhodesiana%20Publication%20No.%2012%20September%201965%20Pages%2012-37.pdf) He chronicles how in 1890, the [Pioneer Column](http://en.wikipedia.org/wiki/Pioneer_Column)'s escort of British South Africa Company's Police progressed into present day Zimbabwe. I had read and heard about this in my history classes, that was then, I am all maps now!

##### ***BUSY*** ?:~ [Cut To The Chase.](http://erickndava.github.io/pioneer-column-map/index.html)*** 

### Why?
* Well, I'm am oft looking for something to map (*and the narrative by Hoste is too good to waste!*)
* To have a 'cartographic-perspective' of how the historic route impacted the development of existing roads and towns.
* Get a 'feel' of the topography the column faced.
* Tinkering!

### Get There Fast
---
##### [1. Vector Data Preparation](#a1)
##### [2. Raster Data Preparation](#a2)
##### [3. Map Creation](#a3) 
##### [4. Map Serving](#a4)
##### [5. Challenges/ Observations](#a5)
##### [6. Results](#a6)

---
My conception of the map was a route, points and relief map that stood out, with a subtle backdrop of existing roads and features. I had bumped into carto works with tilemill, in particular [Toner](http://maps.stamen.com/toner/#10/-17.8239/31.0556). I had to 'broad-read' on various carto projects. For starters, I had an undated, georeferenced 1:250 000 topography map of Zimbabwe(Rhodesia). I opened a blank QGIS project, which had the following CRS settings. This was the basis of other work to follow:
<img align="center" src="/images/qgis-crs.png" alt="QGIS CRS">

### <a name="a1">1. Vector Data Preparation</a>
##### Key Points
* (*route_points.shp*): **T**he first task was to create spatial data for key points. Sources of information was the topo map and the [narrative by horste](https://github.com/erickndava/pioneer-column-1890/blob/master/Rhodesiana%20Publication%20No.%2012%20September%201965%20Pages%2012-37.pdf). Editing in QGIS is pretty straight forward. This route_points.shp shapefile would contain three fields: name, type, notes, arrival. These fields I came up with after several passes of the narrative. **Name** would be used to label  the point, **type** to style (in Tilemill) , **notes** for additional information on the point and **arrival** to capture the date the Pioneer Corps arrived at the 'point'.

##### Route Plotting
* (*route_track.shp*): **R**oute plotting logic was to join the points with a line. To refine the route, I took a hint from the narrative - avoid the hills and follow watersheds.

##### Route Buffer
* (*route_50km_buffer.shp*): **W**ithin QGIS Processing Toolbar, the next operation was to buffer an area around the route. I would use this extent to map the route and generally clip other data for the project. I decided on a buffer radius of 50km. A guy named Selous had 'pre-scanned' the road ahead and gave indication as to where the column should march through. Additionally, I intended to use terrain data with 30m spatial resolution and 50km would give me ~1700 pixels on either side of the route. This should provide good 'terrain-context'.

### <a name="a2">2. Raster Data Preparation</a>
I am a fan of relief maps. I could just spend hours just panning a good representation of terrain so this stage would give me great pleasure! For this section I intended to follow these tutorials - [Working with terrain data](https://www.mapbox.com/tilemill/docs/guides/terrain-data/) and [Using TileMill’s raster-colorizer](https://www.mapbox.com/blog/tilemill-raster-colorizer/). I however ended up emulating this in QGIS. Which gave excellent results! 
<img align="center" src="/images/relief_in_qgis.png" alt="Relief In QGIS">

##### Relief Map
* **Q**GIS handles raster data easily. I was going to use the [SRTM Version 3, 30m DEM](http://www.jpl.nasa.gov/news/news.php?release=2014-321) data set. The project area (*route_50km_buffer.shp*) was covered by 14 elevation data tiles. In QGIS I merged the tiles to form one dem tif. ***[Toolbar]*** -- Raster -- Miscellaneous -- Merge, to come up with (*route_dem_raw.tif*)

* I clipped the merged elevation model with (*route_50km_buffer.shp*), this resulted in a 'along-route' tif viz (*route_dem_50km_buf.tif*). 

* **I**n line with [this tutorial](https://www.mapbox.com/tilemill/docs/guides/terrain-data/), I was to create a hillshade first. My machine is setup with [OSGeo4W](http://trac.osgeo.org/osgeo4w/) so running gdal commands was supposed to be a breeze. so I ran
```sh
gdaldem hillshade -co compress=lzw route_dem_50km_buf.tif route_dem_hillshade.tif
```
 
* **A** relief map was next. Firstly I styled (*route_dem_50km_buf.tif*) in QGIS: <img align="center" src="/images/relief_style_in_qgis.PNG" alt="Relief In QQGIS">. It turned out the 15 equal interval classes and a spectral colour map gave an unsatisfactory relief map. Pleasantly, QGIS permits the export and import of colour ramps. So I got busy editing the 15 interval ramp I had generated - a painstaking task, but I prevailed. So with the [colour_ramp.txt](https://github.com/erickndava/pioneer-column-1890/blob/master/colour_ramp.txt), which I had also checked in QGIS, I ran
```sh
gdaldem color-relief route_dem_50km_buf.tif colour_ramp.txt route_dem_colour_relief.tif
```
* **N**ext up was slope shading which is a two way procedure. First 
```sh
gdaldem slope route_dem_50km_buf.tif route_dem_slope.tif
```
* Then secondly, the actual slope shade
```sh
gdaldem route_dem_colour_relief.tif -co compress=lzw route_dem_slope.tif slope-ramp.txt route_dem_slopeshade.tif
```
As explained [here](https://www.mapbox.com/tilemill/docs/guides/terrain-data/), make sure to use the [slope.txt](https://github.com/erickndava/pioneer-column-1890/blob/master/slope.txt) file so that the "color-relief command can use it to display white where there is a slope of 0° (i.e. flat) and display black where there is a 90° cliff (with angles in-between being various shades of grey)."

**J**ust for fun, I loaded the three elevation data files (tifs) created above into QGIS and styled them with the transparencies indicated in the Tilemill tutorial, viz colour_relief: 10% transparent, hillshade: 60%,slopeshade: 40%. The result was astounding!


### <a name="a3">3. Map Creation</a>
##### Osm Toner
To provide cartographic contrast and temporal context I wanted a subtle background and osm toner seemed the best choice. The procedure is outlined succinctly [here](https://github.com/aaronlidman/Toner-for-Tilemill).

* **F**irst , I got a subset of OpenStreetMap data relevant to my project from [BBBike.org](http://download.bbbike.org/osm/) from which one can clip data to custom boundaries. *(Aside: I only discovered this site while hacking this project, indeed [giyf](http://www.giyf.com)! )*

* **N**ext was loading the OSM data into a PostGIS database. I already had a [Postgres Installation](http://www.enterprisedb.com/downloads/postgres-postgresql-downloads?quicktabs_postgres_plus_dwnlds=1#quicktabs-postgres_plus_dwnlds). So in PgAdmin III, I created a database and named it osm. After that the actual loading of the data had to be done. More information on running osm2pgsql can be found [here](http://learnosm.org/en/osm-data/osm2pgsql/). For this I downloaded [cygwin-package.zip](https://github.com/erickndava/pioneer-column-1890/blob/master/cygwin-package.zip) and extracted to a folder. After saving my custom OSM data (*pioneer_route2.osm.pbf*) to the same folder as *osm2pgsql.exe*. I ran the command and got error:
<img align="center" src="/images/osm2pgsql_error_1.PNG" alt="osm2pgsql error">
After some *Googling* and amends, another error
<img align="center" src="/images/osm2pgsql_error_2.PNG" alt="osm2pgsql error 2">
After this, I had to download [default.style](https://github.com/erickndava/pioneer-column-1890/blob/master/default.style) from the web. Re-running the command again, now with the style available...another error:
<img align="center" src="/images/osm2pgsql_error_3.PNG" alt="osm2pgsql error 3">, I tried to address that with some Postgis chops.
<img align="center" src="/images/create_hstore.PNG" alt="create hstore 3">. That also did not give solace. I opened the file in Notepad++ and commented out line 155 to 160 of default.style in the text editor. I figured this wasn't that important for my intended use - map styling. <img align="center" src="/images/default_style.PNG" alt="Default Style">. 
#### Tilemill

* **R**unning *config.py* : In accordance with  the tutorial, I edited the python file accordingly and successfully ran *make.py*. My project was automatically created. Unfortunately several things went wrong with this setup - among them, having to download a ~300MB file (*I have access to very limited bandwidth*). 
* Since I had some exposure to Tilemill, I had an idea of how stuff was structured so decided to take the 'brute-force' route to having a Toner-Template setup. I resorted to modifying the DC-Streets project (which is auto-setup with an installation of TileMill):

     -  I prepared my custom osm data (previously loaded into PostGRES ) to match that on the DC-Streets project. The (shapefile) schema had to be exact - viz field for field so that styling and labelling would be smooth.
     
     - Now what remained was to tweak the major CartoCSS colour styles using gray scales only. For this I simply edited the highway.mss and used [ColorBrewer](http://colorbrewer2.org/) to more accurately pick greys that would represent the roads and [color-hex](http://www.color-hex.com/) to decode the 'hashed' alpha-numeric characters.




 **M**ore **S**tyling in **T**ilemill

* Creating the terrain map

    - Using the raster layers I had prepared in QGIS in Stage 2. above, I loaded them in TileMill and styled them as I had in QGIS. Amazeballs!  <img align="center" src="/images/relief_in_qgis.PNG" alt="Relief In QGIS"> This would serve as the base layer for the other data except at higher zoom levels viz > 13. (I concluded the relief display range from playing with the visualisation in TileMill).
    
* Adding detail - The Route and Stop Points
   
    - Adding the Column *route* was straight forward as I had styling in highway.mss to emulate. 

    - With the Stop points I had a little reading of the manual (aka Google) to do as the *open-streets-dc templates did not include any points styled. I wanted some fancy symbolisation. Through trial and error I got satisfactory results eventually for the various zoom levels.
    
    - Rivers and streams were essentially lines and polygons and I had the template as a starting point.

* Labelling 

    - My Intention was emphasise history and 'background' the present. So I made my labels for the column landmarks coloured. Luckily the place names in open-streets-dc were already black and white. So I didn't have to touch those.
    
    - A *serious* challenge was to avoid label conflicts and also at the same time display landmarks and labels at the same time. Again reference to the manual saved the day. Used **text-dx:** and **text-dy:** extensively in the CartoCSS.
    


**Exporting** **T**he **Map**work

This stage was the most exciting for me - who doesn't want to see the fruit of their labour?! TileMill gives you a preview of what the export will be like in the WYSIWYG manner so there's no crossing of fingers to what the output will be like, just a demand for patience as the export runs.

After two unsuccessfully runs I had to explicitly define the RCS for all the layers in my project.(those were set to Auto-Detect). I defined my export parameters - MBTiles, Bounds, Centre  - saw the software estimated 8 hours to completion of the run. Luckily it was night so I went for some shut-eye.

Come morning there was my 237MB MBTiles file!

I fired up QGIS to take a look. I recalled QGIS supported these. The result was not so impressive - had a grainy feel to it. TileMill had rendered it smoothly so I knew it was not my data. I remembered a Portable MBTiles viewer. I couldn't quite recall the name to I consulted my GitHub account (anything I think might be of interest to me I put on the Watch list ) - there it was [TileStream Portable](https://github.com/springmeyer/portable-node-app ).

I loaded my MBTiles per instruction and my pannable map ....

<img align="center" src="/images/tilestream_map.PNG" alt="TileStream Map">

So one can actually give a friend, client a pannable map on a USB Stick loaded with the MBTiles being served by the TileStream Portable. (*I've read on the inter-web companied serving imagery as MBTiles *) 

### <a name="a4">4. Map Serving </a>

**I will not go into detail describing step-by-step this part of my exercise as it detracts from the intention of this blog post. Summary will only be given since with Stage 3 above, the Mapping exercise would be complete.*

How-to serve the resultant map was largely inspired by the following blog post which I emulated closely - [Setting up a Cloud MBTiles Server with Benchmarks](http://fuzzytolerance.info/blog/2014/03/03/2014-03-03-screencast-33-setting-up-a-cloud-mbtiles-server-with-benchmarks/) (*You can also find the screencast in my Github Repo*).

[Leaflet](http://leafletjs.com) was used as the Mapping Client. I had had a historic stint with [The Bootleaf Template](https://github.com/bmcbride/bootleaf) and I started there - with a clone of that repository. I spend considerable time in SublimeText 3 editing the template to suit my needs.


### <a name="a5">5. Challenges/ Observations </a>
Some points to note in the representation of wok done here:

* I had to deal with data of varying spatial scales - Topo map, Elevation data, Openstreetmap data, etc.

* For some stretch of the route between explicitly mentioned stop points, the narrative by horste was not sufficient to accurately approximate the route the pioneer corps took.

* There is error inherent in the the use of Laagers plotted from the topo map since no temporal information was given. These could well have been apart historically.

* Laagers are a temporary feature hence their representation must be interpreted as being virtual, temporally obsolete from point to point. (The corps were moving forward and 'broke laager' as they progressed!)

* Notice that after Fort Victoria, the track becomes dual. According to Horste "We now made two parallel roads, about fifty yards apart, as it had been decided to have a double line of wagons, instead of the long cumbersome single line that we had had up to then."

* Gave water bodies prominence (represented in colour) - little might have changed since 1890 just as is the case with terrain. Not withstanding the construction of dams since then.

### <a name="a6">6. Results </a>

I have served all the data relating to this project to a [GitHub repository](http://github.com/erickndava/pioneer-column-1890/). 

You can link directly to the resultant map here - [The Pioneer Column Map](http://erickndava.github.io/pioneer-column-map)

#### #postscript

* I traversed many 'technology domains' in this exercise and it was fun. That has helped me know a comfortable bit of everything. Linux Server administration! Database Server Management - remember my PostGIS instance?
* After my experience with TileMill on this project, I decided to move to (Mapbox) Studio. No need to remain in 'legacy mode'  - I am a [geohipster!](http://geohipster.com/)
* TileMill may be 'old' and out of active development but it does pack a punch! Additionally you don't have to 'connect' to [MapBox](http://mapbox.com) to use it like its successors - [MapBox Studio](https://www.mapbox.com/mapbox-studio/) and [MapBox Studio Classic](https://www.mapbox.com/mapbox-studio-classic/).
