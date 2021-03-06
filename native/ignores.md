---
layout: post
date:   2014-02-14 19:05:21
title: What to .gitignore
---

Setting Git Ignore Rules in Sencha Touch + Cordova Apps
=======

Once you create your first native built, the number of files in your project will increase tremendeously. You don't want most of that to clutter your Git repo as they will re-generate on each `sencha app build native`.

Global (project) `.gitignore`
--------------------------------
First of all you may want to ommit the general suspects.

{% highlight bash %}
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
.idea
.project
{% endhighlight %}

You can also safely ignore sass cache.

{% highlight bash %}
.sass-cache
{% endhighlight %}

Should you ever upgrade Sencha Touch through Cmd (recommended), you will get another folder that you can ignore.

{% highlight bash %}
.sencha_backup
{% endhighlight %}

Then the _build_ and _archive_ folders. They hold the temporary build files that are then copied to respective cordova dirs. 

{% highlight bash %}
./build
./archive
{% endhighlight %}

Warning: don't just put _build_ as there are several build folders and executables that will get ignored and you don't want that!

Now we are getting to cordova. Most of these will get updated with each build:

{% highlight bash %}
cordova/platforms/android/bin
cordova/platforms/android/CordovaLib/bin
cordova/platforms/android/assets/www
cordova/platforms/ios/build
cordova/platforms/ios/www
cordova/www
{% endhighlight %}

Note: All users that need to build should make sure that they have `cordova/platforms/android/assets/www` dir created, even though it's ignored. The conent will be replaced with each build, though. 

Optionally, if you don't plan on modifying the _xcodeproj_ heavily, you can ignore these:

{% highlight bash %}
cordova/platforms/ios/CordovaLib/CordovaLib.xcodeproj/xcuserdata
cordova/platforms/ios/MI.xcodeproj/project.xcworkspace
cordova/platforms/ios/MI.xcodeproj/xcuserdata
{% endhighlight %}

---


####All together now
Finally, your project's .gitignore file could look like this:

{% highlight bash %}
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
.idea
.project
.sass-cache
.sencha_backup
./build
./archive
cordova/platforms/android/bin
cordova/platforms/android/CordovaLib/bin
cordova/platforms/android/assets/www
cordova/platforms/ios/build
cordova/platforms/ios/www
cordova/www
cordova/platforms/ios/CordovaLib/CordovaLib.xcodeproj/xcuserdata
cordova/platforms/ios/MI.xcodeproj/project.xcworkspace
cordova/platforms/ios/MI.xcodeproj/xcuserdata
{% endhighlight %}

If you already commited any of the files and folders we just added to .gitignore, you will have to remove them from repo to apply the change:

{% highlight bash %}
git rm -r --cached FILE_OR_FOLDER_PATH
{% endhighlight %}

Cordova's `.gitignore` fix
-----------------------

There's a glitch in some versions of Cordova where they ignored _build_ ending up in omitting important content.

Navigate to `cordova/platforms/ios/` and open `.gitignore`. Comment out `build` and add `CordovaLib/build`

{% highlight bash %}
#build
CordovaLib/build
{% endhighlight %}

Had you left it there, `cordova/platforms/ios/cordova/build` executable would have been ignored, causing troubles to your teammembers. 

Conclusion
----------
Try these rules before you apply them to a production environment. Please share your tips and tricks!