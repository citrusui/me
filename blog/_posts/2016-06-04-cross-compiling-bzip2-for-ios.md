---
layout: post
title: Cross-compiling bzip2 for iOS
description: Learn to cross-compile bzip2 on Linux for iOS devices.
image: bzip2.png
tags: cydia, developer, guide, ios, jailbreak
---

As detailed in my [previous blog post](https://citrusui.me/blog/2016/04/30/compiling-git-on-ios/), I showed you how to compile Git using an on-device toolchain. Now, I'll show you how to do something similar, but instead, on Linux.

First things first, we're going to need the iOS SDK and Linux Toolchain. You can download the former from [this website](https://sdks.website) and the latter from [here](https://developer.angelxwind.net/Linux/).

This tutorial assumes you are running Ubuntu 16.04 LTS. If this does not apply to you, then you may need to make some modifications to the following processes.

<!-- break -->

OK, now that you've got the SDK and Toolchain, it's time to extract them. Suppose my home directory was `/home/citrusui`.  Create two folders in this directory called `sdks` and `toolchain`, then unzip the files to these locations accordingly.

Now, it's time to download a script that automates the compiling process. Make sure you run this process as root or sudo!

```
#!/bin/bash
rm -rf ~/built/bzip2*
VER=1.0.6
CHAIN=~/toolchain/linux/iphone/bin/armv7-apple-darwin11
AR=$CHAIN-ar
CC=$CHAIN-clang
RANLIB=$CHAIN-ranlib
SDK=/home/citrusui/sdks/iPhoneOS9.3.sdk
CFLAGS="-arch armv7 -arch arm64 -isysroot $SDK"
LDFLAGS="-Wl,-segalign,4000"
PREFIX=~/built/bzip2/var/stash/usr
apt install bison clang libcurl4-openssl-dev xutils-dev
if [ -f bzip2-$VER.tar.gz ] && [ -d bzip2* ]; then
	echo "Already downloaded."
	cd bzip2*
	make clean
	make install CC="$CC" CFLAGS="$CFLAGS" RANLIB="$RANLIB" AR=$AR LDFLAGS="$LDFLAGS" PREFIX="$PREFIX"
	cd ~/built/bzip2
	lndir var/stash
	mkdir DEBIAN
	cd DEBIAN
  cp ~/build/bzip2-control control
  sed '/^Version:/ s/$/ $1.0.6/' control
	cd ../..
	dpkg-deb -Zgzip -b bzip2
	mv bzip2.deb bzip2_iphoneos-arm.deb
	exit 0
fi
curl -O http://www.bzip.org/$VER/bzip2-$VER.tar.gz
echo "Downloading..."
tar -xvzf bzip2-$VER.tar.gz
cd bzip2*
make clean
make install CC="$CC" CFLAGS="$CFLAGS" RANLIB="$RANLIB" AR=$AR LDFLAGS="$LDFLAGS" PREFIX="$PREFIX"
cd ~/built/bzip2
lndir var/stash
mkdir DEBIAN
cd DEBIAN
cp ~/build/bzip2-control control
sed -i '/^Version:/ s/$/1.0.6/' control
cd ../..
dpkg-deb -Zgzip -b bzip2
mv bzip2.deb bzip2_iphoneos-arm.deb
```

All right, what does this script do? Well...

- Clears out cache of any previously "built" versions of bzip2
- Sets the current version of bzip2 (1.0.6)
- Specifies which compiler to use (armv7-apple-darwin11-clang)
- Sets some CFLAGS and LDFLAGS in order to build for iOS
- Installs some dependencies needed for the compile process
- Downloads bzip2 source code
- Unzips source code, and compiles it
- Runs lndir to avoid any issues with Cydia stashing
- Copies the current version of bzip2 (1.0.6) to the Debian control file
- Packages the directory in ~/built/bzip2 into a .deb

You may notice that a file, aptly named "bzip2-control" is specified in this script too. This is a file that you'll need to add manually, in the same directory that you've saved bzip2.sh to. It should look something like this:

```
Package: bzip2
Priority: important
Section: Archiving
Maintainer: Your Name <your@email.com>
Architecture: iphoneos-arm
Version:
Description: Freely available high-quality data compressor
Homepage: http://www.bzip.org/
```

Make sure you leave a blank line at the bottom of your control file, or else `dpkg-deb` will return an error.

**Important Note:** I left out a step that involves running `ldid -S` on all of the bzip2 binaries. Without this step, iOS will refuse to run bzip2 (I think).

Hopefully this tutorial helped you cross-compile bzip2 for iOS! Feel free to upload the generated package to your personal Cydia repository. If I manage to get Git to properly cross-compile, I might make a follow-up to the previous blog post.
