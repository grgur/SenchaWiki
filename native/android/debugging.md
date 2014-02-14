Debugging on Android version <= 4.3
======
**Prerequisites**

* Node.js
* NPM

**Setup**

1. Install weinre `sudo npm -g install weinre`
2. Run weinre `weinre --boundHost -all-`. On Windows you may have to run it this way: `node.exe node_modules\weinre\weinre --boundHost -all-`
3. Enable weinre in the app: Open `app.json` and uncomment the remote dependency that looks similar to this: `http://192.168.1.218:8080/target/target-script-min.js`. Replace IP with that of your machine's. 
4. Then run `sencha app build native` to refresh dependencies and metadata 

**Debugging**

1. Deploy to device or run in a browser to test
2. Run debugging client on *Safari only*. Point Safari to `http://<YOUR_LOCAL_IP/client/`
3. Click on the client you wish to inspect
4. Go to console or another tab to start debugging

Note: The debugging client has to run on Safari. Weinre no longer works with Chrome due to flex box issues