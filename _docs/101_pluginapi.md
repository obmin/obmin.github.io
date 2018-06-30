---
title: Extensions API
permalink: /docs/:path/
layout: documentation
---

<p class="description">Extensions API is still `beta` and could have a lot of changes after release.</p>

The server extensions API is pretty simple. Extensions can receive request and have return a response. It could be some value like boolean or string with some HTML tag inside or they have to process some long responses like streams.

First, you must have a metadata object. You need a name, type and uuid in your METADATA at least. UUID have to be an unique identifier. You could use [uuid_generator](https://github.com/konkor/obmin/tree/master/tools) from the tools project folder to make it.
```js
// SAMPLE: File lists extension's METADATA
var METADATA = {
    name: "File lists",
    uuid: "f7d92e608a582d0fe0313bb959e3d51f",
    summary: "Various file lists generator",
    tooltip: "Shows various menu buttons for URLS, PLS, M3U...",
    schema: "obmin.plugins.konkor.filelists",
    author: "konkor",
    url: "https://github.com/konkor/obmin/",
    type: Base.PlugType.MENU_ITEM
};
```
All Plugin types defined in the `plugins/base.js` module.

```js
var PlugType = {
UNDEFINED:   0,
SCRIPT:      1,
STYLE:       1 << 1,
LINK:        1 << 2,
MENU_ITEM:   1 << 3,
TOOLBAR:     1 << 4,
NOTIFY:      1 << 5,
TOP_PANEL:   1 << 6,
BOTTOM_PANEL:1 << 7,
LEFT_PANEL:  1 << 8,
RIGHT_PANEL: 1 << 9,
FOOTER:      1 << 10
};

// You can define several types in an binary expression
var METADATA = {
    name: "Sample",
    uuid: "11111111111111111111111111111111",
    type: Base.PlugType.MENU_ITEM | Base.PlugType.NOTIFY
};
```

Second, you have to inherit the base plug-in class in a new one. You can see what is supported by the extension API from the BasePlugin Class now. The class structure has next parts:
1. **Constructor** has two arguments: server and METADATA references. There is one more property `puid` - Plugin Unique ID for runtime. `uuid` is using for internal identification of an extension, you are enabling/disabling the extension through this uuid. `puid` is using in URI's queries to identify the extension. So `puid` is equal to `uuid` by default. But you can change it in your constructor to generate dynamic ID to an example to have different links to the extension each time you start the server for some security reasons.
2. **has** function used by server to identify extension types.
3. **link** function used to modify the standard link in the WEB UI list.
4. **menu_item** function return additional menu item's button.
5. **notify** function return notify panel div for UI.
6. **response** function is a main response handler.
7. **root_handler** is like **response** but for the root directory. It can have a several file/folder sources and you could handle it in different way.

```js
// ./plugins/base.js module
// BasePlugin Class have to inherit it in all extensions

var Plugin = new Lang.Class ({
    Name: 'BasePlugin',
    Extends: GObject.Object,

    _init: function (server, meta) {
        this.parent();
        this.obmin = null;
        if (server) {
            this.obmin = server;
            DEBUG_LVL = this.obmin.debug_lvl ();
        }
        this.name = '';
        this.uuid = '';
        this.summary = '';
        this.tooltip = '';
        this.schema = '';
        this.author = '';
        this.url = '';
        this.type = PlugType.UNDEFINED;
        if (meta.type) this.type = meta.type;
        if (meta.name) this.name = meta.name;
        if (meta.uuid) this.uuid = meta.uuid;
        if (meta.summary) this.summary = meta.summary;
        if (meta.tooltip) this.tooltip = meta.tooltip;
        if (meta.schema) this.schema = meta.schema;
        if (meta.author) this.author = meta.author;
        if (meta.url) this.url = meta.url;
        //puid runtime Plugin Unique ID it can be equal to:
        //uuid   - to has constant path (for bookmarks, public radio etc), default
        //custom - assigned by user for some reason (to access to hidden staff)
        //random - Gio.dbus_generate_guid ();
        //         new on each server start (user have to access to the server 1st to get link)
        this.puid = this.uuid;
    },

    has: function (attribute) {
        return (this.type & attribute) == attribute;
    },

    link: function (file, div) {
        return div;
    },

    menu_item: function (class_name) {
        return "";
    },

    notify: function (files) {
        return "";
    },

    response: function (request) {
        return null;
    },

    root_handler: function (request) {
        if (!this.obmin) return false;
        this.obmin.redirect (request.msg, "/");
        return true;
    },

    destroy: function () {
        GObject.signal_handlers_destroy(this);
    }
});

```

Finally, the `base.js` module has definitions for processing debug(), info() and error() messages in your extension. You can use them inside an extension like:
```js
// Import plugins/base.js module
const Base = imports.plugins.base;

// Call methods directly
Base.debug ("MY SUPER EXTENSION", "Hello World!!!");

// or you can redefine them like
const LOG_DOMAIN = "MY SUPER EXTENSION";
function debug (domain, text) {
    if (!text) Base.debug (LOG_DOMAIN, domain);
    else Base.debug (domain, text);
}
// and use it inside your extension
debug ("Hello World!!!");
error ("SOME FUNCTION", "Hello World!!!");
```

What is next? Take a look at [the extension sample](/docs/101_plugsample) and exist extensions.
