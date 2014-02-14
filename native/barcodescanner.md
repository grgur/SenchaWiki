---
layout: post
date:   2014-02-14 19:05:21
title: BarcodeScanner plugin
---

BarcodeScanner
=======

**BarcodeScanner plugin repo:** https://github.com/wildabeast/BarcodeScanner

**Installation: **
```cordova plugin add https://github.com/wildabeast/BarcodeScanner```

Then add this section after the closing `<author>` tag in `./config.xml`

```
<feature name="BarcodeScanner">
    <param name="ios-package" value="CDVBarcodeScanner" />
    <param name="android-package" value="com.phonegap.plugins.barcodescanner.BarcodeScanner" />
</feature>
```

This will enable the Scanner plugin for iOS and Android deployments. 

Here's a class you can use invoke the scanner:

{% highlight javascript %}
/**
 * Created by grgur on 28/01/14.
 */

/**
 * Singleton for working with the Cordova Barcode scanner plugin
 */
Ext.define('MyApp.Barcode', {
    singleton : true,

    /**
     * Check for dependencies and return the scanner plugin.
     * return false otherwise
     * @returns {window.plugins.barcodeScanner|*}
     */
    getScanner : function () {
        var isCordova = window.hasOwnProperty('cordova'),
        	cordova = window.cordova,
            scanner = isCordova ? cordova.require("com.phonegap.plugins.barcodescanner.BarcodeScanner") : null;

        if (Ext.isObject(scanner)) {
            return scanner;
        }

        // try alternative method if cordova.require can't find the plugin
        scanner = isCordova ? cordova.plugins.barcodeScanner : null;
        return scanner;
    },

    /**
     * Start scanning
     * @param cfg
     * @param success {Function} Success callback
     *      @argument result {Object} The only argument in success callback containing:
     *          @param text {String} Recognized barcode
     *          @param format {String} Barcode format
     *          @param cancelled {Boolean} True when user cancels
     * @param failure
     *      @argument error {String} Description of the error
     * @param scope {Object} Scope for success and failure callbacks
     *
     * Example:
     *
     *          MyApp.Barcode.scan({
     *              success: function (result) {
     *                  alert("We got a barcode\n" +
     *                      "Result: " + result.text + "\n" +
     *                      "Format: " + result.format + "\n" +
     *                      "Cancelled: " + result.cancelled);
     *              },
     *              failure: function (error) {
     *                  alert("Scanning failed: " + error);
     *              }
     *          });
     */
    scan : function (cfg) {
        var success = cfg.success || Ext.emptyFn,
            failure = cfg.failure || Ext.emptyFn,
            scope = cfg.scope || Ext.global,
            scanner = this.getScanner();

        if (!scanner) {
            return failure('Barcode scanner plugin is not present');
        }

        return scanner.scan(success.bind(scope), failure.bind(scope));
    }
});
{% endhighlight %}