# CLAUDE.md

Guidance for Claude Code when working in this repository.

## Project

Hugo static site for **Prof. Atanas Kirjakovski's IBU blog** — lecture notes, reading materials, and presentations for psychology courses at International Balkan University. Deployed to `https://ibu.kirjakovski.mk` via AWS Amplify.

## Stack

- **Hugo** (static site generator) — `config.toml` (TOML, not Hugo's newer YAML/Hugo modules)
- **Theme**: [hugo-theme-yinyang](https://github.com/joway/hugo-theme-yinyang) — git submodule at `themes/hugo-theme-yinyang`. Don't edit theme files directly; override in `layouts/`.
- **Hosting**: AWS Amplify (`amplify.yml`) — runs `hugo --minify`, publishes `public/`.

## Commands

```bash
hugo server -D                  # local preview (includes drafts)
hugo --minify                   # production build → public/
hugo new posts/<section>/<slug>.md   # new post from archetype
git submodule update --init     # after fresh clone, to pull theme
```

## Layout

```
config.toml                     # site config (baseURL, taxonomies, params)
archetypes/default.md           # front-matter template for new posts
content/posts/                  # all content lives here
  general-discussion/
  social-psychology/            # LEC01..LEC06 + reading-materials.md, presentations.md
  experimental-psychology/      # same shape
  ethical-dilemmas-...-resources/
layouts/                        # overrides on top of the theme
  index.html, 404.html
  _default/{single,list}.html
  partials/{head,header,footer,seo,scripts,related,math,disqus}.html
  shortcodes/{youtube,a_blank,underline,caption}.html
  gallery/single.html
static/{css,js,fonts,images}    # assets (override theme assets by same path)
themes/hugo-theme-yinyang/      # submodule — read-only
public/                         # generated output (currently committed)
```

## Content conventions

- Lecture posts: `LEC##-YYYY-MM-DD.md` inside the course folder.
- Each course folder also has `reading-materials.md` and `presentations.md`.
- Front-matter fields used by templates:
  - `title`, `date`, `categories` (array), `draft` — standard
  - `deadline` — custom, rendered next to the post date in `layouts/_default/single.html`
  - `math: true` — opt-in math rendering via `partials/math.html`
  - `album` — image used for OG meta in `partials/head.html`
- Categories drive the top nav in `partials/header.html` (it iterates `.Site.Taxonomies.categories`). Adding a new category creates a new nav entry automatically.
- `mainSections = ["posts"]` in config — only `posts` renders post-style chrome (date, categories, related).

## Known rough edges

- `archetypes/default.md` hardcodes `categories: ["Organizational Psychology"]`, which doesn't match the current course set. Update categories per post or fix the archetype.
- No `.gitignore`; `.DS_Store` files and the entire `public/` build output are tracked. Don't make this worse — when adding files, avoid committing `.DS_Store` or build artifacts.
- `layouts/partials/header.html.bak` is a stale backup; safe to ignore, prefer not to resurrect.
- Theme is a submodule — after cloning or pulling, run `git submodule update --init` if `themes/hugo-theme-yinyang/` is empty.

## Editing rules of thumb

- Style/layout tweaks: override in `layouts/` or `static/css/index.css`, never in `themes/`.
- New shortcodes go in `layouts/shortcodes/`.
- When changing `config.toml` params, check whether `partials/head.html` or `header.html` reads them — most theme params are surfaced there.
- Build locally with `hugo --minify` before claiming a change is done; Amplify runs the same command.
