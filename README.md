Application preferences Cordova plugin.
-----------------------

Store and fetch application preferences using platform facilities.
Compatible with phonegap 3.x

Installing:
---

From plugin registry:

    $ cordova plugin add me.apla.cordova.app-preferences

From the repo:

    $ cordova plugin add https://github.com/apla/me.apla.cordova.app-preferences

From a local clone:

    $ cordova plugin add /path/to/me.apla.cordova.app-preferences/folder


More information:
[Command-line Interface Guide](http://cordova.apache.org/docs/en/edge/guide_cli_index.md.html#The%20Command-line%20Interface).

[Using Plugman to Manage Plugins](http://cordova.apache.org/docs/en/edge/guide_plugin_ref_plugman.md.html).


Synopsis:
---

```javascript

function ok (value) {}
function fail (error) {}


var prefs = plugins.appPreferences;

// store key => value pair
prefs.store (ok, fail, 'key', 'value');

// store key => value pair in dict (see notes)
prefs.store (ok, fail, 'dict', 'key', 'value');

// fetch value by key (value will be delivered through "ok" callback)
prefs.fetch (ok, fail, 'key');

// fetch value by key from dict (see notes)
prefs.fetch (ok, fail, 'dict', 'key');
```

Platforms:
---
1. Native execution on iOS using `NSUserDefaults`
1. Native execution on Android using `android.content.SharedPreferences`
1. Native execution on Windows Phone using `IsolatedStorageSettings.ApplicationSettings`
1. (WIP) fallback using `localStorage`

Notes:
---
1. iOS, Android and Windows Phone basic values (`string`, `number`, `boolean`) stored using typed fields.
1. Complex values, such as arrays and objects, always stored using JSON notation.
1. Dictionaries supported only on iOS, so on another platforms when using dict key
will be written like `<dict>.<key>`

Tests:
---
Tests available in `src/test.js`. After installing plugin, you can add test code from this file and then launch `testPlugin()` function.

iOS, Android and Windows Phone 8 test pass ok at this moment.

Credits:
---

Originally ported from:
https://github.com/phonegap/phonegap-plugins/tree/master/iOS/ApplicationPreferences

Another android implementation for cordova 2.x:
https://github.com/macdonst/AppPreferences
