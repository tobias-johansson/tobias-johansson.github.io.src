+++
date = "2015-03-09T10:16:55+02:00"
draft = false
title = "Android WebView Cookies"

+++

Had some cookie problems when loading raw content in an Android WebView:

    Uncaught SecurityError: Failed to read the 'cookie' property from 'Document': Cookies are disabled inside 'data:' URLs.

It seems that
```java
WebView webView = new WebView(activity);
webView.loadData(htmlString, "text/html", null);
```
puts us at a 'data:' url (which makes sense), where cookies are blocked.

We need to enable cookies and also forcibly set the url to something else, like:
```java
CookieManager.getInstance().setAcceptCookie(true);
WebView webView = new WebView(activity);
webView.loadDataWithBaseURL("http://localhost/", htmlString, "text/html", "utf-8", null);
```
