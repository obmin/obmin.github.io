---
title: Installation
permalink: /docs/:path/
layout: documentation
---

1. [Dependencies](#dependencies)
1. [Gnome extensions](#gnome-extension-version)
1. [Debian package](#debian-package)
1. [Installation from sources](#source-archive)
1. [Restarting Gnome Shell](#restarting-gnome-shell)
1. [Managing Extensions](#managing-extensions)
1. [Upgrading the extension](#upgrading-the-extension)
1. [Uninstalling](#uninstalling)
1. [Troubleshooting](#troubleshooting)

## Dependencies

If you have Gnome Desktop, you already have all requirements installed probably. But if not or something is wrong, you should recheck the dependencies.

* gjs (core dependency)
* GTK3 libraries:
 * gir1.2-atk-1.0
 * gir1.2-glib-2.0
 * gir1.2-gtk-3.0
 * gir1.2-soup-2.4
* psmisc (mics tools for applets)
* gir1.2-appindicator3 (the obmin-indicator for non-Gnome shell extension)
* Gnome Shell 3.14+ (the gnome version only)
* Font Roboto (recommended for the client side browsers)

Debian/Ubuntu flavors can do next:

```sh
sudo apt-get update
sudo apt-get install gjs gir1.2-atk-1.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-soup-2.4 psmisc curl gir1.2-appindicator3
```

## Gnome extension version

The easiest way to install OBMIN Server is installing the gnome extension package. There are a few ways to make it.

* [Official Gnome Site](https://extensions.gnome.org/extension/1254/obmin/) for all supported by Gnome extensions.
* You can use your Software Application Center on many modern distributions. They already have the integration with Gnome extensions repo. So you can just type Obmin in the search box of your application center.
* You can install it manually from [the latest stable zip package ](https://github.com/konkor/obmin/raw/master/releases/obmin@konkor.zip) on GitHub's [releases page](https://github.com/konkor/obmin/blob/master/releases/) and install it through `gnome-tweak-tool` or in terminal:

```sh
# Remove the old extension if exist
rm -rf ~/.local/share/gnome-shell/extensions/obmin@konkor

# Unpack obmin@konkor.zip package to the Gnome extensions folder
unzip obmin@konkor.zip -d ~/.local/share/gnome-shell/extensions/obmin@konkor
```
* Download [the installing script](https://github.com/konkor/obmin/raw/master/install_obmin.sh) and:

```sh
# Make it executable
chmod +x install_obmin.sh

# Run it
./install_obmin.sh
```
* The deb package installing contains Gnome extension so.
* You can just clone git repo and move it to _~/.local/share/gnome-shell/extensions/obmin@konkor_
* At least you can download desired branch as an archive on GitHub and install it even in Nautilus.

**After some installation methods, you have to [restart Gnome Shell](#restarting-gnome-shell) and enable it via [managing tools](#managing-extensions)**

## Debian package

## Installation from sources

## Restarting Gnome Shell
<p class="description">Different ways to restart or re-log current Gnome Shell session</p>
 * user's **Log-out / Log-in** (_X11/Wayland_)
 * <kbd>Alt</kbd>+<kbd>F2</kbd> and enter <kbd>r</kbd> command (_X11 only_)
 * or just **reboot** PC (_X11/Wayland_)

## Managing Extensions
<p class="description">Here are some ways to manipulate the extension state (enabling, disabling, installing, updating, removing settings...).</p>

You can manage your extensions in many ways:
* `gnome-shell-extension-prefs`
* `web browser page` [Installed Extensions](https://extensions.gnome.org/local/)
* `gnome-tweak-tool`
* `Gnome Software Center`.
* `Manual method` by removing any extension folder you will remove the extension. After this operation you have to [restart current Gnome session](#restarting-gnome-shell).

## Upgrading the extension
<p class="description">Here are some ways to upgrade the extension</p>

Hopefully frequently, the extension will receives updates to fix bugs, update the documentation or add new features and abilities.
So here is a few ways to do this:
1. You can update the extension through the `web browser page` [Installed Extensions](https://extensions.gnome.org/local/)
2. You can do this in the `Gnome Software Center`.
3. You can get the development version from GitHub.
 * Download desired archive from GitHub
```
wget https://github.com/konkor/obmin/archive/master.zip
```
 * Extract _obmin-master.zip_.
 * Replace all files in the _~/.local/share/gnome-shell/extensions/obmin@konkor_ folder.
 * [Restart GNOME Shell](#restarting-gnome-shell).
4. You can use [installation script](#installation-script) for the Gnome extension version. Using the command will switch you to the latest desired GitHub branch:
```sh
./install_obmin.sh [GITHUB_BRANCH]
```
5. Download [deb package](https://github.com/konkor/obmin/raw/master/releases/obmin_latest_all.deb)

**You can also use manual method, `gnome-tweak-tool`, software center etc.**

## Uninstalling
<p class="description">Sometimes we need to remove some extension. The cause could be for example complete reinstallation or bugs. It can be useful if you have saved broken settings values or to clean up previous installations.</p>

Completly removing the extension and stored settings.
1. Remove the extension folder
```sh
rm -Rf ~/.local/share/gnome-shell/extensions/obmin@konkor
```
**Be careful with this command as any mistake could cause a data loss!!!**

2. You can check this values in the **dconf-editor** at `/org/gnome/shell/extensions/obmin/`.
If you want reset the extension's values to defaults just run it and restart gnome-shell.
```sh
dconf reset -f "/org/gnome/shell/extensions/obmin/"
```

## Troubleshooting

### Check system journal

```sh
# for current log
sudo journalctl

# for monitoring
sudo journalctl -f
```

### [GitHub Issues Page](https://github.com/konkor/obmin/issues)

Check known issues on GitHub and if can't find the solution just report there.

### Check your installation
1. Enable Obmin Server from user interface or run it in terminal.
2. Open your browser and enter the local IP address and obmin server port (default 8088). So you can look your local address in the gnome or obmin-indicator applets it's looking like http://192.168.1.10:8088 to an example or just enter localhost:8088. You should see obmin home page with selected file locations or link to your Home Folder if it's not configured yet.
3. Now you can check it from other devices (mobile phones, other machines) connected to the same the network. Do the same at 2 for your local IP address (ex. http://192.168.1.10:8088). `If not you have to check your Firewalls on the server and/or guest sides.`
