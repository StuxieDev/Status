<p align="center">
  <img src="https://global.media.stuxie.dev/logo.png" height="80" alt="StuxieDev Logo">
</p>

# Contributing to Status

Status is StuxieDev's status page, [status.stuxie.dev](https://status.stuxie.dev), built with
[GitHup](https://githup.stux.group). To report an outage, open an Issue. Bugs or ideas for the
status page software belong in [StuxGroup/GitHup](https://github.com/StuxGroup/GitHup/issues).

## Local setup

You need Python 3.11+ and nothing else.

```bash
./dev-server.sh [--no-dev-mode] [--lan] [port]   # or dev-server.bat on Windows
```

Pass `--lan` to open it on a phone or another device on your local network: the server then listens on every interface
instead of 127.0.0.1 only, and prints the addresses to open (usually the 192.168.x.x one; allow Python through the
firewall if asked).

## Project conventions

- **Monitors live in `.githup.yml`.** Its syntax is documented in the
  [GitHup docs](https://githup.stux.group/docs/). Only add sites StuxieDev runs.
- **The status page itself is GitHup's**, including the legal pages and 404. Change how it
  looks or works in GitHup, not here.
- **Brand.** The StuxieDev accent is `#9b4f96`, set as `site.accent`.
- **Legal pages.** The `legal:` block in `.githup.yml` drives **Boring Legal Stuff** at `/legal/`.
  Keep it accurate.
- **Don't edit `data/` by hand.** It belongs to GitHup and the workflow.

## Branches and going live

- **`main` is what's live.** status.stuxie.dev is built from it. Changes to the page only reach it through a pull
  request from `staging`; the one exception is the GitHup workflow, which commits its monitoring data straight to
  `main` every few minutes.
- **`staging` is the last check before live.** Nothing is pushed to it directly either: it only changes when a pull
  request from `test` is merged.
- **Work happens on `test`**, or on a branch off `test` that's merged back into it. CI runs on every push and on every
  pull request. Releases are made on `test` too: `commit.sh` / `commit.bat` refuse to run on `staging` or `main`.
- **Going live:** push `test` with its tag, open a pull request into staging (`gh pr create --base staging --head
  test`), check staging once it's merged, then open one from staging into main (`gh pr create --base main --head
  staging`). The commit script prints these commands after tagging.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh`.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.
5. `git push origin test --tags`, then open a pull request from `test` into `staging`, and once staging is checked one
   from `staging` into `main` (see Branches and going live).
