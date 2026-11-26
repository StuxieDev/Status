# Changelog

All notable changes to StuxieDev's status page (status.stuxie.dev) are documented here. Since
v26.10.23 this project uses [Date Versioning](https://datevers.ing) (`YY.MM.DD`, the UTC release date, with `-1`, `-2`…
for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v26.11.26-1

### Added

- **Fluxer.Life is monitored**: fluxer.life, an unofficial fan project for the Fluxer chat app, coming soon for now.
  It's in the Projects group and checks the site's `/api/health`. Its slug is `fluxer-life`.

## v26.11.26

### Added

- **Fluxer.Now is monitored**: fluxer-now.stuxie.dev, guides for moving from Discord to Fluxer, built and maintained by
  StuxieDev for FluxerHost. It's in the Projects group and checks the site's `/api/health`, and its slug, `fluxer-now`,
  gives the Projects site's Fluxer.Now card a live status badge.

## v26.11.22

### Added

- **Fluxer Music is monitored**: fluxer.music, the Fluxer Music community's website, now that it's live. It's in the
  Projects group, and its slug, `fluxer-music`, gives the Projects site's Fluxer Music card a live status badge.

## v26.11.21

### Added

- **StuxieDev Social is monitored**: social.stuxie.dev, StuxieDev's Fediverse server, now that it's live. It's listed at
  the top of the page with StuxieDev Links, and its slug, `stuxiedev-social`, gives the Projects site's StuxieDev
  Social card a live status badge.

## v26.11.15-2

### Changed

- **The workflow's 5-minute schedule comment says what really happens.** It used to say GitHub "may run it a little
  late"; it now says the workflow asks GitHub for a check every 5 minutes and that GitHub, which runs schedules
  best-effort, often runs it less often (the status page measures about one check every 45 minutes). Only the comment
  changed: the schedules are the same.

## v26.11.15-1

### Changed

- **A `staging` branch between `test` and `main`.** Changes now go live in two steps, through pull requests: `test` →
  `staging`, then `staging` → `main`. Nothing is pushed to `staging` or `main` directly. The page is still built from
  `main`, where the monitoring data is committed. CONTRIBUTING.md has a new "Branches and going live" section, and the
  README's Versioning section says how releases move.
- **`commit.sh` and `commit.bat` refuse to run on `staging` or `main`**, since releases are made on `test`. After
  tagging, they print the push command and the two `gh pr create` commands for going live; they used to say to push
  `main`.

## v26.11.15

### Added

- **`--lan` for the dev server**: `./dev-server.sh --lan` (or `dev-server.bat --lan`) listens on every network
  interface instead of 127.0.0.1 only, so a phone or another device on the same network can open the local copy. It
  prints the addresses to open, one per IPv4 address of the machine (usually the 192.168.x.x one), and a reminder to
  let Python through the firewall if asked. Without it, the server stays on 127.0.0.1.

## v26.11.10-1

### Changed

- **The status page's icons are StuxieDev's own**: `/favicon.ico`, the phone home-screen icon and the web manifest's
  icons are now the bi-ring avatar with a status jewel, as on every StuxieDev project, instead of GitHup's default
  heartbeat square. They live in `icons/` and `.githup.yml` points GitHup at them with `site.icons`, so they're
  served from status.stuxie.dev itself.

## v26.11.10

### Added

- **Get your own Kat** (kat.stuxie.dev/kat.js, the script other sites load to have the kat) is monitored, beside
  StuxieDev Links, so its card on projects.stuxie.dev can show its live status

## v26.11.08-1

### Changed

- **"Checked regularly", not "every 5 minutes":** GitHub runs the 5-minute schedule best-effort, often far less often,
  so the page's description and the README no longer promise 5 minutes. The status page itself shows the real check
  rhythm it measured (GitHup v26.11.08). The schedule is unchanged

## v26.11.08

### Added

- **The bi kat:** the pixel kat from [kat.stuxie.dev](https://kat.stuxie.dev) follows your pointer around every page,
  as on stuxie.dev and projects.stuxie.dev, and "Your kat" in the footer swaps it for one of the Ridgwell cats (Olly,
  Lily, Poppy or Dougal) or turns it off. It's GitHup's `site.kat` (GitHup v26.11.08), and the generated Privacy and
  Cookies pages say so

## v26.11.06-2

### Added

- **StuxieDev Links** (links.stuxie.dev) is monitored, at the top of the page beside StuxieDev and its media CDN

## v26.11.06-1

### Changed

- The README's "What's monitored" list includes SNAIRK, which was already monitored
- The changelog's intro says the project is on Date Versioning, instead of first saying it follows Semantic Versioning

## v26.11.06

### Changed

- **The status page's logo and favicon are StuxieDev Status's own badge icon** (the StuxieDev avatar with a heartbeat
  badge, as on projects.stuxie.dev) rather than the plain StuxieDev logo, and the README's header matches, now titled
  StuxieDev Status.

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.1.0
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.1.0

### Added

- SNAIRK (snairk.stuxie.dev) is monitored, in the Projects group

## v1.0.3

### Changed

- `max_response_time` raised to 15 seconds (GitHup's new default), so a slow but working site is no longer shown as degraded

## v1.0.2

### Changed

- The Related section no longer monitors RoboStux: it now links to the RoboStux website (robo.st) and RoboStux's own status page (status.robo.st) as plain links, which needs GitHup v1.9.0 or newer

## v1.0.1

### Removed

- The archives.ljdr.uk and archives.ridgwell.network monitors: they're the Ridgwell-branded copies of the Archives, so the StuxieDev status page now checks only archives.stuxie.dev and archives.stuxiedev.com

## v1.0.0

### Added

- status.stuxie.dev, a GitHup status page for StuxieDev, checked every 5 minutes: the StuxieDev website and media CDN, a **Projects** group (projects.stuxie.dev, TIGHC, TS4RLS, TWRAR), a **StuxieDev Archives** group (its four domains) and a **Related** group linking RoboStux's own status page, each group with a combined status
- `.github/workflows/status.yml`: a GitHup `check` every 5 minutes (with `fill-gaps`) with incident Issues, then a build into `_site`, deployed with `actions/deploy-pages` when a status changes, hourly and on pushes; it also keeps the README's status table up to date
- A `legal:` block in `.githup.yml`, so GitHup generates the **Boring Legal Stuff** hub at `/legal/` with its six sub-pages, a themed 404 page, `sitemap.xml`, `robots.txt` and `/sitemap/`
- A live status badge and status table in the README, read from `data/summary.json`
- `dev-server.sh`/`dev-server.bat`, which build the page from generated example data into `.dev/public` and serve it locally with `DEV_MODE` on by default (`--no-dev-mode` to opt out)
- `commit.sh`/`commit.bat` release scripts that read `VERSION.md` and tag `vX.Y.Z`
