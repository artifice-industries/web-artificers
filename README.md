# web-artificers

Source of the Artificers studio website — [artificers.co.uk](https://artificers.co.uk).

Built with [Zola](https://www.getzola.org/) (static site generator) and deployed to GitHub Pages on every push to `main`.

## Develop

Requires Zola (`brew install zola`).

```sh
zola serve     # live-reload dev server at http://127.0.0.1:1111
zola build     # static output → ./public
zola check     # validate internal + external links
```

## Structure

```
config.toml            site config (base_url, sass, metadata)
data/projects.toml     single source of truth for the Projects grid
content/               markdown pages (_index = home; privacy)
templates/             Tera templates (base, index, page) + partials/
sass/main.scss         design tokens + components (compiled to /main.css)
static/                robots.txt, CNAME, project icons and artwork
```

## Pages

| Route      | Content        |
|------------|----------------|
| `/`        | Studio home: hero and the Projects grid |
| `/privacy` | Privacy policy |

`/playback` and `/swift-eos-kit` redirect to `/` to keep old deep links alive.

## Deploy

`.github/workflows/deploy.yml` builds the site and publishes it to GitHub Pages via `actions/deploy-pages`. `static/CNAME` carries the custom domain. Pull requests get a build check from `.github/workflows/ci.yml`.
