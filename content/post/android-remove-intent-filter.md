+++
date = "2015-08-31T15:53:57+02:00"
draft = true
title = "Removing an intent-filter using the Android Manifest Merger"

+++

Needed to remove an `intent-filter` for an activity that was defined in a library. This can be done by instructing the [Android Manifest Merger](http://tools.android.com/tech-docs/new-build-system/user-guide/manifest-merger) with a `tools:node="remove"` on the `intent-filter` tag.

To identify a specific `intent-filter` tag (there can be many), the merger uses the combination of `android:name` attributes from the child `action` and `category` tags.

Example:
```xml
<activity
  android:name=".SomeActivity">
  <intent-filter tools:node="remove">
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER"/>
  </intent-filter>
</activity>
```
