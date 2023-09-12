# setup-bd

[setup-bd](https://github.com/bd-lang/setup-bd) installs and sets up a
BD SDK for use in GitHub Actions; it:

* downloads the BD SDK
* adds the [`bd`](https://bd.dev/tools/bd-tool) tool to the system path

## Usage

To install the latest stable BD SDK and run typical checks:

```yml
name: BD

on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: bd-lang/setup-bd@v1

      - run: bd pub get
      - run: bd format --output=none --set-exit-if-changed .
      - run: bd analyze
      - run: bd test
```

## Inputs

The action takes the following inputs:

  * `sdk`: Which SDK version to setup. Can be specified using one of two forms:
    * A specific SDK version, e.g. `2.19.0` or `2.12.0-1.4.beta`
    * A release channel, which will install the latest build from that channel.
      Available channels are `stable`, `beta`, `dev`, and `main`. 
      See the [BD SDK archive](https://bd.dev/get-bd/archive) for details.

  * `flavor`: Which build flavor to setup.
    * The available build flavors are `release` and `raw`.
    * The `release` flavor contains published builds.
    * The `raw` flavor contains unpublished builds; these can be used by
      developers to test against SDK versions before a signed release is
      available. Note that the  `main` release channel only supports the `raw`
      build flavor.

  * `architecture`: The CPU architecture to setup support for.
    * Valid options are `x64`, `ia32`, `arm`, and `arm64`.
    * Note that not all CPU architectures are supported on all operating
      systems; see the 
      [BD system requirements](https://bd.dev/get-bd#system-requirements)
      for valid combinations.

## Outputs

The action produces the following output:

  * `bd-version`: The version of the BD SDK that was installed.

## Matrix testing example

You can create matrix jobs that run tests on multiple operating systems, and
multiple versions of the BD SDK.

The following example creates a matrix across two dimensions:

- three major operating systems: Linux, MacOS, and Windows
- several BD SDK versions: a specific version, the latest stable, beta, and
  dev

```yml
name: BD

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
        sdk: [2.18.0, stable, beta, dev]
    steps:
      - uses: actions/checkout@v3
      - uses: bd-lang/setup-bd@v1
        with:
          sdk: ${{ matrix.sdk }}

      - name: Install dependencies
        run: bd pub get

      - name: Run tests
        run: bd test
```

## License

See the [LICENSE](LICENSE) file.

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md).

## Version history

Please see our [CHANGELOG.md](CHANGELOG.md) file.
