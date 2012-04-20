---
date: '2009-02-06 14:08:12'
layout: post
slug: debugging-qgis-plugins
status: publish
title: Debugging QGIS Plugins...
wordpress_id: '73'
categories:
- General
- GIS Tool Dev
---

Well, the title might better read "debugging [PyQt](http://www.riverbankcomputing.co.uk/software/pyqt/intro) applications...", but much of my PyQt foo happens when developing [QGIS plugins](http://qgisplugins.z-pulley.com/). In general I am old school... [emacs](http://www.gnu.org/software/emacs/) and [gdb](http://www.gnu.org/software/gdb/) are my friends. When it comes to developing in PyQt there is one life saving code snip that will make your life much easier:

    
    from PyQt4 import QtCore
    import pdb
    ...
    QtCore.pyqtRemoveInputHook()
    pdb.set_trace()


This not only sets a trace (breakpoint) in your code, but it stops the PyQt event loop. The call to [pyqtRemoveInputHook()](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#using-pyqt-from-the-python-shell) is a tasty little tidbit in PyQt to allow for this "stop it in it's tracks" behavior.  This is a must have for debugging PyQGIS or Python based plugins.

Once you are in [pdb](http://docs.python.org/library/pdb.html), you are set to go with interactive debugging:

    
    --Return--
    > /home/aaronr/.qgis/python/plugins/refmap/refmap.py(101)__init__()->None
    -> pdb.set_trace()
    (Pdb) bt
    <string>(1)<module>()
    /home/aaronr/.qgis/python/plugins/refmap/refmap.py(144)initGui()
    -> self.refmap_gui = ReferenceMapWindow(self.iface,flags,self)
    > /home/aaronr/.qgis/python/plugins/refmap/refmap.py(101)__init__()->None
    -> pdb.set_trace()
    (Pdb) print self
    <refmap.refmap.ReferenceMapWindow object at 0x8cc6c2c>
    (Pdb) print self.iface.mainWindow().windowTitle()
    Quantum GIS - 1.1.0-Unstable-trunk
    (Pdb)


Happy debugging!!!
