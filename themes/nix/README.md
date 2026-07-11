# Nix

Terminal-inspired Hugo theme for [carlosrabelo.com.br](https://carlosrabelo.com.br/), based on [hugo-theme-nix](https://github.com/LordMathis/hugo-theme-nix) with the same site capabilities as `maverick` (feeds, SEO, comments, tags, pagination).

## Switch theme

Theme configs live at the site root. Activate one by copying it over `config.toml`:

```bash
cp config.nix.toml config.toml       # use Nix
cp config.maverick.toml config.toml  # use Maverick
cp config.book.toml config.toml      # use Book
```

Edit `config.*.toml` for theme-specific params; keep `config.toml` as the active copy.

MIT licensed — see [LICENSE.md](LICENSE.md).
