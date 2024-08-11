# EGOIST LTS Kernel for Arch Linux

Based on the official LTS repository of Arch Linux.

## Support Microarchitecture

Since version `6.6.32-1`, the kernel will minimally support the x86-64-v2 Microarchitecture.

```
~/linux-egoist-arch main* love4taylor@sony-nuro-n1.love4taylor.com
❯ /lib64/ld-linux-x86-64.so.2 --help | grep supported
  x86-64-v3 (supported, searched)
  x86-64-v2 (supported, searched)

```

## Installation

### Prebuilt binaries

```
wget -q --show-progress $(wget -q -O - https://api.github.com/repos/love4taylor/linux-egoist-arch/releases/latest | jq -r '.assets[] | select(.name | contains ("tar.zst")) | .browser_download_url')
sudo pacman -U /path/to/file
# The headers package is not required, only if you need to compile kernel modules.
```

### Build from source

```
gpg2 --locate-keys torvalds@kernel.org gregkh@kernel.org nathan@kernel.org
git clone https://github.com/love4taylor/linux-egoist-arch.git
cd linux-egoist-arch
makepkg --syncdeps
sudo pacman -U /path/to/file
```

## Switch kernel

### systemd-boot

```
~/linux-egoist-arch main* love4taylor@sony-nuro-n1.love4taylor.com 20m 45s
❯ cat /boot/loader/entries/linux-egoist.conf
# Created by: archinstall
# Created on: 2024-04-24_16-08-53
title   Arch Linux (linux-egoist)
linux   /vmlinuz-linux-egoist
initrd  /initramfs-linux-egoist.img
options root=PARTUUID=89d2b8d2-5e05-4e77-aa42-40314ea38958 zswap.enabled=0 rw rootfstype=ext4

```

### grub

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## Patches

- Arch Linux official patches
- Graysky's Kernel patch enables compiler optimizations for additional CPUs
- Broadcom fullcone NAT from ASUS Merlin
- Netfilter FLOWOFFLOAD target
- BBRv3
- Cloudflare: Add a sysctl to skip tcp collapse processing when the receive buffer is full ([How-to-use](https://blog.cloudflare.com/optimizing-tcp-for-high-throughput-and-low-latency/))
- TCP Brutal
- Partial Clear Linux patches

## Notice

1. **This kernel has a built-in TCP Brutal module, please do not use the official installation script to install the DKMS module.**
2. I **hardcoded** the enable parameter for fullcone to prevent recompiling iptables or adding nftables parameters to use fullcone, so you can use MASQUERADE as usual, and it will **force** to using fullcone.

