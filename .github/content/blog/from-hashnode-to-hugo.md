---
title: 'From Hashnode to Hugo: Notes From the Move'
date: 2026-07-19
authors:
  - name: Saurav Jalui
    link: https://github.com/sauravjalui
    image: https://github.com/sauravjalui.png
tags:
  - Hugo
  - Hashnode
  - Meta
category: 'Writing'
images:
  - /images/post-hashnode.jpg
---

![From a hosted platform to my own stack](/images/post-hashnode.webp)

This blog has a new home. It used to live on Hashnode; it now runs on [Hugo](https://gohugo.io) with the [Hextra](https://github.com/imfing/hextra) theme, builds on GitHub Actions, and serves for free from GitHub Pages: same domain, same URLs.

## Why move

Hashnode was a great starting point, but in 2026 custom domains moved behind their new Pro plan, and that nudged me toward something I'd been meaning to do anyway: own the whole stack. Now every post is a Markdown file in a Git repo. No platform, no lock-in, no surprises.

## The stack

The setup is small enough to describe in one breath: Hugo builds the site, Hextra makes it look good, a GitHub Actions workflow deploys on every push, and four DNS records point the domain at GitHub Pages. Keeping the old URL structure was one config line:

```yaml
permalinks:
  blog: /:slug/
```

That single line is what preserves years of links and search rankings across the move.

## What broke along the way

Almost nothing, except the time I copied a shortcode block from a _rendered_ Markdown view and it silently injected blockquote markers into the file, breaking the build with the world's most cryptic error. Lesson learned: always copy from the raw source.

## What's next

Migrating the full archive over from the Hashnode export, rehosting the images, and then getting back to actually writing. If you're reading this on sauravjalui.com over HTTPS, every piece of the pipeline above did its job.
