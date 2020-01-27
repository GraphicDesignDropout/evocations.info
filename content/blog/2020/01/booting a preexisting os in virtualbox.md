---
title: "Booting a Preexisting OS in Virtualbox"
description: "Because Linux is /comfy/ but WINE is inconistent"
date: 2020-01-22
tags: ["Linux","VirtualBox","Gaming","VM","Windows"]
draft: false
---

I had an idea to get around rebooting to play some of the Windows games I enjoy. Why not virtualize a windows environment? What kind of performance can I get from a Windows VM?

Unfortunately, not great performance without some serious tinkering.

My current configuration is dual-boot Windows (Gaming) and Arch Linux (Work/Browsing). Quite a lot of my data was created before installing Linux, and at this point, would be too much of a hastle to organize. I have other priorities anyways, since I desperately need to backup, but having 6TB of data makes that fairly expensive. (I have plans to build a backup server, but am currently saving up cash to do so.)

I thought then, can I boot an existing Windows partition using Virtualbox? Turns out, yes! AND with minimal complications!

Using Virtualbox, I:

 1. Created rawdisk VMKD files pointing to the partitions I use in Windows.
 2. Created a virtual EFI partition.
 3. Attached Windows Installation ISO.
 4. Launched the VM and held my breath

To my amazement, the VM actually launched, and worked without many hiccups! I wondered how I would get the GPU to work correctly. Would virtualized video memory be enough?

After installing the Oracle Virtualbox expansion, Windows ran into some issues. Now, most of the applications rendered incorrectly, including the Task Bar. I looked into what it would take to get bare-metal performance of a GPU, and rendering everything correctly, but it required an additional graphics card and PCI passthrough. I do have a spare GTX-730, but that would still create some issues for me.

 - The GTX-730 would have to render Arch Linux, and the GTX-1070ti would render Windows
 - This means I can’t switch between the two, because they will be rendering to separate monitors
 - Who the hell wants to buy all those new cables? I don’t want to purchase a new mini-HDMI.

Unfortunately, I’ll have to scrap this plan for now, and either find a way to play the games on Linux using WINE, or just resign myself to rebooting anytime I want to have a gaming session.

---

BONUS ISSUE: After failing, and then rebooting into Windows (the intended way this time), my Windows license was invalid. Looks like the change in hardware caused the deactivation. No amount of troubleshooting or reactivating would work. I was worried about somehow my Windows license not being valid anymore since I upgraded from 8.1, but after a few days the problem resolved itself. Windows 10 is fully activated again :)
