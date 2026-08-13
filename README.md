# netomat-theme

Netomat brand layer on top of [PaperMod](https://github.com/adityatelange/hugo-PaperMod).
All three sites (website, blog, internal) import this theme so they look identical.

## How sites use it

Each site adds **two** submodules and layers them in `hugo.toml`:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
git submodule add ../netomat-theme.git themes/netomat
```

```toml
theme = ["netomat", "PaperMod"]   # left wins: netomat overrides PaperMod
```

## What lives here

- `assets/css/extended/` — brand CSS (PaperMod bundles these automatically)
- `layouts/shortcodes/email.html` — obfuscated mailto links: `{{</* email address="x@y.z" text="Email" */>}}`
- `static/images/` — logos
- `static/favicon/` — favicon set (reference via `params.assets` in each site)

## Rules

- **All** visual changes happen in this repo, never in a site's local `layouts/` —
  local overrides are how the three sites drift apart.
- After changing this repo: commit + push, then in each site
  `git submodule update --remote themes/netomat`, commit, push.
