---
title: Quick Start Guide
permalink: /docs/:path/
layout: documentation
---

If you already have a GJS environment installed (see Obmin's [dependencies](/docs/01_install/#dependencies)), you can  download [latest zip package](https://github.com/konkor/obmin/raw/master/releases/obmin%40konkor.zip), unpack it and start the server just from Terminal:

```sh
# cd to uncompressed folder
cd obmin@konkor
# Run the server
./obmin-server

# Now browse to http://localhost:8088 (8088 port is a default value)
```

If you are running Obmin first time, you should see something like this:

<p><img src="{{ "/assets/images/docs/default_page.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/></p>

Now you can start to browse your home folder by default. After you can check your local IP address to an example in a terminal like this:

```sh
# Method 1
hostname -I

# Method 2
ip addr show

# Method 3 is require ROOT
sudo ifconfig

# You can use Network Manager setting or
# Obmin applets to find your addresses so
```

You can check it from other device/PC/tablet/etc connected to your local network. If your local IP address is 192.168.1.10 to example, enter the `192.168.1.10:8088` in the address bar of an Internet browser and you should see the similar page.

There are many ways to configure your settings. It depends on your installation and your desktop environment. You can find more in further sections about the installation, configuration and running.
