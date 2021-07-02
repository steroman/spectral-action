# Spectral Linter Action

This action uses [Spectral](https://github.com/stoplightio/spectral) from [Stoplight](https://stoplight.io/) to lint your OpenAPI documents, or any other JSON/YAML files.

![](./image.png)

## Usage

See [action.yml](action.yml)

```yaml
name: Run Spectral on Pull Requests

on:
  - pull_request

jobs:
  build:
    name: Run Spectral
    runs-on: ubuntu-latest
    steps:
      # Check out the repository
      - uses: actions/checkout@v2

      # Run Spectral
      - uses: stoplightio/spectral-action@v0.7.3
        with:
          file_glob: 'doc/api/*.yaml'
          spectral_ruleset: 'doc/api/custom.spectral.yaml'
```

### Inputs

- **file_glob:** Pattern describing the set of files to lint. Defaults to `*.oas.{json,yml,yaml}`. (_Note:_ Pattern syntax is documented in the [fast-glob](https://www.npmjs.com/package/fast-glob) package documentation)
- **spectral_ruleset:** Optional custom ruleset to load in Spectral. The file must end in `.spectral.yml`. When not defined, the default Spectral ruleset will be loaded.

## Configuration

Spectral Action will respect your [Spectral Rulesets](https://stoplight.io/p/docs/gh/stoplightio/spectral/docs/getting-started/rulesets.md), which can be defined, extended, and overriden by placing `.spectral.yml` in the root of your repository.
