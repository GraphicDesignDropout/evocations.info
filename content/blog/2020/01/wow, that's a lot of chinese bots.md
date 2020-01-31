---
title: "Wow, That's a Lot of Chinese Bots"
description: "Learning to secure your Raspbian web server. The hard way."
date: 2020-01-22T15:36:02-08:00
tags: ["Raspberry Pi","Raspbian","Apache2","SSH","Web Server","Python"]
featured_image: "/images/count2json.png"
draft: false
showpage: true
---

If you’re new to IT like me, you might be surprised by how much your server is targeted. I run a small home server using a Raspberry Pi. It allows SSH connections via web, and I had no idea how much traffic it could get. I got curious and checked /var/log/auth.log.

Tens of failed authorizations each second.

Most of the IP address were coming from Chinese ISPs, or DigitalOcean servers. I wonder what these bots do once they break in? Time to harden security. I changed some settings within /etc/ssh/sshd_config

No longer accepting password auth Only accepting publickey auth

Then I learned to generate SSH keys on the devices I use to connect to the server. No more brute force attempts :)

---

I wanted to know exactly how many attempts there were, and from who.

	$ sudo cat /var/log/auth.log | grep -E "([0-9]{1-3}\.){3}[0-9]{1-3}" >> ipaddress.txt

I wrote a python script that takes ipaddress.txt and creates a JSON file counting each IP address and the number of attempts to brute force it had made. You can find it at https://www.github.com/GraphicDesignDropout/count2json

The results ranged from 1 to 756 attempts, and that was just from that one auth.log. I wonder what tools exist to beter monitor auth attempts?
