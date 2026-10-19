<!--
  Template repository for an ARGVUS Arch Linux package.

  Before using this template, replace the placeholders and the example payload:
  <OWNER>, <REPO>, <PKGNAME>, <PKGDESC>, the maintainer, and the license.
  Keep the local and CI PKGBUILDs aligned; their source definitions are the
  only intentional difference.
-->

# <PKGNAME>

<PKGDESC>

[![CI](https://github.com/<OWNER>/<REPO>/actions/workflows/ci.yml/badge.svg)](https://github.com/<OWNER>/<REPO>/actions/workflows/ci.yml)
[![Release](https://github.com/<OWNER>/<REPO>/actions/workflows/release.yml/badge.svg)](https://github.com/<OWNER>/<REPO>/actions/workflows/release.yml)
[![License](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)

This repository is a starting point for an Arch Linux package. Replace the
`src/` example with the files owned by the package and update both PKGBUILDs,
the workflows, metadata, and documentation before publishing it.

## Build and install

On Arch Linux or a compatible distribution:

```sh
sudo pacman -S --needed base-devel git shellcheck
make validate
make build
make install
```

`make build` creates a deterministic local source archive in
`build/artifacts/` and a package in `build/dist/`. `make install` requires
`sudo` and installs the one package found in that directory without a blanket
`--overwrite` rule.

For package metadata only:

```sh
make validate
makepkg -p packaging/arch/ci/PKGBUILD --printsrcinfo
```

See [packaging/arch/README.md](packaging/arch/README.md) for the difference
between local and release builds.

## Desktop package model

`argvus` is the master package of the ARGVUS desktop. A component package depends on
`argvus`, so installing it pulls in the desktop and no install order is required.
Runtime tools that belong to the desktop are subcommands of `argvus` (for example
`argvus config` and `argvus i18n`), not separate executables.

## Documentation

- [DEVELOPMENT.md](DEVELOPMENT.md) — layout, checks, and releases
- [CONTRIBUTING.md](CONTRIBUTING.md) — contribution workflow
- [SECURITY.md](SECURITY.md) — private vulnerability reports

## License

SPDX: `GPL-3.0-only`. See [LICENSE](LICENSE).
