---
date: '2007-10-11 09:55:56'
layout: post
slug: getting-qgis-to-install-on-windows-and-support-python-apps
status: publish
title: Getting QGIS to install on windows AND support Python apps...
wordpress_id: '51'
categories:
- GIS Tool Install
---

So here are the simple (kind of) steps as of today to get a windows install of QGIS working that supports PyQt and the python bindings to QGIS... all with out having to compile anything:

1) Make sure you have Python 2.5 or newer installed on your machine... if you don't have it you can download it from [HERE](http://www.python.org/ftp/python/2.5.1/python-2.5.1.msi) (official) or [HERE](http://media.reprojected.com/qgis_dev/dev_files/qt4.3.1_based/Python/python-2.5.1.msi) (my archive).

2) Install PyQt4.3.1 from [HERE](http://www.riverbankcomputing.com/Downloads/PyQt4/GPL/PyQt-Py2.5-gpl-4.3.1-1.exe) (official) or [HERE](http://media.reprojected.com/qgis_dev/dev_files/qt4.3.1_based/PyQt/PyQt-Py2.5-gpl-4.3.1-1.exe) (my archive)

3) Download and unpack [THIS](http://media.reprojected.com/qgis_dev/dev_files/qt4.3.1_based/PyQt/PyQt4.zip) zip file.  Copy the PyQt4 directory unpacked from the zip into your Python 2.5 site-packages directory.  Make sure to save the old PyQt4 directory in the site-packages by renaming it in case something goes wrong!

4) Download and install QGIS from [HERE](http://media.reprojected.com/qgis_dev/dev_files/qt4.3.1_based/QGIS/qgis_setup0.9.0.11_10_2007.exe) (my archive).  This is the latest release candidate from what_nick that is based on the Qt4.3.1 series.

5) In the QGIS install there are some GRASS documentation files that are missing and can cause warning dialogs to pop up when using the GRASS toolbox.  You can unzip the contents of [THIS](http://media.reprojected.com/qgis_dev/dev_files/qt4.3.1_based/QGIS/qgis0.9_grass_docs.zip) archive into the QGISDIR\grass\docs\html directory to stop the warnings.

You can still follow the instructions [HERE](http://wiki.qgis.org/qgiswiki/BuildingFromSource) to build QGIS yourself and play to your hearts content, but I know that there are many windows users out there that really would just like to get moving without the hassle of compiling.  This post is for you.

