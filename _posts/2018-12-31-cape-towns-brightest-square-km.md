---
layout: post
title: "A Bright Square Kilometre"
date: 2018-12-31 10:20:42 +0200
summary:  Data Wrangling 
comments: true
sharing: true
thumbnail: map
tags:
 - opendata
 - visualisation
 - aggregation
 
---

##### SCT Part 4

### All That Glitters

<img align="center" src="/images/cpt_night_lights.jpg" alt="Cape Town Night Lights">


Image credit - [Gathua's Blog](https://gathua.wordpress.com/tag/cape-town-nights/)

The above is a typical representation of Cape Town night lighting. How would that look like from space? One way to answer that is demonstrated [here](https://aetperf.github.io/2018/09/19/Nighttime-Lights-with-Rasterio-and-Datashader.html) but, the data used there is quite coarse. This post is on a similar approach with the further investigation of finding the brightest spot on a Cape Town night. Data on the location of street lights was used as provided on the Cape Town [open data portal](http://web1.capetown.gov.za/web1/opendataportal/Default).


### Some Assumptions
- Street lighting is the only lighting at night time at a place.
- All street lights are represented (no broken light).
- The dataset is complete and accurate (temporally).
- All the lights have identical lumens.
- [Other implied assumptions.]

### Public Lighting

The subject data is described as "*Location of street light poles and area lighting (high-masts) in the Cape Town metropolitan area.*" - ***Public Lighting 2017.zip***

In Q, I ran Statistics for text field to find out how many ***unique*** lighting types there were. Just two - ***Streetlight*** and ***High-mast Light.*** A total of 229 538 lights.

<img align="center" src="/images/stats_on_lighting_type.PNG" alt="Street Light Stats">

The distinctiveness of street light types persuaded me to give greater weight to the High-mast Light. So, an additional assumption -
> High-mast Lighting is twice as bright as just Streetlight lighting.

So in Q I created a weight field and populated it appropriately. 

To scratch the curiosity itch. The lighting in Q, for the CBD and surrounds.

<img align="center" src="/images/cbd_lighting_in_q.PNG" alt="CBD and enviros">

### Boot Strapped Visualisation

If you haven't heard of Kepler.gl you must [check it out](http://kepler.gl/#/). I handles your geodata in the browser and does some amazing things.

First step is to convert the shapefile to csv, json or geojson. In Q this is achieved via right click on the layer and Save As.

Load the ***CapeTown_Public_Lighting.csv*** in Kepler.gl

(On loading the ***CapeTown_Public_Lighting.csv*** in Kepler.gl the weight field was being interpreted as type Boolean and not just Integer. It turns out this was a bug (December 2018). I quickly remembered this as I am actively 'watching' the Kepler.gl [github repository](https://github.com/uber/kepler.gl))

As a workaround I used weights of 100 and 200 for the StreetLights and High-mast Light respectively.

<img align="center" src="/images/high_mast_light.PNG" alt="High mast lighting">

Panning around the map, the above caught my eye. Turns out the more isolated dots are high-mast lights. Actually in Kepler, you can filter/ view a type at a time or together using different colours and a whole other options.

Our objective of finding the brightest spot requires we aggregate the points data. That is home turf for Kepler. With a few clicks we have this;

<img align="center" src="/images/light_intensity_hexes.PNG" alt="Light Hexes">

We are looking for ***The Brightest Square Kilometre*** and we factor in the assumption high-mast light = 2 X Streetlight.

So in order to get to calculating the correct area for the hexagon being employed by Kepler, I got to asking.

<img align="center" src="/images/kepler_hexagon_radius.PNG" alt="Hexagon Radius">

Taking a hint from [here](https://www.vcalc.com/wiki/vCalc/Polygon+-+area2) and using the formula

~~~
 A = ½• n • r² • sin( (2π) / n)
~~~

where:

- A is the area of a polygon
- r is the outer radius
- n is the number of sides

I got the radius as 0.6204 km

Under **Radius Tab**, Enter Radius value of 0.6204 and decrease the **Coverage** (base area of the hexagon being visualised)
Switching ON The **Enable Height** Tab - Enter a reasonably high **Elevation Scale**, The HeighT is based on Point Count.
**High Precision Rendering** turned ON.


These parameters aid quick identification of the 'tallest' hexagonal column hence the brightest square kilometre. With a count of 923.

<img align="center" src="/images/brightest_sqm_1.png" alt="Brightest Square Km">


### Light Weight

To take into account the weight of the light type (high-mast vs street light), we add another data layer (a duplicate of the ***CapeTown_Public_Lighting.csv*** really), apply a weight filter Add a Layer based on this and style it with similar parameters to the first Layer. (*At the time of writing this post, a filter when applied to a dataset affects all the layers based on it. Hence the need to duplicate the dataset with this approach.*)


<img align="center" src="/images/brightest_sqm_2.png" alt="High Mast Lights">

With a highest count of 52 per the square kilometre. Even doubling high mast lighting for impact falls short of the 871 (923 - 52) of 'StreetLight' alone.

Now styling the High Mast Lighting with grey scale...so we can see the two together.

<img align="center" src="/images/combined_lighting.png" alt="All Lights">

There is apparent correlation - Highly lit areas also have high mast lights. High Mast ~ 'white' columns.


You can interact with the Street Lights Map below.


#### #PostScript  - Replicate


Kepler.gl is under active development and new features are being added continuously including some fascinating ones on the developers' road map.

One of the features is the ability to share a visualisation easily. So here goes: 

- The *Data **and** Settings* ~ for this exercise can be downloaded [here](https://www.dropbox.com/s/zjo1e177b55eztb/CapeTown_Street_Lighting.json?dl=0).

- Download the file to your local drive and open it from [The Kepler.gl Website](https://kepler.gl/#/demo).
