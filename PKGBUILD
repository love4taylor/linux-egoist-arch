# Maintainer: Andreas Radke <andyrtr@archlinux.org>

pkgbase=linux-egoist
pkgver=6.6.31
pkgrel=2
pkgdesc='LTS Linux'
url='https://www.kernel.org'
arch=(x86_64)
makedepends=(
  bc
  cpio
  gettext
  libelf
  pahole
  perl
  python
  tar
  xz
)
options=('!strip')
_srcname=linux-$pkgver
_srctag=v$pkgver
_llvmver=18.1.6
source=(
  https://cdn.kernel.org/pub/linux/kernel/v${pkgver%%.*}.x/${_srcname}.tar.{xz,sign}
  https://mirrors.edge.kernel.org/pub/tools/llvm/files/llvm-${_llvmver}-x86_64.tar.{xz,sign}
  0001-ZEN-Add-sysctl-and-CONFIG-to-disallow-unprivileged-C.patch
  0002-skip-simpledrm-if-nvidia-drm.modeset=1-is.patch
  0003-Default-to-maximum-amount-of-ASLR-bits.patch
  config  # the main kernel config file
  0021-netfilter-nat-add-brcm-fullcone-support.patch
  0022-netfilter-nat-add-brcm-fullcone-nft-support.patch
  0023-net-tcp_brutal-make-it-as-a-built-in-kernel-module.patch
  0024-net-tcp_brutal-use-div_u64-to-let-it-build-on-32-bit.patch
  0025-bbrplus.patch
)
validpgpkeys=(
  ABAF11C65A2970B130ABE3C479BE3E4300411886  # Linus Torvalds
  647F28654894E3BD457199BE38DBBDC86092693E  # Greg Kroah-Hartman
  2437CB76E544CB6AB3D9DFD399739260CB6CB716  # Nathan Chancellor
)
# https://www.kernel.org/pub/linux/kernel/v6.x/sha256sums.asc
sha256sums=('d6ecff966f8c95ec4cb3bb303904f757b7de6a6bcfef0d0771cb852158e61c20'
            'SKIP'
            '00c83a3500e6b91155ed37e5ce02b9875ca42d82378499620f0cb1f5497ac0e5'
            'SKIP'
            '21195509fded29d0256abfce947b5a8ce336d0d3e192f3f8ea90bde9dd95a889'
            '2f23be91455e529d16aa2bbf5f2c7fe3d10812749828fc752240c21b2b845849'
            '6400a06e6eb3a24b650bc3b1bba9626622f132697987f718e7ed6a5b8c0317bc'
            'fa8fd6269b55add2f2a93c07cc88f597cd1ae5ac460da9aa5fd2a5422525e819'
            'e32903a97ff3b4626b42201829c5c22229448cf98fdf6f755dc06a8d3958221d'
            '370fe2c70073b79d3e3cb92b166ab1366069a7d5075e0aaf05f893c5862629d0'
            '49586f20e99796d3aa4a689e389b1183f850e2a112859ddc794cd3caea126e53'
            'c68c40721bdff6660647d2d0a7c586f48b18cfd95990c4f8e32770ef8464edb9'
            '54744a7b71269bd8884feb07ad1066abfffb6f749c46e45183236830edb677e8')
b2sums=('521d01b10be736cc7be1108ad0fe9b046aad0ba5af02539d3d0425e424d5c081aaa69446e9f861e5ff4166c0f99201cb827b044d5a70816e4059f53f417c945f'
        'SKIP'
        'a4941becc7b96caebc6141c374a936ae7eca2db0963c692ccf43358df832a071c6ba67cd4d13c4079ada58feaa4e699b9185bfe69f7a2a5f3eea3e2a60877d15'
        'SKIP'
        '02a10396c92ab93124139fc3e37b1d4d8654227556d0d11486390da35dfc401ff5784ad86d0d2aa7eacac12bc451aa2ff138749748c7e24deadd040d5404734c'
        '5dc21a7a6f0b840e6a671dcf09a865e42f0e2c000d5e45d3f3202c02946a8ab2207858d0b2ef1004648b8c2963efb428298b263c8494be806dfc9b6af66d5413'
        'ba6ebe349b3757411364a9ba2deaa30a8d71a247d518c159385977c2b4782771bda4edfc96bd954808617c9ba984d832471b63c11f5bd6003369bfe4051df31f'
        'b4818abc884f9581c5c8a8940cb63142cb5f7fa829a6705ec7c052c2271e3e7450364524c53ef0195e38e1137a2ff285a9eee98526be12de43985d0e09823137'
        '947bd89f5dc4ac9c0dc34fe7d9c4548a36b1107d3afef7be89e6946d2a74f7290624b58f142acf5a38304ea997401b78bc0a1469275e87690a15f06c247eaec8'
        '59b2fa102e40428081f7bf447f03686bac3c3e4af1813bf4d859eb3ed22154a89f04468ca4c274f47cfd6d6f69d3d447736fd459904db4cfd25d2e9cfecf6131'
        '4d05b385dae0c2406ca0dc4b032eecfc2db912f45551ec4a00c04ae0a889689a4a45e24ff7e0cd7a8e2fb8c3197600d1aa77762800eae24fbaa0f3336da124ad'
        '437e724436c1efcc4019f80466cf0c15b1a027cda4482f14b353386b611ef27211a29ac7ad3f5cc3bc8e9461f765bd408744cdc249da38027fff493598fcc220'
        '35015578e22ce7aefd49358beab5dd0851fe2afd79f6a866b15447a4e7248549207a680c8c6ebc523b72ab5b2724a626cfd44a38def5df21e6acc8fb79a6a4ca')

export KBUILD_BUILD_HOST=archlinux
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcname

  echo "Setting version..."
  echo "-$pkgrel" > localversion.10-pkgrel
  echo "${pkgbase#linux}" > localversion.20-pkgname

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
  cp ../config .config
  scripts/config -e TCP_CONG_BRUTAL
  scripts/config -d LTO_NONE \
                 -e LTO \
                 -e LTO_CLANG \
                 -e ARCH_SUPPORTS_LTO_CLANG \
                 -e HAS_LTO_CLANG \
                 -e LTO_CLANG_FULL \
                 -e HAVE_GCC_PLUGINS
  make LLVM=$PWD/../llvm-${_llvmver}-x86_64/bin/ LLVM_IAS=1 olddefconfig
  diff -u ../config .config || :

  make -s kernelrelease > version
  echo "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcname

  make LLVM=$PWD/../llvm-${_llvmver}-x86_64/bin/ LLVM_IAS=1 all
}

_package() {
  pkgdesc="The $pkgdesc kernel and modules"
  license=(
    'Apache-2.0 OR MIT'

    'BSD-2-Clause OR GPL-2.0-or-later'

    BSD-3-Clause
    'BSD-3-Clause OR GPL-2.0-only'
    'BSD-3-Clause OR GPL-2.0-or-later'
    BSD-3-Clause-Clear

    GPL-1.0-or-later
    'GPL-1.0-or-later OR BSD-3-Clause'

    GPL-2.0-only
    'GPL-2.0-only OR Apache-2.0'
    'GPL-2.0-only OR BSD-2-Clause'
    'GPL-2.0-only OR BSD-3-Clause'
    'GPL-2.0-only OR CDDL-1.0'
    'GPL-2.0-only OR Linux-OpenIB'
    'GPL-2.0-only OR MIT'
    'GPL-2.0-only OR MPL-1.1'
    'GPL-2.0-only OR X11'
    'GPL-2.0-only WITH Linux-syscall-note'

    GPL-2.0-or-later
    'GPL-2.0-or-later OR BSD-2-Clause'
    'GPL-2.0-or-later OR BSD-3-Clause'
    'GPL-2.0-or-later OR MIT'
    'GPL-2.0-or-later OR X11'
    'GPL-2.0-or-later WITH GCC-exception-2.0'

    ISC

    LGPL-2.0-or-later
    'LGPL-2.1-only'
    'LGPL-2.1-only OR BSD-2-Clause'

    LGPL-2.1-or-later

    MIT
    MPL-1.1
    X11
    Zlib
  )
  depends=(
    coreutils
    initramfs
    kmod
  )
  optdepends=(
    'wireless-regdb: to set the correct wireless channels of your country'
    'linux-firmware: firmware images needed for some devices'
  )
  provides=(
    KSMBD-MODULE
    VIRTUALBOX-GUEST-MODULES
    WIREGUARD-MODULE
  )
  replaces=(
    wireguard-lts
  )

  cd $_srcname
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

  # licenses
  install -vDm 644 LICENSES/deprecated/{GPL-1.0,ISC,Linux-OpenIB,X11,Zlib} -t "$pkgdir/usr/share/licenses/$pkgname/"
  install -vDm 644 LICENSES/preferred/{BSD,MIT}* -t "$pkgdir/usr/share/licenses/$pkgname/"
  install -vDm 644 LICENSES/exceptions/* -t "$pkgdir/usr/share/licenses/$pkgname/"
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the $pkgdesc kernel"
  license=(
    BSD-3-Clause
    'BSD-3-Clause OR GPL-2.0-only'

    GPL-1.0-or-later
    'GPL-1.0-or-later WITH Linux-syscall-note'

    GPL-2.0-only
    'GPL-2.0-only OR Apache-2.0'
    'GPL-2.0-only OR BSD-2-Clause'
    'GPL-2.0-only OR BSD-3-Clause'
    'GPL-2.0-only OR CDDL-1.0'
    'GPL-2.0-only OR Linux-OpenIB'
    'GPL-2.0-only OR Linux-OpenIB OR BSD-2-Clause'
    'GPL-2.0-only OR MIT'
    'GPL-2.0-only OR MPL-1.1'
    'GPL-2.0-only OR X11'
    'GPL-2.0-only WITH Linux-syscall-note'
    '(GPL-2.0-only WITH Linux-syscall-note) AND MIT'
    '(GPL-2.0-only WITH Linux-syscall-note) OR BSD-2-Clause'
    '(GPL-2.0-only WITH Linux-syscall-note) OR BSD-3-Clause'
    '(GPL-2.0-only WITH Linux-syscall-note) OR CDDL-1.0'
    '(GPL-2.0-only WITH Linux-syscall-note) OR Linux-OpenIB'
    '(GPL-2.0-only WITH Linux-syscall-note) OR MIT'

    GPL-2.0-or-later
    'GPL-2.0-or-later OR BSD-2-Clause'
    'GPL-2.0-or-later OR BSD-3-Clause'
    'GPL-2.0-or-later OR MIT'
    'GPL-2.0-or-later WITH Linux-syscall-note'
    '(GPL-2.0-or-later WITH Linux-syscall-note) OR BSD-3-Clause'
    '(GPL-2.0-or-later WITH Linux-syscall-note) OR MIT'
    'LGPL-2.0-or-later OR BSD-2-Clause'
    'LGPL-2.0-or-later WITH Linux-syscall-note'

    ISC

    'LGPL-2.0-or-later WITH Linux-syscall-note'
    'LGPL-2.0-or-later OR BSD-2-Clause'

    LGPL-2.1-only
    'LGPL-2.1-only OR BSD-2-Clause'
    'LGPL-2.1-only OR MIT'
    'LGPL-2.1-only WITH Linux-syscall-note'

    LGPL-2.1-or-later
    'LGPL-2.1-or-later OR BSD-2-Clause'
    'LGPL-2.1-or-later WITH Linux-syscall-note'

    MIT
    Zlib
  )
  depends=(pahole)

  cd $_srcname
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts

  # required when STACK_VALIDATION is enabled
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # required when DEBUG_INFO_BTF_MODULES is enabled
  install -Dt "$builddir/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

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

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
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
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"

  # licenses
  install -vDm 644 LICENSES/deprecated/{ISC,Linux-OpenIB,X11,Zlib} -t "$pkgdir/usr/share/licenses/$pkgname/"
  install -vDm 644 LICENSES/preferred/{BSD*,MIT} -t "$pkgdir/usr/share/licenses/$pkgname/"
  install -vDm 644 LICENSES/exceptions/* -t "$pkgdir/usr/share/licenses/$pkgname/"
}

pkgname=(
  "$pkgbase"
  "$pkgbase-headers"
)
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
