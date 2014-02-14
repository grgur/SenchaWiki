---
layout: post
date:   2014-02-14 19:05:21
title: Build and Deploy to Android Device
---

Build and Deploy to Android Device
====

When you debug on Android phones, copying over to native device and manually installing your app can be very time consuming. On the other hand the simulator is often not the way to debug and is kinda slow. 

Here is what I often do to build a ST2 app and deploy automatically:

```
sencha app build native && adb -d install -r cordova/platforms/android/bin/MYAPP-debug.apk 
```

The secret sauce comes after the `&&` part. Adb (belongs to Android Tools) will install (and replace if needed) the apk file after Sencha Cmd and Cordova build it. Of course, you will need to have your device plugged in with debugging mode on.