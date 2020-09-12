WK Cache Clear
=============

WKCacheClear selectively clears the WkWebView cache for Cordova 9 running on iOS 9 or above. 

Derived from Anrip Wong's CacheClear plugin https://github.com/anrip/cordova-plugin-cache-clear. This plugin was rewritten to specifically support WkWebView on iOS, whose cache clearing mechanics differ from UIWebView. Android support was not considered, since WkWebView is specific to iOS.


Installation
======
Using the standard Cordova CLI:

<pre>
cordova plugin add https://github.com/mgatto/cordova-plugin-wkwebview-clearcache.git
</pre>

Usage
====
```javascript
document.addEventListener('deviceready', function() {
    window.WkCacheClear({domain: 'example.com', delete: ['cookies','assets']}, (msg) => '', (error) => '');
});
```

Options
-------

* `domain`: Required. A domain name string: "example.com" or "sub.domain.com". Omit slashes and protocols, like "http:". Required, since the user may not like cookies for other sites being deleted in Safari
* `delete`: Optional. an array of plain-text aliases for `WkWebSiteDataType` constants:

    **Supported:**
    * *(included automatically)* WKWebsiteDataTypeMemoryCache
    * *(included automatically)* WKWebsiteDataTypeOfflineWebApplicationCache
    * `cookies` => WKWebsiteDataTypeCookies 
    * `assets` => WKWebsiteDataTypeDiskCache *(HTML, JS and image files cached from the Cordova bundle)*
        
    **Unsupported:**
    - WKWebsiteDataTypeLocalStorage
    - WKWebsiteDataTypeSessionStorage
    - WKWebsiteDataTypeIndexedDBDatabases
    - WKWebsiteDataTypeWebSQLDatabases
