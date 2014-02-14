Fix for Hardcoded ADB Path
====

If you ever built a Sencha Touch 2.3 Android hybrid app and shared it with your team (e.g. thru GitHub), you may have noticed a warning when another user tried to build it from their machine.

The `cordova/platforms/android/local.properties` file clearly states that it should not be manually modified. It should not even be check into a SCM system (like Git). However, if you simply remove that file you will only get more errors in return.

The solution is to specify an environment variable that Cordova understands. In your `~/.profile` or `~/.bash_profile` append this line:

```
export ANDROID_HOME=/path/to/android/sdk/
```

Of course, you will need to reflect your real path to make it work. 

Execute the profile file (e.g. `. ~/.profile`) to apply the change immediately. Make sure you comment out any paths in any of the `local.properties` files and rebuild. It should work automatigcally.