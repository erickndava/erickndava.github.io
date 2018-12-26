---
layout: post
title: Anything for a Map - Part 1
date: 2015-09-04T03:53:36+02:00
summary:    Finding something to map.
categories: technical tutorial
thumbnail: map-marker
tags:
 - hands-on
 - tutorial
---
### On The Heels of The Pioneer Corps

Mapping the footprints of the men who faced the thicket, built drifts
across rivers, played the debut soccer and rugby matches in a country.

### Background

So, as I was working on some project and the corresponding write-up for
a blog post, I got a ‘technology’ interruption. The key data for the
project was ready now and the other processing was still ongoing
TileMill, GDAL, ASTER.. what not.

[CartoDB](cartodb.com) was the interruption and particularly
[Odyssey.js](http://cartodb.github.io/odyssey.js/). My (initial)
intention was to make a pannable map with an ‘old’ theme. Since this was
going to be a spatio-temporal kind of a map I decided to give Odyssey.js
a go.

### Tire-kicking

So in one afternoon I had a reasonable visualisation going! Having a
CartoDB account was one of the requirements for this exercise and I had
long back signed up for a free account when CartoDB came on to the
scene. I went with the Torque Template on
[Odyssey.js](http://cartodb.github.io/odyssey.js/). The point data I
uploaded to my CartoDB account, simply added a ‘integer’ field to
represent time. It wasn’t difficult to figure out how the story could be
put together using Markdown. And after two hours or so….voila!

[The Map Story](http://bl.ocks.org/anonymous/raw/f850a15e428eb2f2e490)

#### \#postscript

-   The experience I had with Markdown helped me to quickly compile my
    story.
-   I used a [great tool](https://github.com/benbalter/github-uploader)
    by Ben Balter to upload a document of the narrative I used to plot
    the points in the visualisation to my GitHub account via the
    browser!
-   Apart from the expediency with which one can make a animated
    visualisation of one ’s data, there’s somewhat a restriction on the
    cartography front. Thus I will still continue with my initial
    intention on creating an old map.
-   Take away from all this is that there are great tools out there to
    help one do great things with minimal effort.

