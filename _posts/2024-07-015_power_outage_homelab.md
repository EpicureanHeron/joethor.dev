---
title: "Power Outage Homelab"
date: 2024-07-15
---

Power went out last Sunday morning just as we, as a family, were about to run some errands.

We figured it would be back up after a few hours.

It was an interesting opportunity to test out my [Uptime Kuma](https://joethor.dev/2024/07/03/uptime-kuma.html) and how it would handle the situation.

Since Uptime Kuma was on the same network and power supply, it did not handle the situation well. 

I want to call out some tools I did use after the power outage to get my homelab up and running again remotely.

I received an email from the power company while we were getting the last odds and ends of our shopping trip.

From the parking lot of grocery store I was able to get over 50% of my homelab up and running again.

## Homelab Back Up and Running 
I have [Tailscale](https://tailscale.com/) installed on my homelab hardware and my Pixel 6 phone which creates a mesh network for all devices.

Tailscale autostarts when my Raspberry Pi boots.

I was able to use [JuiceSSH](https://juicessh.com/) to SSH using the Tailscale address for Raspberry Pi that handles several of my services.

All the services I run use docker-compose whenever they can. I had to manually restart Uptime Kuma. That was no issue, but Uptime Kuma also uses a Cloudflare Tunnel to manage some of its monitoring.

I was able to get my Cloudflare tunnel up and running again. This is a fairly complicated docker command I always have to look up:  

`docker run -d cloudflare/cloudflared:latest tunnel --no-autoupdate run --token <TOKEN_INFO>`
  
I should move this to a docker-compose.yml.

Several of my other services did not require additional intervention, they just restarted when the Pi they were hosted on received power. And once the Cloudflare Tunnel was back up, I was able to access these through the custom domains I have for their respective services.

Interestingly, my Pi 4 did not restart on its own. I have it housed in a [Argon ONE M.2](https://argon40.com/products/argon-one-m-2-case-for-raspberry-pi-4) which has some unique firmware to handle its power button. Uptime Kuma let me know that all the services on this device were not accessible.

Some takeaways I have from this experience

- Long Term
    - [ ] Move Uptime Kuma offsite
- Short Term
    - [ ] Set `restart: yes` for Uptime Kuma's docker-compose.yml
    - [ ] Set Raspberry Pi 4 to autorestart (if possible)
    - [ ] Cloudflare Tunnel needs to be moved to a docker-compose file and set the `restart: yes` flag