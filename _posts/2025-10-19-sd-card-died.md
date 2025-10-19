---
title: "SD Card Died - Homelab Impact"
date: 2025-10-19
---

# SD Card Died 
## Homelab Impact

One of the micro SD cards I use to power one of my Raspberry Pi's stopped working this week.

It ran the following services:
- [Pi Hole](https://pi-hole.net/)
- [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/)
- [Uptime Kuma](https://github.com/louislam/uptime-kuma)
- Custom Discord bot

I noticed two things. First, when I was on my tailnet, I couldn't browse the internet as I used the Pi Hole as a [tailnet wide ad blocker](https://tailscale.com/kb/1114/pi-hole). 

Second, only the red LED on my Pi was on. There was not green LED activity.

I found recently at work while replacing a Pi in kiosk on site that the green LED indicates [micro SD card read/write activity](https://raspberrytips.com/green-and-red-light-on-raspberry-pi/). 

I got very lucky, nothing on the card was important data. I literally have no back up strategy right now. I know about the [3-2-1 rule](https://www.backblaze.com/blog/the-3-2-1-backup-strategy/) and it has been on my list to implement a solution. 

This is a wake up call. 

I plan on doing follow up posts on this subject. First, getting the pi back up and running, re-establishing the services that were previously available. This will act as a sort of documentation I can refer back to if I ever need it. Secondly, I will detail the back up solution I embrace. 

