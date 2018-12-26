---
layout: post
title: "Saving A One to Many 'Join' in QGIS"
date: 2018-06-15 12:18:50 +0200
summary:  Data Processing 
comments: true
sharing: true
categories: hands-on
thumbnail: fa-chalkboard-teacher
tags:
 - qgis
 - sql
 - geopackage
 - data processing
 - analysis
 
---

### When A Relate Won't Do

While working on the next part of my [series of blogs](https://erickndava.github.io/idea/2018/05/24/a-city-with-data/) I ran into an interesting 'discovery' which warrants an interjection. Testing the data loads into a geopackage, I decided to join a spatial and attribute data AND retain the results as a new 'layer'. Tools in the QGIS Processing didn't help much. So I Googled for a solution. To my surprise I got a few first time hits. I learnt MapInfo can do it so can ArcMap. There we also suggestions of having a relate in  QGIS. But, that's not what I sought.

Buried in a Google Forum was the solution by Thomas McAdam. So here's how I ended up doing it ... so we have one more source for the solution on the web.

### Love The Database

A pre-requisite to the procedure is to have the data stored in some database and that's not scary at all. I explain one way to doing that [here](https://erickndava.github.io/hands-on/2018/06/01/in-with-the-new-geopackage/) creating a Geopackage. You can also create a SQLite Database as explained [here](https://docs.qgis.org/2.8/en/docs/training_manual/databases/spatialite.html). You don't even have to leave the comfort of Q while doing it. 

### A One To May (1-M) Join

With the objective of joining two datasets and keeping the results. The assumption is that your data is clean and you have common fields between your two datasets.

- Table 1: suburbs - Has polygons of suburbs I wish to join (*One Record*).
- Table 2: land_disposals_2009_2018  - which has sales records per suburb (*Many Records*).

<img align="center" src="/images/1_two_tables.PNG" alt="Two tables">

Now, with the target datasets loaded in a 'spatial database' as suggested above.

- From within Q, Launch DB Manager to access the geopackage (*in my case, explained [here](https://erickndava.github.io/hands-on/2018/06/01/in-with-the-new-geopackage).*)

- Select the appropriate database/ geopackage then
- Launch the SQL Window.

<img align="center" src="/images/2_sql_windows.PNG" alt="SQL Window">

- Within the window write SQL Statement to JOIN our **suburbs** with the **land_disposals_2009_2018** table.

Which translates to 

~~~
SELECT  *
FROM suburbs
JOIN land_disposals_2009_2018
ON suburbs.alt_name = land_disposals_2009_2018.area;
~~~

Simply put this says, *"Basing on the common valued fields **alt_name** and **area** of the suburbs and land_disposals_2009_2018 layers respectively, join these two."* 

- Click on Execute to see what results this gives. (*An inspection will help verify the legitimacy of the operation we just ran.*)

- Tick the ***Load as new layer*** Check Box near the bottom of the SQL Window.
- Tick the ***Geometry column*** Check Box. (Selecting a value that looks/ read something like geom).

- Now click on ***Load now!*** to have the results display in Q.

<img align="center" src="/images/3_load_in_q.PNG" alt="Load Results to Q">

### Results, If You Please.

On clicking Load Now! The Q canvas will fill with spatial, familiar ground!

To Save the results, Right Click the layer name in Q, Save As and we can save to any format supported by Q to our heart's content.

### #PostScript

The JOIN used here is an overly simplified approach to tip-top SQL queries. I would recommend intensive reading up on the JOIN operation as things can really go wrong surreptitiously.
