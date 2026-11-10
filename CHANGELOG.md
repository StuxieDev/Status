# Changelog

All notable changes to StuxieDev's status page (status.stuxie.dev) are documented here. Since
v26.10.23 this project uses [Date Versioning](https://datevers.ing) (`YY.MM.DD`, the UTC release date, with `-1`, `-2`…
for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
