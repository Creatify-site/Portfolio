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

The site will be running at `http://localhost:1313`.

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
hugo
```

This generates a static site in `public/`, ready to deploy to Netlify, Vercel, or any static host.

## License

Licensed under the [MIT License](LICENSE).
