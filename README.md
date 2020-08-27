# woke-action-reviewdog

[![Test](https://github.com/caitlinelfring/woke-action-reviewdog/workflows/Test/badge.svg)](https://github.com/caitlinelfring/woke-action-reviewdog/actions?query=workflow%3ATest)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/caitlinelfring/woke-action-reviewdog?logo=github&sort=semver)](https://github.com/caitlinelfring/woke-action-reviewdog/releases)

Woke GitHub Actions allow you to execute [`woke`](https://github.com/caitlinelfring/woke) command within GitHub Actions.

This GitHub action uses [reviewdog](https://github.com/reviewdog/reviewdog)

This is a GitHub action for [`woke`] repository for [reviewdog](https://github.com/reviewdog/reviewdog) action with release automation.
Click `Use this template` button to create your reviewdog action :dog:!

## Inputs

Inputs to configure the `woke` GitHub Actions.

| Input            | Default               | Description                                                                                       |
|------------------|-----------------------|---------------------------------------------------------------------------------------------------|
| `args`           | `.`                   | (Optional) Additional flags to run woke with (see <https://github.com/caitlinelfring/woke#usage>) |
| `fail-on-error`  | `false`               | (Optional) Fail the GitHub Actions check for any failures.                                        |
| `workdir`        | `.`                   | (Optional) Run `woke` this working directory relative to the root directory.                      |
| `version`        | latest                | (Optional) Release version of `woke` (defaults to latest version)                                 |
| `github_token`   | `${{ github.token }}` | (Optional) Custom GitHub Access token (ie `${{ secrets.MY_CUSTOM_TOKEN }}`).                      |

## Usage

```yaml
name: woke
on: [pull_request]
jobs:
  linter_name:
    name: runner / woke
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: caitlinelfring/woke-action-reviewdog@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          # Change reviewdog reporter if you need [github-pr-check,github-check,github-pr-review].
          reporter: github-pr-review
          # Change reporter level if you need.
          # GitHub Status Check won't become failure with warning.
          level: warning
```

## License

This application is licensed under the MIT License, you may obtain a copy of it
[here](https://github.com/caitlinelfring/woke-action-reviewdog/blob/main/LICENSE).
