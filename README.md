# The SwapWright website

Built by `node scripts/build-site.mjs`. Everything in this folder is generated —
edit the generator, not these files.

Privacy and Terms are rendered from `src/legal.js`, the same module the app
serves, so what the website promises and what the product promises cannot drift
apart. Rebuild after changing either.

## Deploying

Copy this folder anywhere that serves static files over https.

**GitHub Pages** — free, gives `https://<you>.github.io/<repo>/`
1. Create a public repo, e.g. `swapwright-site`
2. Copy the contents of `site/` into it and push
3. Settings → Pages → Source: deploy from branch, root
4. The address appears there in a minute or two

**Cloudflare Pages** — free, gives `https://<project>.pages.dev`
1. Create a project, connect the repo (or drag this folder into the dashboard)
2. No build command; output directory `/`

Either address is a valid answer to Lemon Squeezy's "Website URL". A custom
domain can be pointed at either later for about $12 a year.

## After deploying

- [ ] Set `updateFeedUrl` in the app's settings to `<your-site>/latest.json`.
      Until then the app can never tell anyone a new version exists.
- [ ] Rebuild with the real store link: `BUY_URL=https://... node scripts/build-site.mjs`
      (it is `#` until you do, so the button goes nowhere)
- [ ] Re-take the screenshots whenever the app's look changes — they are
      `dashboard.png` and `setup.png`, captured from the running app

## On each release

1. Edit `release/latest.json`: bump `version`, set `date`, replace `notes`
2. `node scripts/build-site.mjs`
3. Redeploy
