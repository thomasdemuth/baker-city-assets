# Baker City Assets

Image hosting for the Baker City modded Minecraft train server, served by GitHub Pages.

**Site:** https://thomasdemuth.github.io/baker-city-assets/

## How it works

- `index.html` is both the public gallery and the admin tool. It commits images to this
  repo through the GitHub API, so there is no server and no build step.
- `assets.json` is the database: every image's slug, path, dimensions, ratio tag, and
  last-updated date.
- General images live in `i/`, artwork in `art/`, advertisements in `ads/`.
- URLs are stable: replacing an image commits new bytes to the **same path**, so anything
  in the Minecraft world that points at the URL keeps working.

## One-time setup

1. Create a [fine-grained personal access token](https://github.com/settings/personal-access-tokens/new):
   - **Repository access:** only `baker-city-assets`
   - **Permissions:** Contents → Read and write
2. Open the site, click **Settings**, paste the token, save.
   The token lives only in that browser's localStorage. Without it, the page is a
   read-only gallery — safe to share.

## Usage

- **Upload:** drop images on either drop zone. The filename becomes the slug
  (`Station Logo.png` → `station-logo`).
- **Copy link:** every card has a Copy link button — paste that URL into the mod.
- **Replace:** swaps the image at the same URL. If the new file is a different format
  it is converted so the extension (and URL) never changes.
- **Ads:** each ad is auto-tagged with its nearest aspect ratio (overridable per card).
  Pick a ratio and hit **Copy random ad link** to get a random matching ad's URL.
- **Campaigns:** group ads via the campaign dropdown on each ad card, or pick an
  "Upload into" campaign above the ad drop zone to tag new uploads as they land
  ("New campaign…" creates one in either dropdown). Groups are collapsible (state
  remembered per browser), and the random picker can be filtered to a single campaign.

## Notes / limitations

- After an upload or replace, GitHub Pages takes ~30–60 s to publish before the URL
  serves the new bytes. Pages also caches for up to 10 minutes.
- Minecraft image mods usually cache a downloaded image per placement — after replacing
  an image you may need to reload chunks or rejoin to see the update in-world.
- GitHub Pages is static, so a single URL can't serve a *different random image per
  request*. The random-ad button picks randomly at copy time instead, which suits
  Minecraft anyway since mods cache whatever they fetch.
- Soft limits: 1 GB repo, 100 GB bandwidth/month — far beyond what this needs.
