# [citrusui.me](https://citrusui.me)

My minimal portfolio and blog, powered by [Jekyll](https://jekyllrb.com) and my [custom fork of Poole.](https://github.com/citrusui/poole)

# Development

## Scripts

`npm run clean`: Removes the `_site` folder.

`npm run dev`: Runs Jekyll using the `development` environment and watches for changes.

`npm run firebase`: Deploys to [Firebase](https://firebase.google.com) static hosting.

`npm run jekyll`: Builds the current site into `_site` using Jekyll.

`npm run lint`: Lints all Sass files in `_sass/` according to rules in `.sass-lint.yml`.

`npm run min`: Minifies HTML output using [html-minifier.](https://www.npmjs.com/package/html-minifier)

`npm run prod`: Runs a Jekyll build using the `production` environment.

`npm run publish`: Removes the previously built site, lints Sass files, builds a `production` site, minifies HTML output, and deploys to Firebase.

## Process

The [`master`](https://github.com/citrusui/me/tree/master) branch contains the newest changes and should not be considered stable. After each commit, various tests are run. If a commit passes all of its tests, it is then built and automatically published to [dev.citrusui.me](https://dev.citrusui.me) via [Netlify.](https://www.netlify.com)

When the changes in [`master`](https://github.com/citrusui/me/tree/master) are deemed stable, the `version` key in [package.json](https://github.com/citrusui/me/blob/master/package.json) is incremented and published as a Git release tag. These changes are then published to [npm](https://www.npmjs.com/package/citrusui.me) and [Firebase Hosting.](https://firebase.google.com/docs/hosting/)

# Terms

Code licensed under [MIT.](LICENSE.md) Blog posts (anything in [`blog/_posts`](https://github.com/citrusui/me/tree/master/blog/_posts)) licensed [CC-BY-NC-SA 4.0.](blog/LICENSE.md)
