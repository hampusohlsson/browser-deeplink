browser-deeplink
================

**‼️  Not maintained** - *Use at own risk*   

Redirect your website users to your native Android and/or iOS app. If the user does not have the app, they are redirected to the corresponding app store page. 

Such functionality is very common for apps like YouTube, Spotify etc. But it is not default functionality in mobile browsers today, and unnecessarily hard to implement. This plugin uses a workaround with a hidden `iframe` and `setTimeout()`.

How to use
-

### 1. Include browser-deeplink on your site.

```html
<script src="browser-deeplink.js" type="text/javascript"></script>
```

or

```js
require("./browser-deeplink");
```

### 2. Provide your app details
```js
deeplink.setup({
    iOS: {
        appName: "myapp",
        appId: "123456789",
    },
    android: {
        appId: "com.myapp.android"
    }
});
```

This will create the following fallback app store links:

**iOS:** `itms-apps://itunes.apple.com/app/myapp/id123456789?mt=8`    
**Android:** `https://play.google.com/store/apps/details?id=com.myapp.android`

#### Options

Optionally, you can specify a `iOS.storeUrl` or `android.storeUrl` to override the fallback redirect.
```js
deeplink.setup({
    iOS: {
        storeUrl: "http://...",
    }
});
```

You can also skip the app store fallback altogether if you want by specifying `fallback: false`
```js
deeplink.setup({
    fallback: false
});
```

In case you want to register your android app on your http(s) links directly you can disable deeplinking for android  by specifying `androidDisabled: true`
```js
deeplink.setup({
    androidDisabled: true
});
```

### 3. Open your deeplinks!
```js
window.onload = function() {
    deeplink.open("myapp://object/xyz");
}
```

# License
This library is released under the MIT licence.
