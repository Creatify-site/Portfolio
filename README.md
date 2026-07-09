# Creatify — Agency Portfolio

Creatify's agency portfolio site, built with [Hugo](https://gohugo.io/) and the [hugo-agency-web](https://github.com/writeonlycode/hugo-agency-web) theme (Tailwind CSS v4).

## Prerequisites

- [Hugo (extended)](https://gohugo.io/installation/) v0.147.8+
- [Node.js](https://nodejs.org/) + npm

## Getting Started

```bash
git clone --recurse-submodules https://github.com/Creatify-site/Portfolio.git
cd Portfolio
npm install
hugo server
```

The site will be running at `https://www.creatify.site/`.

If you already cloned without `--recurse-submodules`, fetch the theme with:

```bash
git submodule update --init --recursive
```

## Project Structure

- `content/` — pages and blog posts
- `data/` — structured content for homepage sections (hero, features, clients, etc.)
- `config/_default/` — site config, menus, and params
- `themes/hugo-agency-web/` — the Hugo theme (git submodule)

## Updating the Theme

```bash
git submodule update --remote --merge themes/hugo-agency-web
```

## Deployment

```bash
hugo --gc --minify
```

This generates a static site in `public/`, ready to deploy to Netlify, Vercel, or any static host.

### Deploying to Vercel

This repo includes a `vercel.json` with the build settings Vercel needs (`hugo --gc --minify`, output `public/`, `npm install` for the Tailwind CLI). To connect it:

1. [Import the repo](https://vercel.com/new) into Vercel.
2. In **Project Settings → Git**, enable **Git Submodules** — the theme is a submodule (`themes/hugo-agency-web`) and won't be cloned otherwise.
3. In **Project Settings → Environment Variables**, add `HUGO_VERSION` = `0.163.2` so Vercel builds with the same Hugo version used locally (must be extended edition, which Vercel provides automatically for recent versions).
4. Deploy. Every push to `main` will auto-deploy after this.

## License

Licensed under the [MIT License](LICENSE).
