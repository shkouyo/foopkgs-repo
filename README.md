# foopkgs

foopkgs is a third-party software repository for Arch Linux on x86_64.

## Setup

First, fetch and locally sign the repository's signing key. It is published under the name `foopkgs <i+foopkgs@0x0f.dev>` with the fingerprint `E3EC87D0E940E9670EB0F1B3D3217A21C16802E8`:

```sh
sudo pacman-key --recv-key D3217A21C16802E8 --keyserver keys.openpgp.org
sudo pacman-key --lsign-key D3217A21C16802E8
```

Then add the repository to `/etc/pacman.conf`:

```ini
[foopkgs]
SigLevel = Required
Server = https://repo.ilovecandy.top/$arch
Server = https://dl.ilovecandy.top/$arch
```

Finally, refresh your package databases and update your system:

```sh
sudo pacman -Syu
```

## Building

The repository is built and published automatically by [Varve](https://git.0x0f.dev/shkouyo/varve). Build progress can be followed live on [the build status page](https://varve.0x0f.dev/), while [the package index](https://varve.0x0f.dev/packages) lists every available package.

## Contributing

foopkgs was created by [ShinKouyo](https://0x0f.dev) and is maintained by:

- ShinKouyo \<<i@0x0f.dev>\>

We are grateful to all contributors. If you would like to contribute, please read the guidelines in [CONTRIBUTING.md](CONTRIBUTING.md).

You can request a new package by opening an [Issue](https://github.com/shkouyo/foopkgs-repo/issues/new?template=10-new-package.yml), or feel free to submit a [Pull request](https://github.com/shkouyo/foopkgs-repo/compare). The software you submit should be free ([as in freedom](https://www.gnu.org/philosophy/free-sw)) software, or at least [open source](https://opensource.org/osd) software.

![Contributors of foopkgs](CONTRIBUTORS.svg)

## License

Copyright (C) foopkgs contributors

Files in the `main` branch that are not marked with an `SPDX-License-Identifier` header or any other explicit notice are licensed under the Apache License 2.0, whose full text is available in [COPYING.Apache-2.0](COPYING.Apache-2.0).

Files in the package branches that carry neither an `SPDX-License-Identifier` header nor a `REUSE.toml` annotation are likewise licensed under the BSD Zero Clause License, whose full text is to be added in [COPYING.0BSD](COPYING.0BSD).

All files are provided WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
