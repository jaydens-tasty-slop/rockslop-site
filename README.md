# rockslop-site

Public site for [rockslop.jayd.ml](https://rockslop.jayd.ml), the homepage of
the rockslop project (a Rockbox flasher for cheap MP3 players).

Jekyll + [Just the Docs](https://just-the-docs.com), deployed with GitHub
Pages. The look (quiet dark theme with a chequered strip and a yellow button) is
mostly colours: `_sass/color_schemes/rockslop.scss` and `_sass/custom/custom.scss`.

## Working on it

```
make setup    # install gems into vendor/bundle
make dev      # live-reload server on http://127.0.0.1:4000
make check    # production build + html-proofer
make drafts   # list every WRITE ME placeholder still left
make help
```

## Where things live

- **Prose**: all of it is filler. Every `{% include todo.html text="..." %}`
  renders a dashed "WRITE ME" box saying what belongs there; delete the
  include when you've written the real text.
- **Ports**: `ports/<id>.md`. Status tables come from `_data/status/<id>.yml`
  (states are defined in `_data/states.yml`). Add a port to `_data/ports.yml`
  for the home page cards and the feature table.
- **Comparison tables**: `_data/features.yml` and `_data/hardware.yml`.
  Hardware columns marked `kind: failed` are the rejected players.
- **Announcements**: blog posts in `_posts/` (`YYYY-MM-DD-title.md`, with a
  `title` and a one-line `description`). They list on `/announcements/`, the
  home page and the Atom feed at `/feed.xml`. The welcome post is filler.
- **Failed ports**: `failed-ports.md`.
- **Photos**: each port page has a Photos placeholder; replace it with
  Markdown images from `assets/images/<port>/`.
- **The call to action**: `releases_url` in `_config.yml`, used by every
  button.

The numbers in `_data/` were drafted from the rockbox-yp3 repo's docs on
2026-11-19. Check them before publishing.

## Deployment

GitHub Actions builds, validates and deploys `_site/` on every push to
`main`. In **Settings > Pages** set **Source** to **GitHub Actions**, and set
`rockslop.jayd.ml` as the custom domain (the `CNAME` file alone doesn't
configure it).
