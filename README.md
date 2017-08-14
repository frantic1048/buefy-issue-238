# buefy-issue-238

A repo for reproducing rafaelpimpa/buefy#238 .

## Build Setup

``` bash
# install dependencies
$ npm install # Or yarn install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, checkout the [Nuxt.js docs](https://github.com/nuxt/nuxt.js).

## Reproduce

Make sure the window is wide enough to not activate mobile card mode. This issue cannot be reproduced in mobile card mode.

Just click the `b-switch` on the index page.

When the switch is on, the `C`, `D` columns still exist while they should not.

Crucial source code is in `pages/index.vue`.
