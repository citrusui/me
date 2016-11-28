# [citrusui.me](https://citrusui.me)

# Status

[![Build Status](https://travis-ci.org/citrusui/me.svg?branch=master)](https://travis-ci.org/citrusui/me)
[![devDependencies Status](https://david-dm.org/citrusui/me/dev-status.svg)](https://david-dm.org/citrusui/me?type=dev)

My minimal portfolio. Clean and simple.

There's a lot of tweaks and modifications to the Sass files, but for the most part, this site uses [Poole](http://getpoole.com).

# Scripts

`npm run dev`: Runs Jekyll and checks for any new changes using LiveReload. Requires [extension](http://livereload.com/extensions/).

`npm run lint`: Lints all Sass files in `_sass` according to rules in `.sass-lint.yml`.

`npm run prepare`: Deploys to Firebase as production before publishing to npm. Requires npm@4.

`npm run prod`: Runs Jekyll with the `production` environment. This overrides `localhost` in favor of `site.url`.

## Terms

Licensed under [MIT](LICENSE.md). If you use any part of this code, please link back to this repository, thanks!
