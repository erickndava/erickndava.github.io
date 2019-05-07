---
layout: post
title: "Button Pushing GIS Analyst, Not"
date: 2019-05-07 18:10:28 +0200
summary:  Thoughts
comments: true
sharing: true
thumbnail: idea
tags:
 - data wrangling
 - career
 - pc
 
---

##### SCT Part 5

### Loading...

<img align="center" src="https://media.giphy.com/media/3oxHQqRipgdX219Zdu/giphy.gif" alt="What to do">

When the year began, I resolved to blog at least twice a quarter. That has proved to be too ambitious. The 'distraction' has largely been a [dirty dataset](https://twitter.com/erickndava/status/1111277809257889792) I was, still am, cleaning. You see, I am now a wannabe *Geo*-Data Scientist. This hype and perception of self has been influenced by endless periods of watching [Pyception](https://www.youtube.com/watch?v=UXd0EDy7aTY). I am proudly, progressively going through the book, **R for Data Science**, affectionately known as [R4DS](https://r4ds.had.co.nz/). Honestly one of the spurring factors are the cool and sophisticated looking graphs made with ggplot.


### Map Monkey
Since learning about it, I have tried as much as possible to not myself mold into a 'Map Monkey' or 'Button-Pushing' GIS Analyst. This year I have taken up *Data Science*, the buzzword of the moment right? I see M.L. and A.I. are trending actually. As a geospatial specialist there is demand for one to be a 'data manager' already. Map production or results from a spatial analysis demand one massage data in one way or the other. Taking on stuff about data and some stats shouldn't be too foreign. So in the first quarter of 2019 I was setting up my machine for Data Science and studying the same. It was pleasant to discover that <a href="http://darribas.org/gds18/" target="_blank">Geographic Data Science</a> is actually a thing and I am not being very divergent from years I have already invested in work and study.

So here's a peek of what's on my PC. 

<img align="center" src="/images/On_my_pc.PNG" alt="What Is On My PC">

I chose Chocolatey to spare me hours of troubleshooting dependency, local installation paths issues with Node, Yarn, et. al. I must mention though that having DBeaver running wasn't straight forward. The solution came from [here](...) and some of the screamed at screen shots are shown below.

<img align="center" src="/images/dbeaver_screenshot1.PNG" alt="Make DBeaver work1">

<img align="center" src="/images/dbeaver_screenshot2.PNG" alt="Make DBeaver work2">

I cannot, not mention <a href="https://github.com/keplergl/kepler.gl/blob/master/contributing/DEVELOPERS.md" target="_blank">kepler.gl</a>, the reason I have Yarn up there. Kepler.gl is any spatial data visualisation enthusiast's goldmine. You look like a pro with very little effort. I have gone through various blog posts and video tutorials to try and <a href="http://think-like-a-git.net/" target="_blank">Think Like (a) Git</a>  with minimum success. So hopefully my learning R accompanied by <a href="https://happygitwithr.com/rstudio-git-github.html" target="_blank">version control</a> with the help of <a href="https://desktop.github.com/" target="_blank">GitHub for Desktop</a> should help. See, I have been abusing GitHub for just an online storage and blog hosting space...none of the version control functionality.


### Endearing Geo

I still love my geo, so when I hit a wall with the Data Science 'things', I fire up QGIS and dabble my spatial data in PostGIS. As one who is a tinkerer, I picked somewhere that SQL skills are an important must have for a geo person, moreso Spatial SQL. ( <a href="https://medium.com/@tjukanov/why-should-you-care-about-postgis-a-gentle-introduction-to-spatial-databases-9eccd26bc42b" target="_blank">This article</a> makes a great read on the importance of SQL for a geo person and how to get started. My blog chronicles my personal path of the same).

<a href="https://www.enterprisedb.com/downloads/postgres-postgresql-downloads" target="_blank">EnterpriseDB</a> distros of PostgreSQL really make the installation and configuration of PostGIS a breeze. Within minutes one has access to a functional sandbox and production ready space. Through click click, type type I had PostGIS ready.

<img align="center" src="/images/PostgreSQL.PNG" alt="PostgreSQL Installation">

<img align="center" src="/images/PostGIS Version.PNG" alt="PostGIS Installation">

 DBeaver has become a dear companion navigating the SQL land, with the plus of a progressively improving spatial view. DB Manager in QGIS is a great go-to when QGIS if fired up.

<img align="center" src="/images/dbeaver_map.PNG" alt="DBeaver for SQL">

Still I cannot just dash over the ability to view spatial from within a database (DBeaver) environment. <a href="https://www.pgadmin.org/download/pgadmin-4-windows/" target="_blank">PgAdmin 4</a> has a spatial viewer but a little more Googling tends to put one off when it comes to the design of PgAdmin 4. There also have been efforts to have a simplistic spatial viewer, my favourite being <a href="https://github.com/NYCPlanning/labs-postgis-preview" target="_blank">PostGIS Preview</a>, although I [haven't been able](https://github.com/NYCPlanning/labs-postgis-preview/issues/55) to make it work yet. Sometimes it is good to be able to see 'map' data without having to fire up a GIS program. Which makes spatial data view in DBeaver celebratable ...enforcing the notion of "spatial is just another table in the database" aka spatial is not special. Well, it is special when you need to know about EPSG codes and why, when to use which.

New and shiny get's my attention, so I have also tried [Azure Data Studio](https://docs.microsoft.com/en-us/sql/azure-data-studio/download?view=sql-server-2017) just for the [*preview PostgreSQL extension*](https://azure.microsoft.com/en-us/blog/azure-data-studio-an-open-source-gui-editor-for-postgres/). This release was  apparently a [big thing ](https://www.theregister.co.uk/2019/03/19/postgresql_azure_data_studio/). I experimented with it a bit, connected to my PostGIS and decided to settle on DBeaver. 
*"Be really good at one thing"*, right?


#### #PostScript


So I'm off to learning R, SQL and git just to be *Button Pushing GIS-Analyst, Not*. The next blog post should be about Data Science, Geo Data Science.
