---
layout: post
title: A week with Acer's Chromebook and Chrome OS
description: My experience with Acer's 15.6-inch Chromebook and Google's Chrome OS.
image: chrome.png
tags: chrome, developer, review
---

It’s been a week since I first received Acer’s Chromebook 15.6". I’d have to say -- I’m pleasantly surprised. Startup times are insane, the Chrome browser is solid, and the build quality is great (for a Chromebook, I suppose).

Normally I wouldn’t have opted for a device in pure white, seeing as it shows dirt and debris very easily. But… it’s all right, I can live with it. A minor downside of the color would very obviously be the lid -- after a few days of use, specks of dirt seem to become very apparent. I guess I’ll have to be more careful about where I put this thing.

<null></null>

The keyboard is well made. Coming from a Windows PC or Mac, it will take some getting used to, as Chrome OS has its own share of keyboard shortcuts to navigate through tabs and apps. One thing I wish I had here was backlit keys -- it’s a shame more laptops don’t come with them. Anyway, most people who have experience with Chromebooks will know that they lack a Caps Lock key. While this can be irritating to others, I’m happy with this change. I hardly need to SHOUT ONLINE. Before I get to the touchpad, though, I will note: I don’t like having the power button as a normal key on the keyboard. It’s awkward to press when starting up Chrome OS and I almost always accidentally hit it (at least one time) while trying to press the backspace key. Luckily, Google must have read my mind and made it so you have to hold the button for at least 3 seconds to completely shut down Chrome. I guess that’s fair.

The touchpad is quite tricky to use. You have three gestures: swipe with two fingers to go up and down a page, swipe with two fingers to the left to go back, and swipe with two fingers to the right to go forward. I find myself using the former the most often. The other two -- well… they’re just weird. My brain tells me that these gestures are in the wrong direction. I guess I’m just used to how other laptops handle multi-touch. Oh, and one more thing: it took me far too long to discover that right clicking on the touchpad doesn’t work. You need to tap with two fingers to trigger a “right click”. This gesture plays very well if you enable “Tap dragging”, an option buried in the advanced settings.

While I didn’t expect much from Chrome OS, I think I got everything I wanted. It doesn’t run many real “apps”, but that’s fine -- most things I do are online or in the cloud. It has a decent file manager, which mounts .zip files and images just like you’d expect. There’s a built-in Calculator, which is nice for quick calculations, and also a Camera app, which works kinda like Photo Booth on the iPad and Mac. Strangely enough, Google bundles what I assume is a third-party app called “Zip Extractor”, which just extracts the contents of a .zip archive and uploads it to your Google Drive. I wonder why that app is here -- perhaps it existed before Chrome OS had a file manager?

The fun part in owning a Chromebook is that you can run Linux side-by-side Chrome OS. Many already know you can do this with [crouton](https://github.com/dnschneid/crouton), a project started by a Google employee. The process is pretty straightforward:

- Enable Developer Mode (which wipes all user data)
- Sign back into Chrome OS
- Download the crouton utility
- Open the Chrome Shell (crosh) with CTRL+ALT+T
- Type `shell` and hit Enter
- Run crouton from your Downloads folder

All you need to know now is what your environment (chroot) you want to run alongside Chrome OS should look like. A typical install with Ubuntu 12.04 + the Xfce desktop would be run with `sudo sh ~/Downloads/crouton -t xfce`. You can also specify `-r` if you want a later version, such as Ubuntu 16.04 (Xenial Xerus). Just be warned: crouton hasn’t been updated to work with 16.04 AND Unity or Gnome desktops.

I did, in fact, run `crouton` on my own Chromebook. However, after many tries (and failed attempts), I gave up. Ubuntu 14.04 (Trusty Tahr) is nice, but surprisingly some apps require 16.04, which is unsupported by crouton at this time. I was also hoping USB devices would work properly in my chroot, but they only seem to mount properly in Chrome OS… bummer. Maybe I’ll try again when these issues are fixed, or try another method, such as ChrUbuntu.
