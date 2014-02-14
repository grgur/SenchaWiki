---
layout: post
date:   2014-02-14 19:05:21
title: Adding Cordova plugins
---

Adding Cordova plugins
======

1. Open terminal
2. Navigate to `./cordova/`
3. Execute `cordova plugin add [ID_OF_PLUGIN | GITHUB_REPO]`
4. Platform specific config.xml is managed by `./config.xml`. All configuration has to be there, otherwise sencha build will overwrite it. You have to manually add plugin-related config there.

You can use plugin IDs for Cordova's, and GitHub repos for third party plugins.

Common issues
======

* If iOS build fails, it's often due to plugin files not being installed for that platform. Navigate to `cordova/plugins/<PLUGIN_ID>/src/ios/`. Copy all files to `cordova/platforms/ios/MI/Plugins/<PLUGIN_ID>/`. It's very likely that you will have to create the `<PLUGIN_ID>`folder. 
* If you can't load the plugin through JS, make sure `cordova_plugins.js` is loaded
* Always make sure that `<feature>` config of your plugin is present in `./html5/config.xml`