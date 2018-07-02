---
title: Downloads
permalink: /resources/
description:  Project Downloads, Sources, Pages, Other Useful Links, and Resources.
layout: default
---

# [DEB package](https://github.com/konkor/obmin/releases)
<p class="description">Download the latest stable <b>deb</b> package for the complete system integration on GNU/Linux Debian/Ubuntu flavors.</p>
<a href="https://github.com/konkor/obmin/raw/master/releases/obmin_latest_all.deb"><img src="{{ "/assets/images/debs.png" | relative_url }}" style="max-width:100%;max-height:43vh;width:auto;height:auto" title="Get latest deb package..." /></a>

# [Gnome Extension Package](https://github.com/konkor/obmin/releases)
<p class="description">The latest Gnome extension package for Gnome Desktop environment.</p>
<a href="https://github.com/konkor/obmin/raw/master/releases/obmin%40konkor.zip"><img src="{{ "/assets/images/zips.png" | relative_url }}" style="max-width:100%;max-height:43vh;width:auto;height:auto" title="Get latest gnome extension package..." /></a>

# [Source Code](https://github.com/konkor/obmin)
<p class="description">The GitHub project's page.</p>
<a href="https://github.com/konkor/obmin"><img src="{{ "/assets/images/github_page.png" | relative_url }}" style="max-width:100%;max-height:43vh;width:auto;height:auto" title="Obmin source code on GitHub..." /></a>

# [Gnome Extensions Page](https://extensions.gnome.org/extension/1254/obmin/)
<p class="description">The OBMIN Server project's page on the Gnome extensions site.</p>
<a href="https://extensions.gnome.org/extension/1254/obmin/"><img src="{{ "/assets/images/gnome_page.png" | relative_url }}" style="max-width:100%;max-height:43vh;width:auto;height:auto" title="Gnome Obmin Page" /></a>

# [Docker Repository](https://hub.docker.com/r/obmin/obmin/)
<p class="description">The Docker images of OBMIN Server.</p>
## Usage
```sh
# Pull the docker image
docker pull obmin/obmin

# Run from any folder to share
docker run --rm --volume="$PWD:/srv/obmin" -p 80:8088 -it obmin

# Go to http://localhost to check it
# Done
```
<a href="https://hub.docker.com/r/obmin/obmin/"><img src="{{ "/assets/images/dockerhub.png" | relative_url }}" style="max-width:100%;max-height:43vh;width:auto;height:auto" title="Docker HUB Repository" /></a>
