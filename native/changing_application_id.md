Changing Application ID
======

If you didn't supply with an app ID during `sencha generate app` process, or just decided to give it a better name, you will need to access a few files and change a few strings. 

* `./cordova/.cordova/config.json` - Replace ID
* `./config.xml` - replace ID in the _<widget>_ tag

If you specified URL schemes in your iOS app, you will need to update the ID there as well:

* `./cordova/platforms/ios/MI/MI-Info.plist` - needed for the URL scheme to work