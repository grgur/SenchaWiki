---
layout: post
date:   2014-02-14 19:05:21
title: Building for Release to Google Play Store
---

Building for Release to Google Play Store
=====

1. Open `.sencha/app/cordova-impl.xml`
2. Find  `target name="-cordova-build"`  (should be around line 117)
3. Append `--release` to the cordova build command. The new value will be:  `cordova build ${cordova.platforms.clean} --release`
4. Create `ant.properties` file in `cordova/platforms/android/`
5. Append this content with your values: 
```
key.store=../../path/to/AndroidRelease.keystore
key.store.password=mypassword
key.alias=myKeyAlias
key.alias.password=mypassword
```
6. Open `cordova/platforms/android/AndroidManifest.xml` and set debuggable to false on this line
{% highlight xml %}
<application 
	android:debuggable="true" 
	android:hardwareAccelerated="true" 
	android:icon="@drawable/icon" 
	android:label="@string/app_name">
{% endhighlight %}
... becomes
{% highlight xml %}
<application 
	android:debuggable="false" 
	android:hardwareAccelerated="true" 
	android:icon="@drawable/icon" 
	android:label="@string/app_name">
{% endhighlight %}

The next time you build you will get new apk files that are also signed automatically. 

If you want to sign manually then make sure ant.properties file is not present. Refer to  [this article](http://developer.android.com/tools/publishing/app-signing.html ) to sign manually.