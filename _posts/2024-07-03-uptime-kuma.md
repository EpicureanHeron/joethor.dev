---
title: "Uptime Kuma"
date: 2024-07-03
---
[Uptime Kuma](https://github.com/louislam/uptime-kuma) is a self-hosted application that will monitor your other applications. It can notify you when those applications no longer are responsive.

Today, during breakfast, I got 4 Discord messages in quick succession.

Four of my applications were no longer reachable by Uptime Kuma so it alerted the channel I set up on Discord for this very scenario. 

I noted that all the IP addresses were the same, so I just turned the Pi off and on again. Everything was up and running in a few minutes and I got confirmation messages via Uptime Kuma. 

I think, ideally, I would have this either on its own dedicated piece of hardware or potentially on a virtual private server outside of my network. There is a scenario where the hardware that Uptime Kuma is running goes down and then the tool itself cannot push the alert. Or power is lost in the house. 

For now, I am running it on a Raspberry Pi 3B+ along with several other services. 
