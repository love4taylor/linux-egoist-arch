# Maintainer: Andreas Radke <andyrtr@archlinux.org>

pkgbase=linux-egoist
pkgver=6.6.31
pkgrel=3
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
  0020-netfilter-add-xt_FLOWOFFLOAD-target.patch
  0021-netfilter-nat-add-brcm-fullcone-support.patch
  0022-netfilter-nat-add-brcm-fullcone-nft-support.patch
  0023-net-tcp_brutal-make-it-as-a-built-in-kernel-module.patch
  0024-net-tcp_brutal-use-div_u64-to-let-it-build-on-32-bit.patch
  0025-tcp-Add-a-sysctl-to-skip-tcp-collapse-processing-whe.patch
  0026-net-tcp_bbr-broaden-app-limited-rate-sample-detectio.patch
  0027-net-tcp_bbr-v2-shrink-delivered_mstamp-first_tx_msta.patch
  0028-net-tcp_bbr-v2-snapshot-packets-in-flight-at-transmi.patch
  0029-net-tcp_bbr-v2-count-packets-lost-over-TCP-rate-samp.patch
  0030-net-tcp_bbr-v2-export-FLAG_ECE-in-rate_sample.is_ece.patch
  0031-net-tcp_bbr-v2-introduce-ca_ops-skb_marked_lost-CC-m.patch
  0032-net-tcp_bbr-v2-adjust-skb-tx.in_flight-upon-merge-in.patch
  0033-net-tcp_bbr-v2-adjust-skb-tx.in_flight-upon-split-in.patch
  0034-net-tcp-add-new-ca-opts-flag-TCP_CONG_WANTS_CE_EVENT.patch
  0035-net-tcp-re-generalize-TSO-sizing-in-TCP-CC-module-AP.patch
  0036-net-tcp-add-fast_ack_mode-1-skip-rwin-check-in-tcp_f.patch
  0037-net-tcp_bbr-v2-record-app-limited-status-of-TLP-repa.patch
  0038-net-tcp_bbr-v2-inform-CC-module-of-losses-repaired-b.patch
  0039-net-tcp_bbr-v2-introduce-is_acking_tlp_retrans_seq-i.patch
  0040-tcp-introduce-per-route-feature-RTAX_FEATURE_ECN_LOW.patch
  0041-net-tcp_bbr-v3-update-TCP-bbr-congestion-control-mod.patch
  0042-net-tcp_bbr-v3-ensure-ECN-enabled-BBR-flows-set-ECT-.patch
  0043-tcp-export-TCPI_OPT_ECN_LOW-in-tcp_info-tcpi_options.patch
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
            'a91afecda4aed1e9165dc9e3303eb44ffa791e7fb615b7717c04318b2ab98af2'
            'e32903a97ff3b4626b42201829c5c22229448cf98fdf6f755dc06a8d3958221d'
            '370fe2c70073b79d3e3cb92b166ab1366069a7d5075e0aaf05f893c5862629d0'
            '49586f20e99796d3aa4a689e389b1183f850e2a112859ddc794cd3caea126e53'
            'c68c40721bdff6660647d2d0a7c586f48b18cfd95990c4f8e32770ef8464edb9'
            '311cee56fd42b0d6a3147652a3024fbf81f75c2b6e48b27b921db3e004ad88c1'
            '26a2d17b17d1814c797fa5029bd68acab70ffe3fd9e173bae298bb50ae02825f'
            '0f329e9c5b75ea120923633513dd2742bc68af7923a7a1cce9bbf542e4cc2d0f'
            '2077da6458994a5d22d970c354836dcc1f2b2d14c399f7711abe39e1856cee73'
            'be64667d77d80cc19830d2b49c534074cc115c882f20f1fa9428d7ea30f9a034'
            '037389c25fc079dcb3b795a1f727d7790016a5e6a4f3733bfb4cc937743bfe76'
            'c17fbaa4f51a932ba25ac38f4ac3dd093c20023e105d506c6f3e1e1d1add5844'
            '69674d51d8b6433b82c547cda96a5669f7e080739e2a7b149b4eea574960deb3'
            '74ea4decbe33eba65ec1d7f55ce477ad0ac4803836883c471b08ef8327a11cab'
            '01c6abdf46394b84903845095f579adab441c4a6f145fd45d232cd1bea4e20f9'
            '988aca34ec59256a132b916e1a80b6d83ce8274f7a02ec90f3ba9dcbcfbf9a6e'
            '5c12fff7cfbf7f9bcc3e7bc4f715d3c9476cf3c9bb88f22d58e8ec4337bd755b'
            '219e9a97b79a181b8135038531e23679d149a2f9c00c5a2d9cdd5555be518fe4'
            '6ac6af20c8a6cf05d7f2ff519476e61ca43b7c05c6d4e0322eae9f9f149852be'
            'eac6f84c1d778a1e85ce23cef4ee7cb04f2ca6b09804da86d1657f501daece27'
            '0eb72d0c54e5685d9dcb41e54b71b07bc477ca1cbf3870c65733ff13880c952b'
            '2f6dc779e74a762b53d139b7545779d937a0c0b36adb1555730b19e715a6f156'
            '9d85a0dfcb188eea01abc2f511b224b7345c056f43f81ee5e5403bb43e389483'
            'e3a4a3daf7d647194106ad96bf10381d26a5c879ff45293f3cb08abf95a9c095')
b2sums=('521d01b10be736cc7be1108ad0fe9b046aad0ba5af02539d3d0425e424d5c081aaa69446e9f861e5ff4166c0f99201cb827b044d5a70816e4059f53f417c945f'
        'SKIP'
        'a4941becc7b96caebc6141c374a936ae7eca2db0963c692ccf43358df832a071c6ba67cd4d13c4079ada58feaa4e699b9185bfe69f7a2a5f3eea3e2a60877d15'
        'SKIP'
        '02a10396c92ab93124139fc3e37b1d4d8654227556d0d11486390da35dfc401ff5784ad86d0d2aa7eacac12bc451aa2ff138749748c7e24deadd040d5404734c'
        '5dc21a7a6f0b840e6a671dcf09a865e42f0e2c000d5e45d3f3202c02946a8ab2207858d0b2ef1004648b8c2963efb428298b263c8494be806dfc9b6af66d5413'
        'ba6ebe349b3757411364a9ba2deaa30a8d71a247d518c159385977c2b4782771bda4edfc96bd954808617c9ba984d832471b63c11f5bd6003369bfe4051df31f'
        'b4818abc884f9581c5c8a8940cb63142cb5f7fa829a6705ec7c052c2271e3e7450364524c53ef0195e38e1137a2ff285a9eee98526be12de43985d0e09823137'
        'fd7f6d316b5bab64ecf2794e9ba2c2e145fb75ca719e7a45df277be340a9288117e0052ac8640423361bad8f3eed2e81b7cd054115325130dfdef106031b9817'
        '947bd89f5dc4ac9c0dc34fe7d9c4548a36b1107d3afef7be89e6946d2a74f7290624b58f142acf5a38304ea997401b78bc0a1469275e87690a15f06c247eaec8'
        '59b2fa102e40428081f7bf447f03686bac3c3e4af1813bf4d859eb3ed22154a89f04468ca4c274f47cfd6d6f69d3d447736fd459904db4cfd25d2e9cfecf6131'
        '4d05b385dae0c2406ca0dc4b032eecfc2db912f45551ec4a00c04ae0a889689a4a45e24ff7e0cd7a8e2fb8c3197600d1aa77762800eae24fbaa0f3336da124ad'
        '437e724436c1efcc4019f80466cf0c15b1a027cda4482f14b353386b611ef27211a29ac7ad3f5cc3bc8e9461f765bd408744cdc249da38027fff493598fcc220'
        'eafc4a591fc8627f38af6875cc74be896cb6da5b9dcca0fb5a05d9cbe01ef2ebeb59fcc9383d234a613b9665437acd4bd34adcafba6b155e6980f9d43c740333'
        'fe166ee111f4d4f25a803f0126d071d99a4bbf77a1268c07da35af51374d515197244c94808b2b189761f34fe43c6a97ed6decf82da0c9bd18110112beae9ffe'
        '2d73ea47fe924059fe8172dcecbb9c60239728211c5bf7b7dcfea9dbece4d1a41d467e41afd6e661c350f491b80c0e3fe88f5a9596c0598d1c0df3fb2debbed3'
        '6d939a211b687545d1dbd5e650c46123dd0d4810d52be04a12188abeab3f8f86cf49d710654167bc15c01d9817c6605c8c685142e086d8148f4b36eeba18c774'
        '85faebd5bc2bc5d247f5055d412da3073bf594b0f414f8e3ae820c88653f2c45cc0ff9bcae2da7361e2bffdac8e806ed477bb04d5dc6e1a48907944708945956'
        '1b9855753135671bea7fc60e177ec6f0d84b770d9b0b7f0d915737b26c5a517bf03517d4ddee4773843f4f4928fe6a13a210bcab656f0ce465198080bd69ab45'
        '11378991f2e2db46cf91610c8bbf6d423b02089d9ffc9a5acb4881d901f6f4576586b1c5bf890ca519fea3151d6767d5b8369a3790c7f442ef1e5aa3fef1e250'
        '5efee238d69f15d34102aa7391593f9fc62a4d2327dc671e171362642d0e92df0fa6aafbb1ad38e5ac53939071b34396f8b3b1683e512d7aa528282e244a5755'
        'ec48d48151a25243f345fea66b9cf093e785ed330cc2e307c86d99c6af72617b0b64b699a9a18363fb8d3eac3145682950f5f0c850fb6157cb0a72302d1ed6ba'
        '352baa96ffeccedf0e6c665de75dd3cedc81ca02e95f3ead5a5631f3a4f2f443d9e361c77a31bf1f18f59bc7bf242575e255eff244540c4d5f0d8d86b4a5c177'
        '9e2e6d9dd9e5fdb8c0635f6cbc54afecf713ffadf2bb1527097b2caf562d8b75c259485629612b1ccb725ff38e4113ea2116c1f2e5ce199e6831aad6a6ae29fb'
        '61de160834df9f3d6af0b964e07e66f1d85980f463d0df30f0d00e4cf11684b2a28f15e32bb86a43918e01d0364ef0d9cb2f9ba86187eb460f5a44d35390bb91'
        'f097ad89b3345bb9a2ec1849221d4748fcb9d286037fb2b19aa24ab8c76ae36d255f13b695f3d3839872ab6c5c306fbf816f5025d0519114deea56c65eb4ef02'
        'c4231ac68fa14bd4d4e165bebfd8bb01c6cbf147f2dc520645ae83bf950258259d4bc490da43999b533d3522a11c5d51f8e5a0714ae74544fb1d42ef9db3984b'
        'b4efc51e1e548ed2e688e06a8d11e4d82a6ff4700006ea81dae24a2040838b64d3466064e2f6b36bea3c3e2ce5d397042e72eea5dff226c2cd0f4d3cf0d89dfd'
        '50fd55d35af15ad8aa50c65ff740bdb7a2f37819ebcb65ae301db6d022e201be90c4efe7e7b003f76625628776879e655f101a36e4635fccd3a51d45249600ff'
        'ad5430e67f5e80d20b1b9ab47f9402a8bc99011ddd4d30ec36402744229fe4d3cd11108c34f54344fa4b0329b596b4fc50ff65f7aa1d8e1b5449ebd05fee2e0b'
        'd3940728bd3c43edf03548c90c5c109fec9b06bc068c98504ba796e0d67672a9539a9ca9a9e9f1868ce866c5fe046527224bc66b86c6b4db26d3694943cc5465'
        'd24d0b9effce50e39de5078f73fcc2420c2f95a2e23dadfacec457f6d907555861f1c1977797db324ba37684c5aa875cce91468ff3ed0849f74afc0bea7f568d')

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
  scripts/config -m TCP_CONG_CUBIC \
                 -d DEFAULT_CUBIC \
                 -e TCP_CONG_BBR \
                 -e DEFAULT_BBR \
                 --set-str DEFAULT_TCP_CONG bbr \
                 -m NET_SCH_FQ_CODEL \
                 -e NET_SCH_FQ \
                 -d DEFAULT_FQ_CODEL \
                 -e DEFAULT_FQ \
                 --set-str DEFAULT_NET_SCH fq
  scripts/config -e NETFILTER_XT_TARGET_FLOWOFFLOAD
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
