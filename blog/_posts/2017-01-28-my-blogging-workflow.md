---
layout: post
title: My blogging workflow
description: How I manage to be a productive blogger with Jekyll and Dropbox Paper.
image: dropbox-paper.png
tags: dropbox github jekyll web
---

At the time of this writing, and perhaps for the foreseeable future, this blog’s posts are written in Markdown. There’s no WordPress, Drupal, or other CMS being used to generate this site; it’s all built locally on my machine and published to the cloud. Additionally, every change I make is saved with Git, so if I ever feel nostalgic, I can look back to [simpler times.](https://github.com/citrusui/oldblog/tree/6d140e86a3de63c91d307e2563cff24477743758)

I started taking this blog seriously more than a year ago on January 2016. However, it was only until two months after where I actually started blogging with Jekyll on GitHub Pages…

<null></null>

In the midst of March, I went ahead and researched as much as I could about how others were bootstrapping their Jekyll blogs. At the time, [gem-based themes](https://jekyllrb.com/news/2016/07/26/jekyll-3-2-0-released/) had not yet been implemented, so I had to manually download a theme from GitHub, and unpack its contents into my blog’s root directory.

That was when I discovered the Jekyll theme [Poole.](http://getpoole.com) It was clean, fast, and mobile-friendly. Though the design is very minimal, it’s perfect for anyone new to the Jekyll/GitHub Pages workflow. Even though it isn't particularly flashy, it still looks pretty darn good [with a few tweaks.](http://hyde.getpoole.com)

Since I was now dealing with Markdown, I realized all I needed to write posts with was a text editor. For the most part, [Atom](https://atom.io) did the job well. Not only did it let me render Markdown with a live preview, it let me make changes to the entirety of my Jekyll-powered Git repository.

Unfortunately though, it became tedious having to pull out my laptop whenever I wanted to write a new blog post or make a small change. As a matter of fact, nearly all of my posts were written right from the Notes app on iOS, of which I had to manually copy from the iCloud web app to my local machine.

Eventually, I turned to [Simplenote](https://simplenote.com). The app was cross-platform, featured previewing in Markdown, and synced to all of my (mobile) devices. However, Simplenote still had its shortcomings when it came to Markdown support. It didn’t support displaying images, `:shorthand_emoji_codes:` , organizing posts into categories, nor syntax highlighting. Additionally, many blocks of code became hidden or appeared broken in Markdown previewing, due to Simplenote’s strange handling of elements in `<brackets>` . This compromise only lasted for a few weeks.

Yet again, I found myself searched the web in the hopes that I’d find a free, cross-platform, and aesthetically-pleasing Markdown app. Suddenly, I remembered the existence of [Dropbox Paper,](https://www.dropbox.com/paper) which I had registered interest to sometime in 2015. Again, switching services was not the easiest process, but this time around, I felt relieved that I could not only add images and emoji, but [embed tracks from SoundCloud,](https://www.dropbox.com/en/help/9167) easily insert and modify tables, organize documents into folders, and [export documents written in Paper to Markdown,](https://www.dropbox.com/help/9212) right from the web.

Is Dropbox Paper perfect? No. It’s obviously not meant to be used with Jekyll, but does satisfy my current needs, even as a product in beta. The mobile app is missing quite a few important features, such as creating new folders, inserting link titles, comments, and tables, embedding external media, and offline support. Similarly, there’s no word yet on whether Dropbox will release an official desktop client for Paper. Hopefully though, Dropbox will realize the potential Paper holds by taking it out of beta sooner rather than later. In the meantime, I’ve got my fingers crossed that it won’t be discontinued like Carousel and Mailbox were [last year.](https://blogs.dropbox.com/dropbox/2015/12/saying-goodbye-to-carousel-and-mailbox/)
