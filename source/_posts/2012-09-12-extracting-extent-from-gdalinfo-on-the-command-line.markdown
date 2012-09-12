---
layout: post
title: "Extracting extent from gdalinfo on the command line"
date: 2012-09-12 13:00
comments: true
categories: 
---
Had a question on #gdal IRC yesterday on how to get the extent from `gdalinfo`.

Well... here is some command line hackity hack to get it in a format that can be passed into things like `gdal_translate` with the `-projwin` flag:

    gdalinfo my.tif | awk '/(Upper Left)|(Lower Right)/' | awk '{gsub(/,|\)|\(/," ");print $3 " " $4}' | sed ':a;N;$!ba;s/\n/ /g'

From this you get some simple output of the UL and LR corners of the image:

    418081.036 3613108.883 1589231.036 2678608.883

Hope that helps someone else out...