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

The generated site is in `_site/`. Posts live in `posts/<slug>/index.qmd` and appear on the homepage automatically. Give each post a title, date, and categories in its YAML front matter. The `aliases` on migrated posts keep their original Jekyll URLs working.

## Publish

The GitHub Actions workflow builds and deploys the site on pushes to `master`. In the repository's **Settings → Pages**, set **Build and deployment → Source** to **GitHub Actions**. Then merge the Quarto branch into `master`. The workflow can also be run manually from the Actions tab.
