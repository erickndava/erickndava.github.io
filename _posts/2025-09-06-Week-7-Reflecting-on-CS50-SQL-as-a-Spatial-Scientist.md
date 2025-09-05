---  
layout: post  
title: "Week 7: Reflecting on CS50’s SQL as a Spatial Scientist."  
date: 2025-09-06T01:15:00+02:00  
categories: CS50 Data Science PGDip Journey GIS  
tags:  
- CS50  
- C Programming  
- Spatial Science  
- PGDip  
- Learning to Code  
description: "Deciding to deep-dive into Data Science, leveraging  spatial data expertise and writing about the break."  
draft: false  
---  
  
As opportunity would have it, this week I was on a work sponsored  [esri](https://esri.com) training course, [ArcPro Advanced](https://www.esri-southafrica.com/wp-content/uploads/2021/08/ArcGIS-Pro-Advanced-Course-Outline.pdf). One of the topics covered was Simple SQL Queries. CS50's SQL Topic became an opportunity to re-learn SQL, dive deeper and master the proper crafting of queries.  
  
The first part turned out to be a great easy-going refresher. As a spatial scientist I ask spatial data questions all the time. As geohipsters, we actually have a cute file format, [geopackage](https://www.geopackage.org/) which is essentially a sqlite database. In the course of the material. I couldn't help reminisce [PostGIS]([https://postgis.net/](https://postgis.net/)) and [SpatialSQL]([https://postgis.net/workshops/postgis-intro/geometries.html](https://postgis.net/workshops/postgis-intro/geometries.html)). I have a decent [exposure to SQL]([https://erickndava.blog/hands-on/2019/07/25/a-data-science-doodle-3-the-data-spatial-part-2/](https://erickndava.blog/hands-on/2019/07/25/a-data-science-doodle-3-the-data-spatial-part-2/)) but, further on with Week 7 content, queries became complex and my learning began to compound.  
  
I noticed a personal preferance when it came to constructing queries, favouring  
```sql  
JOIN ... ON ... ---Inner Table Joins  
```  
versus  
~~~sql  
SELECT ... FROM ( SELECT ... ---Subqueries/ nested SELECT statements  
~~~  
Which was an interesting introversion of how I understood things. At the end of it, it was great mastering the alternative.  
  
The brief discussion of SQL Injection attacks during lectue was very intriguing. A peek into cybersecurity.  
  
## Learnings for the geo-person  
  
1. Geospatial software leverage relational databases ubiquitously. As such, the topic of databases is one that cannot be side stepped in the profession. It is one that can actually be divergent, as some projects demand tools which emphasise data storage versus a spatial view. Few years back I was intrigued by a command line [spatial data viewer]([https://github.com/robe2/node_postgis_express](https://github.com/robe2/node_postgis_express)) which connected to PostGRES with a PostGIS extension. Not long [DBeaver]([https://dbeaver.io/](https://dbeaver.io/)), a universal databae tool, debuted with a [spatial viewer]([https://erickndava.blog/2019/05/07/button-pushing-gis-analyst-not/](https://erickndava.blog/2019/05/07/button-pushing-gis-analyst-not/)).  
Something that was domain specific to GIS.  
  
2. A great geospatial scientist should know above average SQL. Increasingly, it is apparent that spatial is just another column in the database. But the gis tech, has the advantage of spatial thinking.  
  
3. After completing this section, I can now do nested and more complex queries. Behind every icon in the spatial manipulation software GUI. The ready to use _Intersect_ icon, is actually a  
  
	```sql  
		SELECT spatial_features FROM spatial_table_A  
			JOIN spatial_table_B  
			ON spatially_congruent_features
	```  
4. My greatest gain from this section was learning to work with database informaton programmatically. This came through the [Fiftyville]([https://cs50.harvard.edu/x/psets/7/fiftyville/](https://cs50.harvard.edu/x/psets/7/fiftyville/)) task of Problem Set 7.  
  
7. In all honesty, I underestimated the depth of topic for this section. It was a great break from general purpose programming and I learnt much much more on SQL. I now appreciate better, the responsibilities of a DBA. The prospects of the average geospatial scientist expanding into webmapping and scripting become greater.
  
That's Week 7, now looking forward to HTML, CSS and JavaScript. Again topics not too foreign but another opportunity to re-learn stuff. As a parting note...Little bobby tables  :laughing: .

```sql
`Robert'); DROP TABLE Students;--`?
