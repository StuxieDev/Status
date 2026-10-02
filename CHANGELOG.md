# Changelog

All notable changes to StuxieDev's status page (status.stuxie.dev) are documented here. It
follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
