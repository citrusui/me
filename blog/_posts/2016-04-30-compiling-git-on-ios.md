---
layout: post
title: Compiling Git on iOS
description: Set up a development environment on your device so you can compile Git!
image: git.png
tags: cydia, developer, guide, ios, jailbreak
---

Before we begin, you will need a few prerequisites:

- a jailbroken device on iOS 5 or newer
- about 10-20 minutes of free time

That's it! Now let's get to it.

First, launch Cydia. If you've just jailbroken, wait for Cydia to prepare the filesystem and restart your device.

You're going to need to add a repository. Tap Sources, tap add, select the text in the alert box, and paste the following URL into the alert box:

<!-- break -->

`https://coolstar.org/publicrepo`

Now, wait for your sources to refresh. This should only take a few seconds.

When that process is done, you are going to need to install the following packages: Make, LLVM+Clang, Darwin CC Tools, gettext, Perl, and MobileTerminal. Make sure you install Darwin CC Tools from the BigBoss repository.

If you don't have them already, install iFile and/or Filza. Experienced users can skip this step if they are familiar with the command line.

In order to compile anything, you're going to need an SDK, downloaded from [Xcode](https://developer.apple.com/xcode/). Using iFile or Filza, extract the compressed SDK to your device to some folder on `/var/`, such as `/var/sdks/`. If you have Theos installed, you're going to want to install the SDK to `/var/theos/sdks/`.

Suppose I chose to download Xcode 7.3.1 (with the iOS 9.3 SDK) and I had Theos installed. My path to the SDK would be `/var/theos/sdks/iPhoneOS9.3.sdk`. For the sake of this tutorial, I am going to leave the SDK path as a placeholder (/path/to/sdk/iPhoneOS.sdk) that you can adjust to your liking.

Assuming you already have iFile or Filza open, let's create and run a shell script. This will symlink the essential programs and headers to their appropriate places.

```sh
#!/bin/bash
ln -s /usr/bin/clang /usr/bin/cc
ln -s /usr/bin/ranlib /usr/bin/armv7-apple-darwin11-ranlib
ln -s /usr/local/bin/perl /usr/bin/perl
ln -s /usr/include/openssl /path/to/sdk/iPhoneOS.sdk/usr/include/openssl
ln -s /usr/include/curl /path/to/sdk/iPhoneOS.sdk/usr/include/curl
ln -s /usr/include/libintl.h /path/to/sdk/iPhoneOS.sdk/usr/include/libintl.h
ln -s /usr/include/expat.h /path/to/sdk/iPhoneOS.sdk/usr/include/expat.h
ln -s /usr/include/expat_external.h /path/to/sdk/iPhoneOS.sdk/usr/include/expat_external.h
ln -s /usr/lib/libintl.8.0.2.dylib /path/to/sdk/iPhoneOS.sdk/usr/lib/libintl.dylib
ln -s /usr/lib/libcurl.4.dylib /path/to/sdk/iPhoneOS.sdk/usr/lib/libcurl.dylib
ln -s /usr/lib/libssl.0.9.8.dylib /path/to/sdk/iPhoneOS.sdk/usr/lib/libssl.dylib
ln -s /usr/lib/libcrypto.0.9.8.dylib /path/to/sdk/iPhoneOS.sdk/usr/lib/libcrypto.dylib
ln -s /usr/lib/libexpat.1.5.2.dylib /path/to/sdk/iPhoneOS.sdk/usr/lib/libexpat.dylib
```

After that's done, you're going to want to grab the Git source code (available [here](https://git-scm.com)). Unzip the source code to somewhere like `/var/mobile/git`.

Time to launch MobileTerminal. The first command you're going to run is `su`, which will ensure you have necessary permissions to build Git. The default password is `alpine` (all lowercase). Next, run `cd git` to open the Git source code directory. Finally, run the following script in MobileTerminal (replace the SDK path as necessary):

`make install prefix="/usr" CFLAGS="-isysroot /path/to/iPhoneOS.sdk" LDFLAGS="-Wl,-segalign,4000" DESTDIR="/var/mobile/git-build/" NO_INSTALL_HARDLINKS="1"`

Depending on your device, compilation time might take a few minutes. If everything went well, you should see a folder in `/var/mobile/` called `git-build`. Hooray! You built Git! Now you can package the compiled binaries into a Debian package, if you'd like.
