# Contributing to foopkgs

Thank you for considering contributing to foopkgs. This document explains how the repository is organized, how packages are added, and how commits should be written.

## Repository structure and workflow

The repository is organized into one branch per package. Each package branch holds a `PKGBUILD` together with any files the build requires, while the `main` branch carries the repository documentation and its automation.

Packages are built and published automatically by [Varve](https://varve.0x0f.dev/). Varve watches the package branches, builds them, and publishes the resulting artifacts to the repository servers, so nothing has to be run manually after a branch is pushed.

## The .varve.toml file

Every package branch must contain a `.varve.toml` file, which tells Varve how to handle the package. The annotated example below covers every available option:

```toml
# Build notifications are delivered to the listed maintainers,
# so every entry must carry a working email address.
[[maintainers]]
name = "Alice"
email = "alice@example.org"

[[maintainers]]
name = "Bob"
email = "bob@example.org"

# How the package's version control state is treated.
# "auto" infers the mode from the package name suffix (-git, -svn);
# "none" marks a non-VCS package; "git" and "svn" force the mode.
vcs = "auto"

# Pull the PKGBUILD from an external git repository instead of keeping
# it in the branch. Review the PKGBUILD for safety before enabling this,
# and prefer non-AUR sources. With this section active, the branch may
# contain nothing but this file.
#[pkgbuild_source]
#url = "https://git.example.org/foo/bar.git"
#branch = "master"
#directory = "packages/foo"

# Artifacts whose names match these glob patterns are dropped from the
# repository, e.g. debug packages.
[collect]
exclude = ["*-debug*"]

# Lifecycle scripts invoked around the build:
# pre_build runs before makepkg starts; post_build runs after makepkg
# finishes but before artifacts are collected; on_success runs after a
# successful build; on_failure runs after a failed build, while the
# container still retains the working directory.
#[hooks]
#pre_build = ["scripts/prepare.sh"]
#post_build = ["scripts/strip-debug.sh"]
#on_success = ["scripts/notify.sh"]
#on_failure = ["scripts/collect-log.sh"]

# Upload the built package to AUR. Keep submit disabled unless the
# package is absent from AUR or the AUR account "ShinKouyo" holds
# Maintainer or Co-Maintainer rights on it.
[aur]
name = "package-base"
submit = false
```

## Adding a new package

To add a package, create a branch named after the package, place the `PKGBUILD` and any files the build needs in it, and add a `.varve.toml` file as described above. Once the branch is pushed, Varve takes care of the rest.

The following conventions apply:

- Annotate licenses with [SPDX license identifiers](https://rfc.archlinux.page/0016-spdx-license-identifiers/).
- Make the repository [REUSE compliant](https://rfc.archlinux.page/0052-reuse/).
- Follow [RFC 0040 on licensing package sources](https://rfc.archlinux.page/0040-license-package-sources/).
- Write the `PKGBUILD` according to the [PKGBUILD documentation](https://wiki.archlinux.org/title/PKGBUILD).
- Follow the [Arch package guidelines](https://wiki.archlinux.org/title/Arch_package_guidelines).
- Consult the [guide to creating packages](https://wiki.archlinux.org/title/Creating_packages).
- Follow the [AUR submission guidelines](https://wiki.archlinux.org/title/AUR_submission_guidelines#Rules_of_submission).
- Respect [RFC 0032 on Arch Linux ports](https://rfc.archlinux.page/0032-arch-linux-ports/) for architecture support.

## Commit messages

Commit messages should follow the guidance in [On commit messages for Arch Linux package packaging](https://0x0f.dev/posts/arch-package-commit-message/), which describes the expected format and suitable commit types. Consistent commit messages keep the history of the package branches uniform and easy to read.

