# goo grotto dev log

The dev-log blog for [Goo Grotto](https://goo-grotto.com), built with Jekyll 4.

## Local development

```sh
bundle install
bundle exec jekyll serve --livereload
```

The site builds to `_site/`. Visit <http://127.0.0.1:4000>.

## Writing a post

Add a Markdown file under `_posts/` named `YYYY-MM-DD-title.md` with front matter:

```yaml
---
layout: post
title: "Your title"
date: 2026-06-15 16:00:00 +0000
---
```

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the site
and publishes it to GitHub Pages. The custom domain is set via the `CNAME` file.