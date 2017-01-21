---
layout: post
title: Pangu8 (for Mac)
description: Taking a look under the hood of Pangu8 to see what it does.
image: pangu8.png
tags: developer, ios, jailbreak, pangu
---

**Update:** Pangu fixed this issue a long time ago and nobody seemed to notice it was resolved.

It you don’t already know, Pangu8 is an iOS jailbreaking tool used to install tweaks, apps, and themes that you get through the **Cydia Store**. Due to Apple’s strict limits on the App Store, they just don’t allow these kind of cool modifications to your device.

For whatever reason, Pangu8 mysteriously broke in 2014/2015. Meaning, whenever you wanted to run the tool and jailbreak, you couldn’t.

<null></null>

Pangu *resolved this* by pointing to new URLs to fetch Xcode and DeveloperDiskImage.

Here are a couple of URLs that Pangu uses in their iOS 8.0 -- 8.1 jailbreak utility for Mac. Note: these strings are *not* in the Windows version. Perhaps they are obfuscated…?

- [http://pangu.io/8_update.plist](http://pangu.io/8_update.plist) (checks for updates to Pangu8)

- [http://tj.8.pangu.io/mac/8/](http://tj.8.pangu.io/mac/8/) (used to check for a working Internet connection)

- [https://albert.apple.com/...](https://albert.apple.com/WebObjects/ALUnbrick.woa/wa/deviceActivation) (checks if a device is activated or not. activation is required for Pangu8 to continue)

- [http://xcode.pangu.io/...](http://xcode.pangu.io/download_key.plist) (downloads Xcode and mounts DeveloperDiskImage)

And if you're curious, here's a plist of the latter URL:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>cookie</key>
	<string>downloadKey=</string>
	<key>type</key>
	<integer>1</integer>
	<key>url</key>
	<string>http://dl.pangu.25pp.com/jb/inject.bundle.xxx</string>
</dict>
</plist>
```
