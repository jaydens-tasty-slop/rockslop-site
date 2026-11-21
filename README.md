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
- **Players**: one file each, `players/<id>.md`, and that file is the single
  place for everything about the player: identity, prose, hardware values,
  download mode and USB IDs, battery runs, feature states and the status
  table. `_layouts/player.html` renders the page from it, and the comparison
  tables read the same files. Missing prose becomes a "Write me" box. To add
  a player, copy `players/yp3.md`. (Failed players live in
  `players/failed/` with `failed: true`, a `chip` and a `why:` table; extra
  prose goes in the body.)
- **Comparison tables**: `_data/hardware.yml` and `_data/features.yml` hold
  only the row names and their order. The values are in each player's file.
  States are defined in `_data/states.yml`.
- **Announcements**: blog posts in `_posts/` (`YYYY-MM-DD-title.md`, with a
  `title` and a one-line `description`). They list on `/announcements/`, the
  home page and the Atom feed at `/feed.xml`. The welcome post is filler.
- **Photos**: each player page has a Photos placeholder; set `photos:` in its
  front matter with images from `assets/images/<id>/`.
- **The call to action**: `releases_url` in `_config.yml`, used by every
  button.

The numbers in `_data/` were drafted from the rockbox-yp3 repo's docs on
2026-11-19. Check them before publishing.

## Deployment

GitHub Actions builds, validates and deploys `_site/` on every push to
`main`. In **Settings > Pages** set **Source** to **GitHub Actions**, and set
`rockslop.jayd.ml` as the custom domain (the `CNAME` file alone doesn't
configure it).
