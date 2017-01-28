# [Avery's website](https://citrusui.me)


My minimal portfolio and blog, powered by [Jekyll](https://jekyllrb.com) and my [custom fork of Poole.](https://github.com/citrusui/poole)

# Development

## Build status

| <p style="text-align:center;margin:auto">master</p> | <p style="text-align:center;margin:auto">latest</p> |
|--------|--------|
| [![Build Status](https://travis-ci.org/citrusui/me.svg?branch=master)](https://travis-ci.org/citrusui/me) | [![Build Status](https://travis-ci.org/citrusui/me.svg?branch=latest)](https://travis-ci.org/citrusui/me) |

## Build scripts

`npm run clean`: Cleans up everything in `_site`.

`npm run dev`: Runs Jekyll using the `development` environment and watches for changes.

`npm run firebase`: Deploys to [Firebase](https://firebase.google.com) static hosting.

`npm run ipfs`: Deploys to [IPFS.](https://ipfs.io) Requires some [setup.](https://ipfs.io/docs/getting-started/)

`npm run jekyll`: Builds the current site into `_site` using Jekyll.

`npm run lint`: Lints all Sass files in `_sass/` according to rules in `.sass-lint.yml`.

`npm run prod`: Runs a Jekyll build using the `production` environment.

`npm run publish`: Cleans the currently built site, lints Sass files, builds a `production` site, deploys to IPFS, and finally to Firebase.

## Website

The [`latest`](https://github.com/citrusui/me/tree/latest) branch contains the newest changes, which are highly experimental and prone to status check failures or numerous other design quirks. If a build passes all status checks, it is automatically published to [dev.citrusui.me](https://dev.citrusui.me) via [Netlify.](https://www.netlify.com)

When the changes in [`latest`](https://github.com/citrusui/me/tree/latest) are deemed stable, a Pull Request is made merging the commits of [`latest`](https://github.com/citrusui/me/tree/latest) into the [`master`](https://github.com/citrusui/me/tree/master) branch. Shortly after, it is published to [npm](https://www.npmjs.com/package/citrusui.me) and [Firebase Hosting.](https://firebase.google.com/docs/hosting/)

# Terms

Code licensed under [MIT.](LICENSE.md) Blog posts (anything in [`blog/_posts`](https://github.com/citrusui/me/tree/master/blog/_posts)) licensed [CC-BY-SA 4.0.](blog/LICENSE.md)
