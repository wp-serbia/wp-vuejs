# WP VueJS

This is just a simple Vue application (built with Vue 3 and [Vite](https://vite.dev/)) that pulls posts from a WordPress REST API endpoint. Clone or fork this sucka & rip it apart to suit your own needs. If you have ideas to make it better for everyone else, contribute!

## Install

In the root of the project, run `nvm install`, `nvm use`, then `yarn install --frozen-lockfile` with Yarn Classic 1.22.

## Usage

### Set Your Environment Variables

Various important values are loaded into the application via Node environment variables, which you'll need to define. Locally, run `cp .env.sample .env.local` to create a local file for defining the following:

- `REST_ENDPOINT` - The WordPress REST API endpoint from which data will be pulled. Leave off the trailing slash. Example: `https://blah-blah-blah.com/wp-json/wp/v2`
- `POSTS_PER_PAGE` - The default number of posts per page that will be displayed.
- `GA_TRACKING_ID` - An optional GA4 measurement ID (G-...). Leave blank to disable tracking.
- `REQUEST_CACHE_MAX` - The maximum number of AJAX requests that will be cached in memory.

When deploying this on your own, you'll need to have these values set through a `.env` file you ship yourself, or if you're using something like Netlify, you can define them in your dashboard.

### Spin Up Locally

Run `yarn serve` to spin up a running version from localhost.

### Build for Production

Run `yarn build`.

### Deploy to Netlify

To keep the same production URL, open the existing Netlify project that owns that URL. Under **Project configuration → Developer settings → Continuous deployment → Repository**, link `wp-serbia/wp-vuejs`. If the old repository is listed, choose **Manage repository → Link to a different repository**. Set the production branch to `master` if that is the branch you publish from.

Once linked, push commits to the production branch. Netlify builds and publishes each update to the same project. [Netlify repository linking guide](https://docs.netlify.com/build/git-workflows/repo-permissions-linking/)

**Create a separate site from this template** only if you want a new Netlify project. The button below starts that workflow.

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/wp-serbia/wp-vuejs)

## Caching

Out of the box, WP Vue will locally cache AJAX requests in memory, and then load them as needed. This first happens on page load, when all queried posts on the current and adjacent pages are cached for quick access later.

To keep things from getting out of control, a maximum request cache value is set. Once your cache reaches this max (regardless of how large each request is), the first request in memory will deleted as a new one is added. So, you shouldn't have to worry too much about an insane amount of data being locally stored as you move through posts.

Manually reloading the page will kill this cache. It will not persist.

## Set Endpoint via URL Parameter

If you'd like to share link to a version of WP Vue that uses a different endpoint than what's set via the code, you can pass that endpoint in as a URL parameter:

Example: `https://wp-vue-app.netlify.com?endpoint=https://css-tricks.com/wp-json/wp/v2`

Instead of using the default, this will use whatever endpoint you provide in the URL.

## Changelog

### 2.0.0 (2026-11-25)

- Migrated the app to Vue 3, Vue Router 4, and Vuex 4.
- Replaced Vue CLI with Vite and `node-sass` with Dart Sass. For local development, use `nvm use` to select Node 22.14.0 and install dependencies with Yarn Classic 1.22.22.
- Fixed featured images on individual posts and redirected missing posts to the 404 page.
- Updated optional analytics to GA4. If you used a Universal Analytics `UA-` ID, set `GA_TRACKING_ID` to your GA4 measurement ID (`G-…`) to continue tracking.

## Contribute

Please do! See the <CONTRIBUTING.md> for details.

## License

MIT © [Web Studio](https://web-studio.dev)
