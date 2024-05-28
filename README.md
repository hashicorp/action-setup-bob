# action-setup-bob [![Heimdall](https://heimdall.hashicorp.services/api/v1/assets/action-setup-bob/badge.svg?key=53a349ec7ff1ff896dfb0889f8410527df8156e287294445dcc504e1c55e88bb)](https://heimdall.hashicorp.services/site/assets/action-setup-bob) [![CI](https://github.com/hashicorp/action-setup-bob/actions/workflows/ci.yml/badge.svg)](https://github.com/hashicorp/action-setup-bob/actions/workflows/ci.yml)

_For internal HashiCorp use only. The output of this action is specifically
designed to satisfy the needs of our internal deployment system, and may not be
useful to other organizations._

GitHub action to setup `bob` CLI. This action can be run on `ubuntu-latest` and `macos-latest` GitHub Actions runners, and will install and expose a specified version of the `bob` CLI on the runner environment.

## Usage

Setup the `bob` CLI:

```yaml
steps:
- uses: hashicorp/action-setup-bob@v2
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
```

A specific version of the `bob` CLI can be installed:

```yaml
steps:
- uses: hashicorp/action-setup-bob@v2
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    tag: v0.2.0
```

## Inputs
The actions supports the following inputs:

- `github-token`: The GitHub token secret to use with permissions to download `bob` CLI
- `tag`: The tag of the release of `bob` to install, defaulting to latest

## Release Instructions

After your PR is merged to the default branch, `main`:
1. Update locally: `git checkout main && git pull origin main`
1. Create a new tag for the release, e.g. `v2.0.1` with `git tag v2.0.1 && git push origin v2.0.1`.
1. Update the major version tag locally, e.g. `git tag -d v2 && git tag v2`
1. Update the major version tag upstream, e.g. `git push origin :refs/tags/v2 && git push origin v2`
