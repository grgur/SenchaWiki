Debugging on Android KitKat
======
**Setup**

1. Enable debugging in the Java view file (`./cordova/platforms/android/src/foo/bar/MI/MI.java`). The code below belongs to the bottom of the `onCreate` method
```
if(Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
    WebView.setWebContentsDebuggingEnabled(true);
}
```

2. Add the necessary imports in the same file
```
import android.os.Build;
import android.webkit.WebView;
```

3. Make sure you have Android SDK level 19 installed and that android tools are in PATH
4. `sencha app build native`

**Debugging**

1. Connect your phone via USB cable
2. Transfer the binary to the phone. A convenient way is running this command: `adb -d install -r cordova/platforms/android/bin/MYAPP-debug.apk`
3. Open the app on the phone
4. In Chrome (version 30+) open this page: `chrome://inspect/#devices`
5. Locate your app on the screen and press _Inspect_