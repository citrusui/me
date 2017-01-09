# [Avery's website](https://citrusui.me)

[![Build Status](https://travis-ci.org/citrusui/me.svg?branch=master)](https://travis-ci.org/citrusui/me)
[![devDependencies Status](https://david-dm.org/citrusui/me/dev-status.svg)](https://david-dm.org/citrusui/me?type=dev)

My minimal portfolio and blog, powered by [Jekyll](https://jekyllrb.com) and my [custom fork of Poole.](https://github.com/citrusui/poole)

# Scripts

If you're interested in running this project locally, use the following scripts:

`npm run dev`: Runs Jekyll using the `development` environment and watches for changes.

`npm run firebase`: Deploys to [Firebase](https://firebase.google.com) static hosting.

`npm run ipfs`: Deploys to [IPFS.](https://ipfs.io) Requires some [setup.](https://ipfs.io/docs/getting-started/)

`npm run jekyll`: Builds the current site into `_site` using Jekyll.

`npm run lint`: Lints all Sass files in `_sass/` according to rules in `.sass-lint.yml`.

`npm run prod`: Runs a Jekyll build using the `production` environment.

`npm run publish`: Lints Sass files, builds a `production` site, deploys to IPFS, and finally to Firebase.

## Terms

Code licensed under [MIT.](LICENSE.md) Blog posts (anything in `blog/_posts`) licensed [CC-BY-SA 4.0.](blog/LICENSE.md)
