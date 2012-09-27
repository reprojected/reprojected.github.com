---
layout: post
title: "Where did all my space go"
date: 2012-09-27 15:01
comments: true
categories: 
---

So I am sitting here on my trusty Ubuntu workstation in the office and realised I am running out of space.  Well, here is an easy command to find out where your top offending directories are:

    du -h --max-depth=1 | sort -rh | head

Here it is in action:

    aaronr@aaron-zlinux-office1:~$ du -h --max-depth=1 | sort -rh | head
    146G                           .
    52G                            ./.VirtualBox
    34G                            ./downloads
    18G                            ./work
    12G                            ./Dropbox
    8.9G                           ./VirtualBox VMs
    7.5G                           ./.local
    4.0G                           ./purgatory
    1.5G                           ./tmp
    1.4G                           ./vm_shared
    aaronr@aaron-zlinux-office1:~$ 

`du` to look from your current location down (recurse), `-h` for human readable, `--max-depth=1` so you just get top level dir summaries... piped into `sort` in reverse order with `-r` and top that off with `-h` to make sure it sorts on human readable sizes... finally pipe that into head to look at the first 10 with an optional `-n 20` to look at more.