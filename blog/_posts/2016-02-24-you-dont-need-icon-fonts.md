---
layout: post
title: You don't need icon fonts.
description: Why icon fonts are a not-so-good idea.
image: fontawesome.png
tags: developer, fonts, github, web
---

So, after reading GitHub’s [blog post](https://github.com/blog/2112-delivering-octicons-with-svg) about serving Octicons exclusively over SVG, I started to look into what I can do for my own site, [citrusui.me](https://citrusui.me).

One of huge reasons to switch from icon fonts was *speed*. Every time you embed an icon font into your page or pages, your browser has to load the stylesheet and font files, then load each individual icon. Now, this isn’t really efficient, considering most sites don’t need 100 icons. I only need 13 icons.

Another reason would be the “blink” you get when loading a page with an icon font. What the browser ends up doing is loading the icons last, leaving a blank space where the icons should be until the font has finished downloading.

<null></null>

GitHub also noted something very important: **accessibility**. Some users use OpenDyslexic, a font designed specifically for users with Dyslexia. When users override the normal fonts with OpenDyslexic, the icon font ends up not loading 🙁. Just blank squares in place of where the images should be.

Luckily, SVG solves all of this. No need for stylesheets, WOFF, or special classes. Just use the following code:

```html
<img src=”/path/to/svg.svg” width=”yourwidth”>
```

...and you’re good to go. SVGs are really, really small. If you optimize them with SVGO, you can get each icon to less than or about a kilobyte each. They load in a *jiffy*.

Of course, icon fonts have also been served via SVG “sprites”, but, again, this is not very efficient: you needn’t load all your icons on a page if you’re not using them all.

I’d also like to bring up Fort Awesome (AKA Fonticons). While Fort Awesome *is* awesome, it’s limited to 20 icons on the free tier. Moreover, you can’t even use other icon sets unless you pay up. Not cool.

Whatever your opinion is, I’d encourage you to learn more about the advantages of SVG over CSS icon fonts. Don’t take it from me — go ask others! Bootstrap v4 is a good example; the core team is dropping Glyphicons in their latest major release. While it’s not necessarily related to SVG vs. icon fonts, it’s nice to see the team is letting users decide on their own if they want to use icons on their website or not. That’s something I really look forward to.
