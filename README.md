# homebrew-tap

Homebrew tap for [IRIS](https://github.com/Urdemonlord/irisproject) — a self-hosted mail stack (IRIS webmail + Stalwart + Caddy) for macOS.

## Install

```sh
brew tap Urdemonlord/tap
brew install Urdemonlord/tap/iris-mail-stack
```

Then finish the setup as root (creates the `iris` user, `/etc/iris`, `/etc/stalwart`, `/etc/caddy` and the launchd services):

```sh
sudo IRIS_DOMAIN=example.com $(brew --prefix)/lib/iris/iris-install-macos.sh
```

See the formula caveats (`brew info iris-mail-stack`) for the full notes.

## Formulae

| Formula | Version | Description |
| --- | --- | --- |
| `iris-mail-stack` | 0.4.1 | Self-hosted mail stack: IRIS webmail + Stalwart + Caddy, one install |

## Updating for a new IRIS release

The formula source of truth lives in irisproject at `packaging/homebrew/iris-mail-stack.rb`. This tap ships the release copy verbatim. When a new IRIS release ships, copy the updated formula here and update the version and both `sha256` values together — download each macOS tarball from the GitHub release and run `shasum -a 256 <tarball>`; never guess the hashes.

## Notes

- Requires macOS Sonoma (14) or later. Apple Silicon and Intel builds both come from the IRIS GitHub release.
- `brew install` only places files in the Cellar. The system setup still needs the sudo step above.
- On Apple Silicon the setup script needs a PREFIX adapter first; see `packaging/homebrew/README.md` in the IRIS repo.
- Every push and pull request runs `brew test-bot` (audit, install, test) on macOS runners via `.github/workflows/tests.yml`.
