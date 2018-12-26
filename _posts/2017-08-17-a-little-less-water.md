---
layout: post
title: "A Little Less Water"
date: 2017-08-17 09:06:42 +0200
summary:  Mapping the reservoirs
comments: true
sharing: true
categories: mapping
thumbnail: map
tags:
 - thought
 - open-data
 
---

### Water Waste to Water, Less ?

This is a pseudo-follow-up post to [A Point About Points](https://erickndava.github.io/thoughts/idea/2017/04/21/a-point-about-points/).CapeTown is still in the midst of drought howbeit winter rains bringing some relief. As further mitigation, introducing Level 4b water restrictions from 1 July 2017, were each individual [should use 87L per day](http://www.capetown.gov.za/Family%20and%20home/residential-utility-services/residential-water-and-sanitation-services/make-water-saving-a-way-of-life).    With this information all about I could not resist the itch to know where the water sources were in CapeTown, well, geographically that is. [The Centre for Geographical Analysis](http://www0.sun.ac.za/cga/) at Stellenbosch University started a satellite image time-series of main dams supplying Cape Town with water. What a brilliant idea! But where were these 6 main (and 8 minor) water sources in the Western Cape? - I sought to answer that.

##### You can - [Cut To The Chase](https://erickndava.github.io/dams-of-capetown/index.html)!


### Think Water, Find Dams

<img align="center" src="/images/think-less-than-87.png" alt="Think Water, Think Less Than 87L per day">

To get me started I got the Dam Names off the City of Cape Town's [Open Data Portal](https://web1.capetown.gov.za/web1/opendataportal/). Search term "dams" yields a csv file of Dam levels, (*Dam levels update 2012-2017.csv*). This listed all the 14 water supply sources, with storage capacities. I Googled the locations for these and had X, Y coordinates for these.

I planned on having a story map of sorts to help the 'gazer' have an idea where the water sources where. I settled for [JackDougherty](http://commons.trincoll.edu/jackdougherty/)'s template on [GitHub](https://github.com/jackdougherty/leaflet-storymap). This was particularly attractive because it had LeafletJS in the mix and some GeoJson. My mind was set on the map portion of [this](https://www.nytimes.com/interactive/2016/07/07/world/americas/bolivia-climate-change-lake-poopo.html) excellent visualisation which proved to be too complex to emulate. I also considered [Odyssey.js](https://cartodb.github.io/odyssey.js/) which turned out to be unpolished and kinda project abandoned.

It didn't take long to have the scrollable map-story for the dams. After following the instructions on the GitHub Repo and editing a few lines in Sublime Text.

[See Full Version](https://erickndava.github.io/dams-of-capetown/index.html)

<iframe width="100%" height="520" frameborder="0" src="https://erickndava.github.io/dams-of-capetown/index.html" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>


### Credits

The following sources were used for the Dams Narratives.

1. [Cape Water Harvest](https://capewaterharvest.co.za/cape-town-dams/) 

2. [Hike Table Mountain](http://hiketablemountain.co.za/table-mountain-walks-reservoirs/)

3. [The Table Mountain Fund](http://www.thetablemountainfund.org.za/why-are-there-five-dams-on-top-of-table-mountain/)

4. [Cape Trekking](http://capetrekking.co.za/table-mountain-history-woohead-dam/ )

and the City of Cape Town website for dam capacities.



