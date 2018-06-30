---
title: Extension Sample
permalink: /docs/:path/
layout: documentation
---

Here is the sample of 'Screenfetch' extension. It just puts the output of console of the `screenfetch` command as a response on the 'FETCH' menu button as plain text. The sample is simple but you could just imagine what you can output to the Internet page. So place the code listening to the new folder to example `plugins/screenfetch/plugin.js`, enable it in [the extension manager](/docs/03_components/#plugins-management) and restart the server.

```js
// Standard modules used in the sample
const Lang = imports.lang;
const GLib = imports.gi.GLib;
const Gio = imports.gi.Gio;

// We have to find the base dir to able load other OBMIN modules
const APPDIR = get_appdir ();
imports.searchPath.unshift (APPDIR);

// Base Plugin's module
const Base = imports.plugins.base;

// Description of our extension
var METADATA = {
    name: "Screenfetch :)",
    uuid: "dc7275b71eb015d3a3e8e49059f8d85b",
    summary: "Brief system information",
    tooltip: "Shows the brief system info\n(screenfetch required)",
    author: "konkor",
    url: "https://github.com/konkor/obmin/",
    version: 1,
    api: 1,
    type: Base.PlugType.MENU_ITEM
};

// The main class of an extension have to be `Plugin` and extend Base.Plugin class
var Plugin = new Lang.Class ({
    Name: 'FetchPlugin',
    Extends: Base.Plugin,

    // the constructor needs only one argument for the server reference
    _init: function (obmin) {
		// calling of base class constructor
		// we leave it with default values
        this.parent (obmin, METADATA);
		// defining `fetch` property for `screenfetch` command
		// if it's not found it will be NULL
        this.fetch = GLib.find_program_in_path ("screenfetch");
    },

	// Creating the extension menu button
    menu_item: function (class_name) {
        let s = "";
		//If `screenfetch` command is not installed we return an empty string
        if (!this.fetch) return s;
		// Generating the menu button as a HTML link
		// We are using `puid` to identify our extension
		// In this example we are using puid = uuid
		// we are using the referenced default class_name here
		// and `toggle()` script on click to hide menu after the event
        s += "<a href=\"?plug=" + this.puid + "\" class=\"" +
             class_name + "\" onclick=\"toggle()\" title=\"Shows the brief system information\">FETCH</a>";
        return s;
    },

	// Here is a magic :)
    response: function (request) {
        if (!this.fetch) return false;
		// Calling the OBMIN send_pipe_async function to send response from command line
        return this.obmin.send_pipe_async (request, [this.fetch,"-N"], "screenfetch", "text/plain");
    }
});

function getCurrentFile () {
    let stack = (new Error()).stack;
    let stackLine = stack.split('\n')[1];
    if (!stackLine)
        throw new Error ('Could not find current file');
    let match = new RegExp ('@(.+):\\d+').exec(stackLine);
    if (!match)
        throw new Error ('Could not find current file');
    let path = match[1];
    let file = Gio.File.new_for_path (path).get_parent().get_parent();
    return [file.get_path(), file.get_parent().get_path(), file.get_basename()];
}

function get_appdir () {
    let s = getCurrentFile ()[1];
    if (GLib.file_test (s + "/obmin-server", GLib.FileTest.EXISTS)) return s;
    s = GLib.get_home_dir () + "/.local/share/gnome-shell/extensions/obmin@konkor";
    if (GLib.file_test (s + "/obmin-server", GLib.FileTest.EXISTS)) return s;
    s = "/usr/share/gnome-shell/extensions/obmin@konkor";
    if (GLib.file_test (s + "/obmin-server", GLib.FileTest.EXISTS)) return s;
    throw "Obmin installation not found...";
    return s;
}
};
```

<p><img src="{{ "/assets/images/docs/plugsample_ui.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>Screenfetch Extension</b> Menu Button in the additional menu.</p>

<p><img src="{{ "/assets/images/docs/plugsample_output.png" | relative_url }}" style="max-width:100%;max-height:60vh;width:auto;height:auto;margin:auto;"/><br><b>Screenfetch Extension</b> Response output as a plain text.</p>
