---
title: "Too Smart Devices"
date: 2026-10-25
---

# Too Smart Devices
Forgive the low effort pun. I have two stories to share about smart devices.

## Smart Bassinet 
We grew our family in February and I got to enjoy [some parental leave this summer to bond with the little guy](https://joethor.dev/2026/05/12/parental-leave.html). 

We have some wonderful friends who lent us their [SNOO](https://www.happiestbaby.com/products/snoo-smart-bassinet), which is a smart baby sleeper and bassinet. 

The idea is, with the baby strapped into the bassinet, the SNOO will monitor the babies movements and respond by rocking the baby as needed. For parents, anything that promises to "fix" sleep for a kid is tempting snake oil. 

The company behind the SNOO previously provided the bassinet for a set price and it would work. They have since optimized their business model to turn it into a subscription based service, which requires a constant online connection and a monthly fee. Our friends, however, were grandfathered into the older agreement, and we were able to try it out.

Well, try it out in theory. 

It has an app that enables the bassinet's connection to the internet. During set up, it would not connect to download the firmware updates. I temporarily disabled my [Pihole](https://pi-hole.net/) and tried again and came up short. After researching the issue, [we have 5ghz wifi and SNOO recommends 2.4ghz](https://www.reddit.com/r/SnooLife/comments/o0sgrg/wifi_network_5ghz/). I switched the network to 2.4ghz and tried again. Nothing. Then I got interrupted and forgot about the set up. 

So the network remained 2.5ghz. Suddenly, my partner's Pixel 7a overheated and basically was unusable. We were trying to figure out what could have caused the device to become unresponsive. After switching the network back to 5ghz the Pixel came back to life. In hindsight, I should've set up a guest 2.4ghz network or something ephemeral and temporary for the SNOO. 

We thanked our friends and decided the SNOO was not for us. 

Overall, I am grateful we got to try it out, but the SNOO was more trouble than what it was worth. And now we do not have to try to transition from having that sleep assisted bassinet now that our youngest is in a crib. 

## DIY Smart Kettle 

I bought a [$20ish SwitchBot switch flipper](https://us.switch-bot.com/pages/switchbot-bot). I attached it our most important appliance, the electric kettle. 


![The Kettle]({{"/assets/images/smart_kettle.jpg" | relative_url}})

The app is *fine*. It keeps trying to get me to set up an AI assistant to manage the single device I have. 

![No Thank You AI]({{"/assets/images/switchbot.png" | relative_url}})

But, it has been a game changer. I set it to flip on the kettle 10 minutes before I usually wake up, and the water has boiled and is ready for coffee! I have this on a schedule so it just happens.

Or, I can think about a cup of tea, hit button in the app, then go up for a cup of tea a few minutes later without getting *as* distracted from work. 

It is simple, it works, the app is tolerable, and most importantly, I can remove it from the kettle and the kettle will continue to function. 

## Ending Thoughts

Smart things can be more trouble than they are worth. The worst example of this is building a stellar automation that makes your life easier, but suddenly it breaks. The two examples above are an obvious failure (SNOO) and a pretty great success (or failure waiting to happen) the SwitchBot Kettle. Arguably, I can go back to making my analog tea without issue (just a couple of minutes waiting). The SNOO was basically useless and worse, caused knock on effects with our home network. 

I contend the smartest devices are ones that still function when the internet goes down. 