---
layout: post
title: "simple psql formating tips"
date: 2012-09-27 13:17
comments: true
categories: 
---

So you are neck deep in `psql` and are doing some queries... but the output looks like crap and the pager keeps getting in your way.

{% img center /images/simple_query_result.png Horible Output %}

First... turn off the pager

    \pset pager

Next, turn on expanded display

    \x

Now... things look a bit better.  You dont loose your initial page by going into the pager, and your output is readable.  This is especially true for very wide columns as is always happens with GIS data in postgis.

{% img center /images/simple_query_better.png Better Output %}
