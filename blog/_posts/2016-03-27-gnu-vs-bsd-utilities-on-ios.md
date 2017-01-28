---
layout: post
title: GNU vs BSD utilities on iOS
description: A closer look at what the iosbinpack means for the future of jailbreaking.
image: terminal.png
tags: developer ios jailbreak pangu
---

Surprise surprise, the Apple TV can now be jailbroken again! Hooray! But that’s not why I’m writing. No, something more (or less) interesting is with this jailbreak. It doesn’t come with saurik’s core utilities from Telesphoreo, it includes binaries from [https://opensource.apple.com](https://opensource.apple.com), compiled by none other than Jonathan Levin (AKA Morpheus). I call these iOS binaries the “iosbinpack” (based on its filename, of course).

Why is this important? Well, there are a couple of things:

- all binaries must be compiled for arm64 on the new Apple TV. saurik’s utilities haven’t been compiled for 64-bit yet
- these binaries also happen to work on watchOS
- the tools included are from BSD, not GNU, like saurik’s

<null></null>

In a nutshell, these are the tools every developer needs. It comes with a bunch of stuff, like dropbear (minimal SSH clone), jtool, procexp (Process Explorer), and the whole slew of BSD Utilities (cp, chown, gzip, etc.)

Because Pangu thought these binaries were good enough to use for the tvOS 9.0.x jailbreak, I decided to give them a try on iOS.

**Note:** don’t try installing the iosbinpack on anything device that’s running iOS 6 or lower — it won’t work.

The binaries, for the most part, are very good. They’re much more recent than the ones on Telesphoreo (which date back to 2009!). I do have several issues, though, (apart from them being BSD) which I believe should be addressed before I plan on compiling them into a Cydia package for others to use.

Here are some tools I’ve ran into issues with, which may plague 32-bit and 64-bit devices:

- login: it just doesn’t work. I don’t know why, but it wouldn’t let me enter the Terminal at any time. saurik’s version worked fine. 64-bit version works fine.
- zsh: It seems like one of the libraries/files it requires is malformed, specifically /usr/local/lib/zsh/5.0.8/zsh/zle.so.
- sysctl: very broken, also vnode errors.
- kextstat: does not work at all.
- ioreg: missing a few things and isn’t up to date.

### Here’s the kicker.

GNU and BSD utilities are slightly, but very different. As I said above, saurik uses GNU utilities. He even relies on using their special GNU arguments in various parts of Cydia. Therefore, switching over to BSD is not ideal, at least at this time. Tools like tar, cp, and chown act very differently between BSD and GNU. I talked to saurik about this; he has no plans to work around this. After pondering back and forth, I’ve attempted to stay neutral, and stay with GNU utilities, mainly because they “just work”. Yes, they are old and hacky, but they work. Perhaps Pangu will bundle the iosbinpack in the next jailbreak — who knows?

You can use the iosbinpack all you want — I’m not forcing you to stick with GNU. Just note that reinstalling GNU utilities will be a long and tedious process.

Thanks to [ReddestDream](https://github.com/ReddestDream) and [parrotgeek1](https://github.com/parrotgeek1) for contributing to this article. I really appreciate it!
