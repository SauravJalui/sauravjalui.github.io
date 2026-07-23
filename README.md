# sauravjalui.com

[![Deploy](https://github.com/sauravjalui/sauravjalui.github.io/actions/workflows/pages.yaml/badge.svg)](https://github.com/sauravjalui/sauravjalui.github.io/actions/workflows/pages.yaml)

Source for my personal site and blog, live at **[sauravjalui.com](https://sauravjalui.com)**.

I'm a developer-turned-product manager in Mumbai. I write case studies about the
platform work I do: internal tools people resist, migrations off spreadsheets, and
design notes published before the build so the follow-up has something to check
against.

**Recent writing**

- [Getting a Company Off Excel Without a Revolt](https://sauravjalui.com/blog/excel-to-portal/): running the portal and the spreadsheet in parallel, team by team
- [The Tool Was Faster. They Still Wanted the Spreadsheet Back.](https://sauravjalui.com/blog/scheduling-portal/): adoption as a trust problem
- [The Most Ambitious Thing I Haven't Built Yet](https://sauravjalui.com/blog/marketing-crm/): a CRM design note, written before the build

## Stack

| | |
|---|---|
| Generator | [Hugo](https://gohugo.io) (extended) |
| Theme | [Hextra](https://github.com/imfing/hextra), pulled as a Hugo Module |
| Hosting | GitHub Pages, free tier |
| CI | GitHub Actions, builds and deploys on every push to `main` |
| DNS | Namecheap, `CNAME` to GitHub Pages |
| Analytics | Google Analytics 4 |

No Node, no bundler, no npm install. Hugo compiles the Tailwind-based theme CSS
itself and everything ships as static files.

## Local development

Requires [Hugo extended](https://gohugo.io/installation/), [Go](https://go.dev/doc/install)
(for Hugo Modules) and Git.

```shell
git clone https://github.com/sauravjalui/sauravjalui.github.io.git
cd sauravjalui.github.io

hugo mod get -u
hugo server --gc --disableFastRender
```

Then open http://localhost:1313.

The `--gc` flag matters. Hugo caches the concatenated CSS bundle in `resources/`,
and without it you will keep seeing stale styles after editing
`assets/css/custom.css`. If something still looks wrong, clear the cache outright:

```shell
rm -rf resources public
```

## Layout

```
content/          markdown: homepage, about, resume, blog posts
assets/css/       custom.css, the only stylesheet I maintain
layouts/          template overrides (blog list, robots.txt, head partial)
static/           images, fonts, favicons, resume PDF
hugo.yaml         menu, logo, analytics, site params
```

Theme templates live in the Hugo Module, not in this repo. To change something the
theme controls, override it under `layouts/` rather than editing the module.

## Deployment

Push to `main`. The workflow in
[`.github/workflows/pages.yaml`](.github/workflows/pages.yaml) builds with Hugo and
publishes to GitHub Pages. Nothing to run by hand.

CSS and favicons cache hard in browsers, so verify a deploy in a private window
before deciding something did not ship.

## Licence

Code and configuration are MIT, see [LICENSE](LICENSE). Post content, images and the
resume are © Saurav Jalui, all rights reserved.
