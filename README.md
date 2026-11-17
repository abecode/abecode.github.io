# abecode.github.io

[Ebrahim (Abe) Kazemzadeh's homepage and blog](https://abecode.github.io/), built with [Quarto](https://quarto.org/).

## Develop locally

Install Quarto, then run:

```sh
quarto preview
```

To make a production build:

```sh
quarto render
```

The generated site is in ignored `_site/`; do not commit it. Posts live in `posts/<slug>/index.qmd` and appear on the homepage automatically. Give each post a title, date, and categories in its YAML front matter. The `aliases` on migrated posts keep their original Jekyll URLs working.

## Publish

In the repository's **Settings → Pages**, set **Build and deployment → Source** to **GitHub Actions**. The workflow renders and deploys the site when the `main` branch is pushed.

## WordPress archive

The 24 posts imported from [abewrites](https://abewrites.wordpress.com/) retain their original publication dates. Images and PDFs are stored locally in `assets/wordpress/`. See [_migration/README.md](_migration/README.md) and the accompanying manifest for source URLs and import details.
