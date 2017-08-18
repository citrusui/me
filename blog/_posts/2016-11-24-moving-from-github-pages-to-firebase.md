---
layout: post
title: Moving from GitHub Pages to Firebase
description: Why I chose Firebase over GitHub Pages for static hosting.
image: firebase.png
tags: github google jekyll web
---

Let me preface this by saying [GitHub Pages](https://pages.github.com) is awesome. Really. If you use it, great! If you don't, that's also great! Don't switch to or from Pages just because it's new or flashy. Assess the differences yourself, and decide which service works the best for _you_.

The beauty of Pages is its simplicity. Powered by [Jekyll](https://jekyllrb.com), Pages enables you to generate a static site using gorgeous templates, or your own content, right from your GitHub repository and onto the web, using either the default `github.io` domain, or a custom domain of your choosing.

So, why switch from GitHub Pages to [Firebase?](https://firebase.google.com) Well, it boils down to user control. There are some great Jekyll plugins out there that just can't be used with Pages because of the tight restrictions. While my main sites will be gradually moving away from Pages, I don't plan on ever making them closed source, or removing them from GitHub. Small projects like [rko-site](https://github.com/citrusui/rko-site) and [width](https://github.com/citrusui/width) will continue to be hosted on GitHub Pages.

<null></null>

Here's a super simple breakdown of the benefits and limits of both services:

# GitHub Pages

**Secure.** Pages only lets you use certain plugins. This can be a great thing, since there's no risk of external plugins running malicious code. However, it limits what you can do with your site. It would be great if you could at least use plugins available from [RubyGems.](https://rubygems.org)

**Friendly.** When you're using Pages, you don't need need to create a Gemfile or run `bundle install`. Every gem you want can be specified through `_config.yml`. The [Automatic Page Generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator/) even lets you generate a site without writing a _single line of code!_

# Firebase

**Full control.** Want to use the latest version of Jekyll, an external plugin, or a custom Jekyll theme? Go right ahead -- nothing's stopping you. However, if you come across an error in page building, or need some help with Jekyll, Firebase isn't going to hold your hand. This is certainly intimidating if you're new to web development.

**HTTPS for custom domains.** This is, without a doubt, awesome to have. It's always been possible to use Cloudflare's DNS with GitHub Pages, which I have no problem with, but it's always nice to have official support for encryption.

**Speed.** Don't get me wrong -- GitHub Pages is fast. But since it has to generate your site every time you push a commit, it takes a while for the changes to go live. With Firebase, you only need to deploy the `_site` directory and you're good to go. Additionally, you can rollback to a previous website deploy without even using Git! This is crucial if you accidentally break the content on your site.

**Flexibility.** You don't have to use Jekyll if you don't want to. The sky's the limit. Here is a [handy list](https://www.staticgen.com) of the top static site generators.

# Conclusion

I've decided to move to Firebase. While the migration will not be painless, in the long run, it will make my life a whole lot easier.
