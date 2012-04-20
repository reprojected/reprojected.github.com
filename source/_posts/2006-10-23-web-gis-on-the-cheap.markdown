---
date: '2006-10-23 17:30:48'
layout: post
slug: web-gis-on-the-cheap
status: publish
title: Web-GIS on the cheap...
wordpress_id: '8'
categories:
- GIS Tool Install
---




OK, I have servers at work that I use daily to develop Mapserver/GDAL/OGR/GRASS/GMT/etc... based apps, but how about on a shared hosting environment?

Well, I finally got it going. I have written up my [install instructions](http://media.reprojected.com/geoblog/?page_id=6) for Mapserver/GDAL/OGR/Proj/Postgres/Postgis/Geos/GMT/GRASS on [Dreamhost](http://www.dreamhost.com), a debian based shared hosting service. The great thing about it...

**1)** It cost $9.95/month (1 year contract) *12 = $119.40

**2)** You can use a discount code to get $97 off... Total cost at sign-up = $119.40-$97 = $22.40

UPDATE (12/09/06): I just created a propmo code that gives the FULL discount to you... Nothing to me.  It is **ZPULLEYFULL **, enjoy! 

**3)** Add a domain for $9.95 and the first year of this site cost $32.35 ... WOW

With this [package](http://www.dreamhost.com/shared) I get 200 Gigs of space (grows weekely!) and 1 Terabyte of bandwidth/month (grows weekly!).

So what good is it if I cant do some mapping work with it? Well, I have posted notes how I was able to get a fully functional Mapserver/PostGIS environment up. I went as far as to get command line GRASS installed to do geo-processing sans the GUI. GMT installed like a breeze, and bammmm... a GIS work environment.

Cant beat the rent ;-)

Check out some demo's running on the server:

**1)** [ka-map](http://media.reprojected.com/apps/ka-map/)

**2)** GMT

pretzel:~/usr/local/src/gmt/GMT4.1.2/examples> ./do_examples.csh
Doing example 01...done
Doing example 02...done
Doing example 03...done
Doing example 04...done
Doing example 05...done
Doing example 06...done
Doing example 07...done
Doing example 08...done
Doing example 09...done
Doing example 10...done
Doing example 11...done
Doing example 12...done
Doing example 13...done
Doing example 14...done
Doing example 15...done
Doing example 16...done
Doing example 17...done
Doing example 18...done
Doing example 19...done
Doing example 20...done
Doing example 21...done
Doing example 22...done
Doing example 23...done
Doing example 24...done
Doing example 25...done
Completed all examples
pretzel:~/usr/local/src/gmt/GMT4.1.2/examples>

[Check out the Output Images](http://media.reprojected.com/apps/gmt/)

**3)** GRASS

IMPORT ------>

`GRASS 6.1.cvs > r.in.gdal input=world-topo-bathy-97_32_84_24.tif output=bmng_grass location=blue_marble
A datum name wgs84 (WGS_1984) was specified without transformation parameters.
Note that the GRASS default for wgs84 is towgs84=0.000,0.000,0.000.
100%
CREATING SUPPORT FILES FOR bmng_grass.red
SETTING GREY COLOR TABLE FOR bmng_grass.red (8bit, full range)
100%
CREATING SUPPORT FILES FOR bmng_grass.green
SETTING GREY COLOR TABLE FOR bmng_grass.green (8bit, full range)
100%
CREATING SUPPORT FILES FOR bmng_grass.blue
SETTING GREY COLOR TABLE FOR bmng_grass.blue (8bit, full range)
r.in.gdal complete.
Mapset  in Location
GRASS 6.1.cvs>`

VERIFY ------->

`Welcome to GRASS 6.1.cvs (2006)
GRASS homepage:                          http://grass.itc.it/
This version running thru:               TC Shell (/usr/bin/tcsh)
Help is available with the command:      g.manual -i
See the licence terms with:              g.version -c
Start the graphical user interface with: gis.m &
When ready to quit enter:                exit
Mapset  in Location  GRASS 6.1.cvs > g.list type=rast
----------------------------------------------
raster files available in mapset PERMANENT:
bmng_grass.blue  bmng_grass.green bmng_grass.red`

`----------------------------------------------
Mapset  in Location  GRASS 6.1.cvs>`

Thats it for now... Up and running!!!!!!
