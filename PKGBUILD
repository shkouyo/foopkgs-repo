# Maintainer: ShinKouyo <i@0x0f.dev>

# SPDX-FileCopyrightText: Arch Linux contributors
# SPDX-License-Identifier: 0BSD

# shellcheck shell=bash
# shellcheck disable=SC2034,SC2154

# shellcheck disable=SC2155

pkgbase=linux-sk
pkgver=6.18.44.sk1
pkgrel=2
pkgdesc='Linux-sk'
url='https://github.com/shkouyo/foopkgs-repo/tree/linux-sk'
arch=(
  x86_64
)
license=(GPL-2.0-only)
makedepends=(
  bc
  binutils
  clang
  cpio
  gettext
  glibc
  libelf
  libgcc
  lld
  llvm
  openssl
  pahole
  perl
  python
  rust
  rust-bindgen
  rust-src
  tar
  xxhash
  xz
  zlib
  zstd
)
options=(
  !debug
  !strip
)
_srcname=linux-${pkgver%.*}
source=(
  "https://linux-libre.fsfla.org/pub/linux-libre/releases/${pkgver%.*}-gnu/linux-libre-${pkgver%.*}-gnu.tar.xz"

  # patches from Arch Linux
  # https://gitlab.archlinux.org/archlinux/packaging/packages/linux-lts
  '0001-add-sysctl-to-allow-disabling-unprivileged-CLONE_NEW.patch'
  '0002-drm-amdgpu-avoid-memory-allocation-in-the-critical-c.patch'
  '0003-drm-amdgpu-use-GFP_ATOMIC-instead-of-NOWAIT-in-the-c.patch'

  # http://www.coreboot.org/EHCI_Gadget_Debug
  '0001-usb-serial-gadget-no-TTY-hangup-on-USB-disconnect-WI.patch'
  # https://labs.parabola.nu/issues/877
  # http://www.fsfla.org/pipermail/linux-libre/2015-November/003202.html
  '0002-fix-Atmel-maXTouch-touchscreen-support.patch'

  # cjktty patches
  '0001-cjktty-6.18.44.patch'
  'https://github.com/bigshans/cjktty-patches/raw/b43d618da6d6536338761a5fc7c9c377c318fb9e/cjktty-add-cjk32x32-font-data.patch'

  # BBRv3 patch, modified from pf-kernel
  '0002-bbr3-6.18.44.patch'

  # patches from CachyOS
  'https://github.com/CachyOS/kernel-patches/raw/4015bbcac0d77539d867f069d777b223dcb21a33/6.18/misc/0001-acpi-call.patch'
  '0001-bore-6.18.44.patch' # modified
  'https://github.com/CachyOS/kernel-patches/raw/4015bbcac0d77539d867f069d777b223dcb21a33/6.18/misc/0001-clang-polly.patch'

  # kernel config from linux-lts
  'https://gitlab.archlinux.org/archlinux/packaging/packages/linux-lts/-/raw/6.18.44-1/config.x86_64'
)
b2sums=(
  '6ab60cd87e12272ca9c8205242a7ca2e54b3772d22d5c9a348da369ea38d1a35244f8c187201b5067372f63f86964c1129df7220366c062fd016c9217f6caafe'
  'f98f4a2e714f7c9e05740caaad2bf014065ec950c096df74a3dee8b2ce6549f034adf6f87a76168f513aa68eb738edbdb6fe1a3f1b3a5104201c65199b5b931e' # 0001-add-sysctl-to-allow-disabling-unprivileged-CLONE_NEW.patch
  '6ca246df80fa85f9c21d090f87ee31e33acb02f3c1147944750e0896ebf199bc0cf427a164dacbdd9baa26dbdbce2fabd89ebdb6a8ce5dae83fc455b27a56cc8' # 0002-drm-amdgpu-avoid-memory-allocation-in-the-critical-c.patch
  'a612d5ea58485eeaa5cce0b30074ab3188f4321c4759448780de2f3f656821356d640df433e31bd4e8f2c9719c8e275374ddea29b9504335ed0981be5ac7bf7b' # 0003-drm-amdgpu-use-GFP_ATOMIC-instead-of-NOWAIT-in-the-c.patch
  'c2214154c36900e311531bfe68184f31639f5c50fed23bc3803a7f18439b7ff258552a39f02fed0ea92f10744e17a6c55cef0ef1a98187f978fe480fb3dddc14' # 0001-usb-serial-gadget-no-TTY-hangup-on-USB-disconnect-WI.patch
  '0c7ceba7cd90087db3296610a07886f337910bad265a32c052d3a703e6eb8e53f355ab9948d72d366408d968d8ee7435084dd89bef5ed0b69355fd884c2cd468' # 0002-fix-Atmel-maXTouch-touchscreen-support.patch
  '6f30d1a5ea1493d8d76141ba21c63fb5d9a904c9202247e87e4bd8c7509a52fa3b660aeadafd1af17e9a7da4b7191377cce856c1dda985123f2464328dd7dd3d' # 0001-cjktty-6.18.44.patch
  '101996793aeede5e456b23b35c2fd4af5c38fd363473dcdda0bce6e21d110a9f88a67e325b1ebf8efef4a7511f135c4f64ff1fc54b8ef925a5df8d6292ba7678' # cjktty-add-cjk32x32-font-data.patch
  '7db56e45022bed8b34c17d5e476fbfc0d13b6ffa9ae35e2c338a4fac91e9e764ace4ec3a263eb0ad80c8ae34b9bf57f618cf61bf2d14996dcf0d7c320f9620c7' # 0002-bbr3-6.18.44.patch
  'be844475f453f79f5d892c2cc2a6843b32501e2a7c57dd0859ec0cba2262d9fa9a95fff77b6e3718dff449c0f3b428fce03bc35d8332081427feedd461388498' # 0001-acpi-call.patch
  '41094d016e9962058c5cd11f01784219eb7d4ca04f674c0088348a6d76885bcad2a81b374eb724d8217f37d8818f8d8bca1d75075fa9827af81f9598eaa7ecc4' # 0001-bore-6.18.44.patch
  'db6e3815cc7fc09e89ff034f33526f4bc03cd4b4720ff6d50f02fc2cdbca6314b37ba2e2d1098436018f373b62289f82b20500e9c2a7d801f7a2a27f9f0b73d8' # 0001-clang-polly.patch
  'a4891a11e75dc7a1f4fd81390da18822c09d8bdb45b5ffe42c145db035503529e7b5d25e03e69bd248377b77d4802a9861cc3bcc0103ba31da7b10d48ccbc51e' # config.x86_64
)

export KBUILD_BUILD_HOST=foopkgs
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

export CC=clang
export LD=ld.lld
export LLVM=1
export LLVM_IAS=1
export AR=llvm-ar
export NM=llvm-nm
export OBJCOPY=llvm-objcopy
export OBJDUMP=llvm-objdump
export READELF=llvm-readelf
export STRIP=llvm-strip

# https://gitlab.archlinux.org/archlinux/packaging/packages/linux/-/merge_requests/15
RUSTFLAGS+=' -C debuginfo=2'
RUSTFLAGS+=' -C strip=none'
RUSTFLAGS+=' -C lto=fat'
RUSTFLAGS+=' -C codegen-units=1'
RUSTFLAGS+=' -C opt-level=3'
RUSTFLAGS+=' -C embed-bitcode=yes'
export CARGO_PROFILE_RELEASE_DEBUG=2
export CARGO_PROFILE_RELEASE_STRIP=false
export CARGO_HOME="$srcdir"
export CARGO_PROFILE_RELEASE_LTO=true
export CARGO_PROFILE_RELEASE_CODEGEN_UNITS=1
export CARGO_PROFILE_RELEASE_OPT_LEVEL=3

prepare() {
  cd "$_srcname" || exit 1

  echo "Setting version..."
  echo "-$pkgrel" > localversion.10-pkgrel
  echo "${pkgbase#linux-sk}" > localversion.20-pkgname

  # add extraversion as localversion
  echo "-${pkgver##*.}" > localversion.00-extraversion
  sed -i '/^EXTRAVERSION[[:space:]]*=/ s/=.*$/=/' Makefile

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    src="${src%.zst}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  echo "Setting config..."
  cp ../config."$CARCH" .config

  # custom kernel config
  echo "Setting kernel config..."
  scripts/config --keep-case --enable FONT_CJK_16x16
  scripts/config --keep-case --enable FONT_CJK_32x32
  scripts/config --module TCP_CONG_CUBIC
  scripts/config --enable TCP_CONG_BBR
  scripts/config --enable DEFAULT_BBR
  scripts/config --module ACPI_CALL
  scripts/config --enable SCHED_BORE
  scripts/config --enable POLLY_CLANG
  scripts/config --disable LTO_NONE
  scripts/config --enable LTO_CLANG_THIN

  make olddefconfig
  diff -u ../config."$CARCH" .config || :

  make -s kernelrelease > version
  echo "Prepared $pkgbase version $(<version)"
}

build() {
  cd "$_srcname" || exit 1

  make -j"$(nproc)" all
  make -C tools/bpf/bpftool vmlinux.h feature-clang-bpf-co-re=1
}

_package() {
  pkgdesc="The $pkgdesc kernel and modules"
  depends=(
    coreutils
    initramfs
    kmod
  )
  optdepends=(
    "$pkgbase-headers: headers and scripts for building modules"
    'linux-libre-firmware: firmware images needed for some devices'
    'scx-scheds: to use sched-ext schedulers'
    'wireless-regdb: to set the correct wireless channels of your country'
  )
  provides=(
    KSMBD-MODULE
    NTSYNC-MODULE
    VIRTUALBOX-GUEST-MODULES
    WIREGUARD-MODULE
  )

  cd "$_srcname" || exit 1
  local modulesdir="$pkgdir/usr/lib/modules/$(<version)"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"

  echo "Installing modules..."
  ZSTD_CLEVEL=19 make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 \
    DEPMOD=/doesnt/exist modules_install  # Suppress depmod

  # remove build link
  rm "$modulesdir"/build
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the $pkgdesc kernel"
  depends=(
    binutils
    glibc
    libelf
    libgcc
    openssl
    pahole
    xxhash
    zlib
    zstd
  )
  provides=(LINUX-HEADERS)

  cd "$_srcname" || exit 1
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  local karch
  case $CARCH in
    x86_64) karch=x86 ;;
    *) echo "Unknown CARCH $CARCH"; exit 1 ;;
  esac

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux tools/bpf/bpftool/vmlinux.h
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/$karch" -m644 arch/$karch/Makefile
  cp -t "$builddir" -a scripts
  ln -srt "$builddir" "$builddir/scripts/gdb/vmlinux-gdb.py"

  if [[ $(scripts/config -s CONFIG_HAVE_STACK_VALIDATION) = y ]]; then
    install -Dt "$builddir/tools/objtool" tools/objtool/objtool
  fi

  if [[ $(scripts/config -s CONFIG_DEBUG_INFO_BTF_MODULES) = y ]]; then
    install -Dt "$builddir/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids
  fi

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/$karch" -a arch/$karch/include
  install -Dt "$builddir/arch/$karch/kernel" -m644 arch/$karch/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "$builddir/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  if [[ $(scripts/config -s CONFIG_RUST) = y ]]; then
    echo "Installing Rust files..."
    install -Dt "$builddir/rust" -m644 rust/*.rmeta
    install -Dt "$builddir/rust" rust/*.so
  fi

  echo "Installing unstripped VDSO..."
  make INSTALL_MOD_PATH="$pkgdir/usr" vdso_install \
    link=  # Suppress build-id symlinks

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */$karch/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -Sib "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v "$STRIP_SHARED" "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v "$STRIP_STATIC" "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v "$STRIP_BINARIES" "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v "$STRIP_SHARED" "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v "$STRIP_STATIC" "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}


pkgname=(
  "$pkgbase"
  "$pkgbase-headers"
)
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#"$pkgbase"}")
    _package${_p#"$pkgbase"}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
