---
title: Components
permalink: /docs/:path/
layout: documentation
---

1. [File Structure](#file-structure)
1. [Obmin Server](#obmin-server)
1. [OBMIN Center](#obmin-center)
1. [Other Configuration Tools](#configuration-tools)
1. [Monitoring Tools](#monitoring-tools)
1. [Gnome Extension](#gnome-extension)
1. [Plugins Management](#plugins-management)

## File Structure

The project has been built on Gnome JavaScript (GJS). GJS is pretty awesome language. It's not an Electron JavaScript application on WebKit render and it's not using Node.JS with huge frameworks. Gnome JavaScript is just utilizing GObject Introspection widely used in all Gnome Stack from GLib, Gtk to GStreamer etc. Actually, Gnome JavaScript has only two components: `gjs` - the interpreter with bindings to system GIRs, and `libmozjs` - pure Mozilla ECMAScript engine. So GJS applications create same pure Gtk, GLib objects and render them like any other system applications written on Python, Ruby, Vala etc.

First versions were only for Gnome Shell like a Gnome Extension. After Gnome Extension release, many Ubuntu users and many others asked for supporting other desktop environments. Actually, users were able to lunch the server from a command line but there were any options to configure or monitor the server. It's how was born the idea to use just binaries hooks to the existing extension modules and make a few new tools for the server.

```sh
# Binary Applications
obmin-server        # OBMIN Server
obmin-center        # Obmin Center
obmin-extensions    # Extensions Manager
obmin-indicator     # System Tray Indicator
obmin-preferences   # Obmin Preferences
```
```sh
# Modules
[common]            # Main Modules Folder
[plugins]           # Server Plugins
convenience.js      # Basic utilities
prefs.js            # Preferences Module
```
```sh
# Gnome Extension
extension.js        # Main Extension
metadata.json       # Extension metadata
stylesheet.css      # Extension CSS
```
```sh
# Other Assets
[data]              # Icons, styles, shortcuts etc
[locale]            # Translations
[schemas]           # GSettings schema
```
```sh
# Documentation
[man]               # MAN pages
config_sample.json  # Configuration Sample
INSTALL.md          # Installation
README.md           # README
```

## Obmin Server

```sh
obmin-server
```
It runs an instance of OBMIN Server. See [Configuration](/docs/02_configuration/) and [WEB Interface](/docs/04_webui/) for more information.

## OBMIN Center
```sh
obmin-center
```
This is the main UI component of OBMIN. Here is you can do almost all tasks:
* control panel for running the server;
* monitor page to see a statistic and actual connections;
* logs page to see the server logs;
* settings page to configure the application (see [Configuration](/docs/02_configuration/)).

<p><img src="{{ "/assets/images/docs/obmin_center.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-center</b> Monitor/Stats Page.</p>
<p><img src="{{ "/assets/images/docs/obmin_center_logs.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-center</b> Logs Page.</p>
<p class="description">You don't need to run it all the time. You can configure, run/stop the server, look at logs and quit to free system resources. The server will be running in the background. There are other lightweight monitoring tools like OBMIN Gnome extension and Obmin Indicator. They could be running during all user session and do not consuming more system resources.</p>

## Configuration Tools
```sh
obmin-center
obmin-preferences
```
You can configure the OBMIN through several tools:
1. OBMIN Center has the Settings Page with embedded Preferences Window widget;
2. OBMIN Preferences is a standalone lightweight application for the configuration;
3. Gnome Shell users can use other standard utilities to call OBMIN Preferences widget:
 * `gnome-shell-extension-prefs` utility
 * `web browser page` [Installed Extensions](https://extensions.gnome.org/local/)
 * `gnome-tweak-tool`

See more about the configuration on [Configuration](/docs/02_configuration/) page.

<p><img src="{{ "/assets/images/docs/obmin_center_prefs.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>obmin-center</b> Settings Page.</p>
<p><img src="{{ "/assets/images/docs/extensions_page_prefs.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>Installed Extensions Page</b> OBMIN Configuration.</p>

## Monitoring Tools
Monitoring Tools can be active and passive. System logs are a passive monitoring option. You can find logs in the system journal `sudo journalctl` or in the local logs. You could find them on the Logs Page of OBMIN Center or in the user's `~/.local/obmin/` folder. You should enable the `local logs` option in the preferences window to store it. Obmin Center (Statistic page), Obmin Indicator and Gnome OBMIN Extension are active tools for the monitoring. They have the main task to notify users about current activity and show a statistic usage like amount of active connections, total requests, transfered data. Also, they show information about local and external IP addresses.
<p><img src="{{ "/assets/images/docs/obmin_indicator_eos.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>OBMIN Indicator</b> on Pantheon Desktop of Elementary OS.</p>

## Gnome Extension
OBMIN Gnome Extension is a monitor. It has the same functionality like OBMIN Indicator and a deep integration with Gnome Desktop environment.
<p><img src="{{ "/assets/images/docs/gnome_extension.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>OBMIN Gnome Extension</b> Activity statistic on Gnome Shell.</p>

## Plugins Management
```sh
obmin-extensions
```
<p class="description">You can call the extension manager from the General Settings Page</p>
OBMIN Server Extension's System is a powerful feature of the solution. It's easy to enhance, customize the server with server extensions and streamed pipelines. You could bring all power of Linux command line to your personal WEB server and utilize all your installed system packages. Later we will overview the OBMIN Extension Structure and look at a simple extension.
<p><img src="{{ "/assets/images/docs/obmin_extensions.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>OBMIN Extensions Manager</b> A list of installed extensions.</p>
