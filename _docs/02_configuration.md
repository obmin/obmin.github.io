---
title: Configuration
permalink: /docs/:path/
layout: documentation
---

We will observe the server settings here. Other settings for UI and system integration components we will overview in the next sections. So all settings we could divide on three general types:
* JSON file configuration settings (highest priority);
* Stored settings in GSettings (normal priority);
* Default settings (lowest priority).

So if you passed some settings to server via a configuration file in JSON format, they will override all settings. If you not defined some settings in JSON the server will take them from the stored settings. Otherwise it will use default settings.

Here are a few graphical components to help to configure your server settings. You can do it in:
* Obmin Center application on the Settings Tab (obmin-center);
* Obmin Preferences application (obmin-preferences);
* You can call Obmin preferences via Obmin Extension Preferences on Gnome desktop.

## Shared Locations Editor
Here is all simple. Just press Plus Button to add new source locations. You can change a source type, FOLDER or just FILE, select desired files, and tell if a folder source should have a recursion or not.
<p><img src="{{ "/assets/images/docs/prefs_locations.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-preferences</b> Locations Editor Page where you can define whats to share.</p>

## General Tab / Server behavior

<p><img src="{{ "/assets/images/docs/prefs_general.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-preferences</b> General Page where you can define the server's behavior.</p>

## Network Settings
You can change the server's listening port here. Also you can configure TLS Certificate for HTTPS connections and set username/password for HTTP Authentication on the client side.
<p><img src="{{ "/assets/images/docs/prefs_network.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-preferences</b> Network Page where you can define the server's listening port and other network security settings.</p>

## Content Settings
You can choose a web client theme and which file system types to show like mount points, symbolic links, hidden content or backups.
<p><img src="{{ "/assets/images/docs/prefs_content.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-preferences</b> Content Page to choose what will see a web client.</p>

## Notifications Tab
There are a debugging level for the log output, an option to enable/disable file logs in addition to SystemD journal logs and a switch for sending messages about server activity.
<p><img src="{{ "/assets/images/docs/prefs_notify.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-preferences</b> Notifications Page for logging and monitor options.</p>

## JSON File Configuration

Here is a sample of the full JSON file configuration for OBMIN Server:

```json
{
"port":8087,
"mode":0,
"debug":1,
"mounts":true,
"links":true,
"hiddens":false,
"backups":true,
"theme":"default",
"logs":true,
"https":false,
"authentication":true,
"user":"obmin",
"password": "123456",
"sources":[
    {"path":"/mnt/archive","recursive":true},
    {"path":"/home/user","recursive":true}
]
}
```

But JSON configuration could contain just one option then other options will be taken from stored system settings or default values. So configuration file could have only port or sources array and could look like this:
```json
{
"port":8087
}
```
