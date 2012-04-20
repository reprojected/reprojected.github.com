---
date: '2006-10-23 17:31:34'
layout: post
slug: adding-session-based-data-store-for-chameleon-based-apps
status: publish
title: Adding SESSION based data store for Chameleon based apps.
wordpress_id: '16'
categories:
- GIS Tool Use
- GIS Tools
---

I have had a great need for a directory structure like the following in my Chameleon based apps:

**_SESSION_DIR
|
--->data
|
--->base_data (Base data shared with all apps on file server)
|
--->app_data (Application specific data residing on local server)
|
--->dyn_data (User specific dynamically generated layers)_**

The way I have tackeled this is to create a new directory in the session space of the Chameleon app and create symbolic links for the base and application data to common data storage areas on my file sservers.  Lastly a new directory is created in that session data directory for dynamically created data.  Pretty basic, but many questions have been asked to me about this, so here is an example.

**index.phtml**

`// Make sure we have a data dir that is session based:
// sessionSavePath/data/base_data -> symbolic link to base data dir (shared)
// sessionSavePath/data/app_data -> application specific data (shared)
// sessionSavePath/data/dyn_data -> user specific dynamic data (not shared)
// If the directory does not exist, then we need to make one.
$data_dir = getSessionSavePath()."/data";
$data_base_dir = $data_dir."/base_data";
$data_app_dir = $data_dir."/app_data";
$data_dyn_dir = $data_dir."/dyn_data";
//save the current application working directory
$cwd = getcwd();
if  (!file_exists($data_dir))
{
// Here we make the session data dir
$dir_exec = sprintf("mkdir ".$data_dir);
exec ($dir_exec,$arr,$err1);
$_SESSION['sessDataDir'] = $data_dir;
// Here we make the user dynamic data dir
$dir_exec = sprintf("mkdir ".$data_dyn_dir);
exec ($dir_exec,$arr,$err1);
// Here we make the base data link
$dir_exec = sprintf("ln -s ".
``$cwd."/../../base_data ".$data_base_dir);
exec ($dir_exec,$arr,$err1);
// Here we make the app data link
$dir_exec = sprintf("ln -s ".
$cwd."/../app_data ".$data_app_dir);
exec ($dir_exec,$arr,$err1);
}
// Finally we modify the data path of our map object
$oMap = $oApp->moMapSession->getMapObj();
$oMap->set("shapepath", $data_dir);`
** **

**mapfile.map**

`# For base data items
DATA Political/counties.shp
becomes...
DATA base_data/Political/counties.shp```# For app specific data
DATA Marinezones/contiguous_us_eez.shp
becomes...
DATA app_data/Marinezones/contiguous_us_eez.shp```
`# For dynamic data
Most apps will just create a layer dynamically in Mapscript and point the data statement toward the dyn_data directory.``

That is it.  Pretty basic, but allows you to keep your data separated between base data all apps will use, application specific data, and data that is generated dynamically by users on the fly.
