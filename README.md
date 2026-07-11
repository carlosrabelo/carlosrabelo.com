# carlosrabelo.com

English engineering portfolio of Carlos Rabelo — software, systems architecture, network tooling, and open source.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hugo](https://img.shields.io/badge/Hugo-0.164.0-blue.svg)](https://gohugo.io/)

## Highlights

- Hugo Extended static site with a custom minimal theme
- English content with Atom and JSON feeds
- Open Graph, JSON-LD, and sitemap for SEO
- Deploy to GitHub Pages on every push to `master`

## Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) **0.164.0** (or compatible)
- Dart Sass (required by Hugo SCSS pipelines)

## Installation

```bash
git clone https://github.com/carlosrabelo/carlosrabelo.com.git
cd carlosrabelo.com
```

Install Hugo Extended matching the version in `.github/workflows/hugo.yml`.

## Usage

Local preview:

```bash
hugo server -D
```

Production build:

```bash
hugo --minify --baseURL "https://carlosrabelo.com/"
```

Output lands in `public/`.

### Optional: Utterances comments

1. Install the [Utterances](https://utteranc.es/) GitHub App on this repository.
2. In `config.toml`, uncomment `params.comments.githubRepo`.

## Project Layout

```
content/           Site content (projects, articles, about)
themes/maverick/   Custom Hugo theme (layouts, SCSS, static assets)
themes/nix/        Alternate terminal-inspired Hugo theme
themes/book/       Hugo Book documentation theme
static/            Site-wide static files (CNAME)
archetypes/        Content archetypes
.github/workflows/ GitHub Pages deploy
```

## Development

- `hugo server -D` — live reload with drafts
- `hugo --minify` — production build
- `hugo --printPathWarnings` — surface path issues (used in deploy)

Deploy runs on push to `master`.

Content markdown filenames stay in English.

Portuguese version: [carlosrabelo.com.br](https://carlosrabelo.com.br/).

## License

Site content and repository: [MIT](LICENSE).

Theme (`themes/maverick`): MIT — based on [Maverick](https://github.com/canhtran/maverick) by Calvin Tran, with modifications by Carlos Rabelo. See [themes/maverick/LICENSE](themes/maverick/LICENSE).
