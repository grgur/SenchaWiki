---
layout: post
date:   2014-02-14 19:05:21
title: Building IPA Files Automatically
---

Building IPA Files Automatically
================================

To automatically build IPA files, make sure you have your certificate and mobile provisioning profile ready. Execute in terminal:

{% highlight bash %}
xcrun -sdk iphoneos PackageApplication \
    -v "cordova/platforms/ios/build/device/APPNAME.app" \
    -o $(pwd)"/cordova/platforms/ios/build/APPNAME.ipa" \
    --sign "iPhone Distribution: Modus Create, Inc." \
    --embed "APPNAME.mobileprovision"
{% endhighlight %}

* `-v` part is the path to the .app folder created by Cordova.
* `-o` is output file. You can change the path per your liking.
* `--sign` refers to the name of certificate. It has to be installed on your system. 
* `--embed` is path to your mobile provisioning profile file.