---
layout: post
title: Enabling Google's Prototype Homepage Design
description: A prototype Material Design refresh for google.com.
image: google.png
tags: developer, google, search, web
---

**Update:** In my testing, it appears that either EditThisCookie or Google itself is removing the NID cookie when it is modified. This method may work for you, but only in certain circumstances.

---

The other day, I randomly stumbled upon a new design for Google's homepage. Luckily, at the time, I was able to capture all the current cookies for my session and track down the specific cause of this design change.

To start off, you're going need a desktop computer with [Chrome](https://www.google.com/chrome/) and [EditThisCookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg). Make sure you give the extension access in incognito mode via `chrome://extensions`.

<null></null>

Now, open a new incognito window (Command-Shift-N / CTRL+SHIFT+N) and navigate to Google. Then, click on the cookie icon at the top-right of Chrome (it should be to the left of the three vertical dots).

Expand the pane labeled `.google.com | NID`, and underneath the pane you should see an input box titled 'Value'. Copy the code below and paste it over the default-set value.

```
88=FTwOA3Yn5oxoQ_gTzkul5mRndwyC2eS67DIymmNsYJ5_B3qkjmB-KVK5ukx4IQ1-Scfbv_8eseBZdHiPHyn6j4Xg8U0qh7yQuREOZgeZ9AT0ZZ7hhQtYmAKjxIIjiljR7o3mry4lnjIXExi-VFo5BGdgW2_8T0nTd4rXPkPiIOH3A1_xqIvrYidHNuWpr6V4Zo9EAdJCuA
```

Reload the page, and if you are lucky, you should see Google Search turn into something like [this](https://imgur.com/lDBidtu)...

I'm keeping my fingers crossed that Google ships this design sooner rather than later. While it has a few bugs, it is much cleaner than the existing design.
