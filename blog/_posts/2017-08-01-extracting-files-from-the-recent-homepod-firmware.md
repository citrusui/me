---
layout: post
title: Extracting files from the recent HomePod OTA firmware
description: How to extract files from HomePod's prerelease audioOS firmware.
image: homepod.png
tags: developer, homepod, ios
---

If you [haven't](https://twitter.com/iOSReleases/status/890727145487691777) [already](https://9to5mac.com/2017/07/28/homepod-firmware-details/) [heard,](https://www.macrumors.com/2017/07/29/homepod-firmware-details-apple-smart-speaker/) Apple accidentally published a prerelease build of audioOS through their public update servers. Whether or not this leak was "intentional" is up for debate, but I personally believe it to be a mistake.

<null></null>

<div class="message">
<strong>WARNING:</strong> This tutorial is not for the faint of heart! Only proceed if you are familiar with UNIX-based operating systems. I <strong>cannot</strong> provide guidance to those who are unfamiliar with the command line.
</div>

To start off, you’re going to want to fetch the OTA firmware from this [direct link.](https://secure-appldnld.apple.com/ios11.0seeds/091-23521-20170827-D4B9565E-731F-11E7-89EE-CBC601BA0AE3/com_apple_MobileAsset_SoftwareUpdate/6841e048050f1f38ecc68977bbdc76d746da6559.zip) The link is hosted by Apple and has not been tampered with.

Once you've finished downloading the firmware, go ahead and unzip it. For the sake of brevity, I recommended you rename the folder to something more memorable, like `firmware`.

<img data-src="https://user-images.githubusercontent.com/9056756/28853854-52517698-7701-11e7-9e5e-294dcacc3f9c.png" class="lazyload">

Let's open the `firmware` folder. We're looking for a file named `payload`. Navigate to `firmware/AssetData/payloadv2` and you'll find the payload file. Copy this file to your Desktop or to the root of your `~/Downloads` folder.

<img data-src="https://user-images.githubusercontent.com/9056756/28853863-5d6b11ec-7701-11e7-9795-974385bd40a3.png" class="lazyload">

Ensure you have the appropriate Developer Tools installed. If you’re running macOS, open Terminal and run `sudo xcode-select --install`. I already have Xcode installed, so `xcode-select` kindly warns me with the message depicted above.

To extract the `payload`, we are going to use two of Jonathon Levin's tools; [pbzx](http://www.newosxbook.com/src.jl?tree=listings&file=pbzx.c) and [ota.](http://www.newosxbook.com/src.jl?tree=listings&file=ota.c)  For the sake of convenience, you may grab the tools from matteyeux’s unofficial [GitHub repo.](https://github.com/matteyeux/iOS-Utilities)

With the terminal window still open, clone the repository linked above with the following command:

```
git clone https://github.com/matteyeux/iOS-Utilities
```

Then, compile the code:

```
cd iOS-Utilities
make
```

<img data-src="https://user-images.githubusercontent.com/9056756/28853826-258f6840-7701-11e7-816e-eb7ff01e83bb.png" class="lazyload">

At this point, you probably want to move the compiled binaries to somewhere easily accessible on your system. The following commands will move them all to your Downloads folder:

```
mv ./pbzx ~/Downloads
mv ./ota ~/Downloads
cd ~/Downloads
```

Now, let’s run pbzx:

```
./pbzx < payload > payload2.xz
```

To decompress the newly-created `payload2.xz`, install [brew](https://brew.sh), and then install xz using the commands below:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install xz
xz --decompress payload2.xz
```

This will take a while. Be patient and wait for all of the commands to finish completely.

Finally, run `ota` to extract the payload files in all their glory:

```
./ota -e '*' payload2
```

When the command finishes, you should see the following new folders. They are highlighted in blue below.

<img data-src="https://user-images.githubusercontent.com/9056756/28853846-3fef0d9e-7701-11e7-8f1a-7b5475e032ec.png" class="lazyload">

## In Conclusion

Sifting through the HomePod’s firmware is actually quite simple! Once you figure out all of the steps, everything else is a piece of cake. I encourage you to go and explore what else is lurking in audioOS!