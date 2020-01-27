---
title: "Removing Python on Raspbian causes some unforseen problems"
description: "The dangers of troubleshooting without --dry-run"
date: 2020-01-13T15:12:44-08:00
tags: ["Raspbian","Linux","Python","Troubleshooting"]
draft: false
---

On Raspbian, I was having an issue with Python3. My first instinct was to uninstall and reinstall.

Que “I can fix it”:

	$ sudo apt remove python3

“Oh f#@&”

Turns out, Debian (And by extension Raspbian) uses Python for tons of things.

Que: Panic. A lot of it. I started mashing CTRL-C

In the end it didn’t uninstall too many things, and my terminal was still functioning, so I tried to repair the damage.

I made a copy of /var/log/apt/term.log and found the full list of packages it had uninstalled, and cleaned it up using vim.

:%norm Wd$

Worked like a charm

Then I took the cleaned copy of term.log and ran: $ cat ~/apt.log | xargs sudo apt-get -y install

Looks now like everything is in its rightful place. Hope nothing is broken. Going to try a reboot and hope for the best.
