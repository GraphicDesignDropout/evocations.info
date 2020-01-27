---
title: "Arch boot broken due to umount /boot"
description: "How in hell did I manage that?"
date: 2020-01-20
draft: false
tags: ["Arch","Linux","GRUB"]
---

I can’t pin down exactly when it happened, but at some point my laptop’s Arch partition stopped booting. It would give me an error “You must load the Linux kernel first!” What in hell do you mean by that? What changed since last week? You were fine last time I used you!

I suspected an issue with GRUB, but I understand now what actually happened. Some how, Linux had upgraded without /boot mounted, causing a version discrepency. /boot expected an older kernel, but all that existed was the new one.

The best way to fix this was to use an Arch live USB drive and mounting /root and /boot partitions, arch-chroot into my system, and pacman -S Linux.

Some lessons learned:

 - Don’t update blindly
 - Keep bootable Arch media nearby
 - Seemingly complex issues can actually be very easy to solve
