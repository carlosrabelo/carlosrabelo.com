# Book

[Hugo Book](https://github.com/alex-shpak/hugo-book) documentation theme, vendored for [carlosrabelo.com.br](https://carlosrabelo.com.br/) with site-specific overlays (feeds, Utterances, home post list).

## Switch theme

```bash
cp config.book.toml config.toml       # use Book
cp config.maverick.toml config.toml   # use Maverick
cp config.nix.toml config.toml        # use Nix
```

## Site overlays

- `layouts/home.html` — home lists posts
- `layouts/index.json` / `index.xml` / `robots.txt` — feeds and robots
- `layouts/_partials/docs/comments.html` — Utterances via `params.comments`
- `layouts/_partials/docs/inject/*` — feed discovery and social/footer links

Upstream: [alex-shpak/hugo-book](https://github.com/alex-shpak/hugo-book) (MIT).
