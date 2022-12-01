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

## Release Instructions

If you have released a new version of [bob](https://github.com/hashicorp/bob), you will need to update the bob version here to ensure it points to the correct version. An example of this update should look like [this](https://github.com/hashicorp/action-setup-bob/pull/4/files) Once the bob version has been updated, you will need to create a new tag and point it to the major version tag.

**Updating `bob` Version**

1. Checkout to a new branch
2. Update bob version
3. Run `npm run prepare` (you might have to do a `npm install` to wake up npm if you haven't used it in a while)
4. Push your changes, open up a PR, get it approved + merged.

**Create a New Tag**

1. `git checkout main && git pull origin main`
2. `git tag v<new-version-number> && git push origin v<new-version-number>`
3. Push the tag while you're on the `main` branch
4. Depending on which major version the action is on, you will need to delete and update the tag version:

- `git tag -d v1 && git push origin :refs/tags/v1`
- `git tag v1 && git push origin v1` (or whatever main version the action is on)
