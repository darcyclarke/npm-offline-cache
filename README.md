# npm-offline-cache
An example of how to set up a **npm** project-specific cache/mirror of deps. This is similar, but different(?), to **yarn**'s [offline mode](https://yarnpkg.com/blog/2016/11/24/offline-mirror/). You can read more about **npm-cache** @ [docs.npmjs.com/cli/cache](https://docs.npmjs.com/cli/cache.html).

#### Steps to generate a project-specific cache

- Create an `.npmrc` file in your project's root with the following

```
 # choose a directory were you want to cache your deps
cache = ./npm_cache_mirror
```
- Run `npm install`
- Your `./npm_cache_mirror` directory will now have a cached version of all your deps

#### Notes

- If you want to check in this cache (which is somewhat expected) ensure you also check in your `package-lock.json` or `npm-shrinkwrap.json` files to ensure everything gets properly resolved
- You'll probably want to `.gitignore` your cache's log files but keep the folder to avoid any warnings/errors (ie. `npm_cache_mirror/_logs/*.log` & `npm_cache_mirror/anonymous-cli-metrics.json`)

#### Demo

You can test out this method of caching/mirroring deps by:

- Cloning this repo `git clone git@github.com:darcyclarke/npm-offline-cache.git`
- Turn off your network connection
- Install deps `npm install`
- All deps required to support [rawkit](https://www.npmjs.com/package/rawkit) & [sleepover](https://www.npmjs.com/package/sleepover) should be installed into `node_modules`
