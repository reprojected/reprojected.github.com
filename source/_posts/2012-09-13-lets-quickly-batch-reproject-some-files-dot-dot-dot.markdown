---
layout: post
title: "Lets quickly batch reproject some files..."
date: 2012-09-13 12:02
comments: true
categories: 
---

Lets say we have a directory full of .jpg files that are geo-referenced (could be any extension like .tif as well):

    for f in *.jpg; do gdalwarp -t_srs EPSG:900913 $f ${f/.jpg}_900913.jpg; done

Boom... that simple.  Love GDAL.
