# foopkgs

foopkgs is a third-party software repository for Arch Linux.

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

<a href="https://github.com/shkouyo/foopkgs-repo/graphs/contributors">
  <img src="CONTRIBUTORS.svg" alt="Contributors of foopkgs" />
</a>
