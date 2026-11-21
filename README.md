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
- **Players**: one file each in `players/<id>.md`, rendered by
  `_layouts/player.html`. The file is only front matter (state, blurb, specs,
  and optional `intro`, `hardware`, `install`, `problems`, `photos`); missing
  prose becomes a "Write me" box. Status tables come from
  `_data/status/<id>.yml`, battery runs from `_data/battery.yml` (both keyed
  by the `player:` field). A new player is one new file, and it shows up in
  the nav, the players table and the feature table (add its column in
  `_data/features.yml`). States are defined in `_data/states.yml`.
- **Comparison tables**: `_data/features.yml` and `_data/hardware.yml`.
  Hardware columns marked `kind: failed` are the rejected players.
- **Announcements**: blog posts in `_posts/` (`YYYY-MM-DD-title.md`, with a
  `title` and a one-line `description`). They list on `/announcements/`, the
  home page and the Atom feed at `/feed.xml`. The welcome post is filler.
- **Failed Ports**: same template, in `players/failed/<id>.md` with
  `failed: true`, a `chip`, and a `why:` table. Extra prose goes in the body.
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
