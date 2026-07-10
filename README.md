# Creatify — Agency Portfolio

Creatify's agency portfolio site, built with [Hugo](https://gohugo.io/) and the [hugo-agency-web](https://github.com/writeonlycode/hugo-agency-web) theme (Tailwind CSS v4). Live at [creatify.site](https://www.creatify.site/).

## Prerequisites

- [Hugo (extended)](https://gohugo.io/installation/) v0.147.8+ (developed against v0.163.2)
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

## Pages

- **Home** (`/`) — hero with a rotating 3D service cube, services grid, "why choose us", about teaser, latest blog posts, platforms strip, testimonials (disabled until real quotes exist), CTA pair
- **About** (`/about`) — mission, vision, values, team bios
- **Services** (`/services`) — overview grid linking to 8 individual service pages (Web Development, Shopify Development, WordPress Development, SEO, Social Media Marketing, Graphic Designing, Video Editing, Digital Strategy), each with a process section and FAQ
- **Our Work** (`/projects`) — 26 Shopify store projects with category filtering and a hover-to-scroll screenshot preview
- **Blog** (`/blog`) — 19 posts across Shopify/HTML-5/SEO categories, with category filter pills and thumbnails
- **Contact** (`/contact`) — mailto-based contact form plus direct contact info

## Project Structure

- `content/` — pages and blog posts
- `data/` — structured content for homepage sections and the projects page (hero, services, about, projects, etc.)
- `config/_default/` — site config, menus, and params
- `layouts/` — **project-level template overrides**. The theme is never edited directly; any customization (new sections, bug fixes, new page types) lives here and mirrors the theme's own file paths so Hugo's template lookup resolves the project version first. See `layouts/_partials/blocks/home/` for the homepage section partials and `layouts/{about,services,projects,blog,contact}/` for page-specific templates.
- `themes/hugo-agency-web/` — the Hugo theme (git submodule, unmodified)
- `static/projects/` — Shopify store screenshots for the Our Work page (served directly, not through Hugo's image pipeline)

## Updating the Theme

```bash
git submodule update --remote --merge themes/hugo-agency-web
```

Because customizations live in project-level `layouts/` overrides rather than edits to the submodule, pulling a theme update should not clobber any site-specific changes.

## SEO

- `robots.txt` and `sitemap.xml` are custom templates (`layouts/robots.txt`, `layouts/sitemap.xml`) — the sitemap excludes the auto-generated `/tags/*` archive pages to avoid indexing thin, single-post taxonomy pages
- Structured data (`layouts/_partials/schema.html`): `ProfessionalService` + `WebSite` sitewide, `BlogPosting` on posts, `Service` on service pages
- `markup.goldmark.renderer.unsafe: true` is enabled in `hugo.yaml` so tutorial posts can include raw HTML/Liquid code blocks

## Deployment

```bash
hugo --gc --minify
```

This generates a static site in `public/`, ready to deploy to Netlify, Vercel, or any static host.

### Deploying to Vercel

This repo includes a `vercel.json` with the build settings Vercel needs (`hugo --gc --minify`, output `public/`, `npm install` for the Tailwind CLI) plus baseline security headers. To connect it:

1. [Import the repo](https://vercel.com/new) into Vercel.
2. In **Project Settings → Git**, enable **Git Submodules** — the theme is a submodule (`themes/hugo-agency-web`) and won't be cloned otherwise.
3. In **Project Settings → Environment Variables**, add `HUGO_VERSION` = `0.163.2` so Vercel builds with the same Hugo version used locally (must be extended edition, which Vercel provides automatically for recent versions).
4. Deploy. Every push to `main` will auto-deploy after this.

The site is served at `www.creatify.site` — `baseURL` in `config/_default/hugo.yaml` must match whichever host (apex or `www`) your DNS/host enforces as canonical, or sitemap/schema/OG URLs will all carry an unnecessary redirect.

## License

Licensed under the [MIT License](LICENSE).
