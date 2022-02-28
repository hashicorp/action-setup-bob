# action-setup-bob
GitHub action to setup `bob` CLI. This action can be run on `ubuntu-latest` and `macos-latest` GitHub Actions runners, and will install and expose a specified version of the `bob` CLI on the runner environment.

The pattern for this action copied from `https://github.com/hashicorp/setup-hc-releases` as it has reliable tests and error handling patterns.

## Usage

Setup the `bob` CLI:

```yaml
steps:
- uses: hashicorp/action-setup-bob@v1
  with:
    github-token:
      ${{ secrets.GITHUB_TOKEN }}
```

A specific version of the `bob` CLI can be installed:

```yaml
steps:
- uses: hashicorp/action-setup-bob@v1
  with:
    github-token:
      ${{ secrets.GITHUB_TOKEN }}
    version:
      0.0.19
```

## Inputs
The actions supports the following inputs:

- `github-token`: The GitHub token secret to use with permissions to download `bob` CLI
- `version`: The version of `bob` to install, defaulting to `0.0.19`
