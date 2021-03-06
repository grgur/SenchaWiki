---
layout: post
date:   2014-02-14 19:05:21
title: Debugging Native Builds
---

Debugging Native Builds
=======================

As you start testing your native build (`sencha app build native`) you may notice additional bugs. By default they will be difficult to track due to JavaScript compression performed during the build. 

To combat that, open `.sencha/app/native.properties`. Append the following content:

{% highlight bash %}
build.compression.yui=0
build.compression.closure=0
build.compression.ugilfy=0
app.microloader.name=testing.js
{% endhighlight %}

Make sure you comment it out for production release!