---
layout: post
title:  "One year of development."
date:   2018-06-25 15:00:00 +0200
categories: obmin news
description: "I'm a big fan of open-source software, community and platforms. I have developed many things but now I'm focused on a few my open-source projects for Linux desktop users. Linux have a lot of fun things but most of them are production oriented and supported by huge corporations and other businesses."
image: "/assets/images/posts/welcome.jpg"
comments: true
author: "konkor"
---

<img alt="WELCOME" src="{{ "/assets/images/posts/welcome.jpg" | relative_url }}" align="left" style="margin:0 8px 16px 0; width:100%">

## Hello there!

<p> I'm a big fan of open-source software, community and platforms. I have developed many things but now I'm focused on a few my open-source projects for Linux desktop users. Linux have a lot of fun things but most of them are production oriented and supported by huge corporations and other businesses. We all are happy that we can use such things like production ready servers, containers, frameworks in our life. It's awesome to able to build dedicated servers just like big brothers at our homes. But it's not always efficient in daily life when you want just things be done time to time or just don't have time or resources to administrate or monitor it. It's why I started to develop own file server for ordinary desktop user needs. But it doesn't mean the Obmin server you cannot use for tasks in your office network or teams. The server part and user graphical tools for monitoring, configuration are in different layers. You can run the server part from command-line interface with defined in JSON file. So it's just weird to do not use all network power of Linux on desktops too.
</p>

<p/> It was almost one year ago when I decided to make own file sharing server for Linux! First version was released 18 july 2017 on [extensions.gnome.org site](https://extensions.gnome.org/extension/1254/obmin). You can ask me why there are tons of servers, especially, on Linux for any kind of tasks. Also, there is a swarm of protocols and online services for a sharing any kind of data. Right, but the truth is more complicated as whole real life. Some of the solutions are overcomplicated and not easy to monitor them. Some need special clients and not available widely. Some want the Internet connection and limited by size and speed. Public services are not private and so on.
<p/>

### _Actually, why I decided to make the server?_
<p/>
I lost my NAS and moved HDD drives to my desktop workstation. I have already used to NAS. It was convenient to watch movies, show photos, listen music or just share something to any device in my home network. I tried a lot things from SAMBA, WebDAV to Rigel but it was not convenient to use all of it on different platforms and devices like tablets, smartphones, Smart-TV. Especially, if you prefer open-source solutions to do such things. Also it's not efficient to run all that things on a desktop 24 hours per day. On other side, every platform, smart device have HTTP protocol support and powerful Internet browsers. It allows to share everywhere on any OS or any device.

<p/>
I decided to build own server to achieve next things:
1. It should be integrated to already existent desktop framework. It would allow to save system resources and make better integration to desktops. I chosen GLib/Gtk framework. It's available on most Linux desktops and using by all major applications from LibreOffice to Firefox.
<img alt="WELCOME" src="{{ "/assets/images/posts/welcome2.png" | relative_url }}" align="right" style="margin: 16px 16px 8px 24px; width:35%">
2. I wanted it to be on-demand server. So it doesn't use any resources when it's not running.
3. All things should work locally without external calls, frameworks by default.
4. It has to have user-friendly tools for a configuration, monitoring and launching.
5. It must have modern responsive design and nice looking.

### _One year of the development_

After this year we have a full-featured Internet server for many kind of tasks (see [features page]({{ "/about" | relative_url }}) for more details).
We have HTTP support ranges, chunked downloading, multiple connections, digest authentication and more. The server can serve/stream any files with any amount of data.
The server has own plugin system to enhance features for your needs. It's fully supporting secure layer of HTTPS protocol for end to end encryption between clients and the server. It has user-friendly graphical tools for any kind of Linux desktops. There are several server plugins to generate filelists for media players, dowloaders, a slideshow plugin to view photos with supporting auto-rotation, preview compressing and RAW images through the dcraw package. There is nice real-time directory compressor for some popular formats (zip, gzip, bz2, xz). It allows to download complex project's folders in single request and save a lot of time and bandwidth. Here are much more features and abilities you have to check it out yourself. There are created [G+ community](https://plus.google.com/communities/111793545135238329562) and this [site](https://obmin.github.io) :)
<p/>

### _What's next?_
<p/>
There are a lot of things to do. First, it's supporting exist features, new releases and distros. I'd like to write a documentation for the applications and plugins API to make it easier to start using and enhance it. There are plans to make docker version of the server and web applets to easy deploy own external server for VPN, HTTP proxies. It's nice to have web control panel, enhance security, notifications and many other things.

<p class="description">
This project was possible only by wasting a huge amount of time. I had a hope you will support the project. But after year I have nothing yet. So I'm asking for your donations to able be to continue the development. Now you can go to the Support Page in the preferences window and make a donation via PayPal service. Later I'm going to make a Patreon page so. If you can support the project in other way let me know.
</p>

_The author, konkor._
