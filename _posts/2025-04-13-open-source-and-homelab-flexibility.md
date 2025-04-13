---
title: "Open Source and Homelab Flexibility"
date: 2025-04-13
---

# Open Source and Homelab Flexibility  

Short anecdote that exemplifies the flexibility of open source, AI, and homelab.

I wanted to try out a new service I read about in [This Week in Self-Hosted newsletter](https://selfh.st/newsletter/). 

I was traveling at the time, sitting in the passenger seat of the car as my partner drove and our two kids sat in back quietly focused on their devices. 

The software in question was [Omni Tools](https://github.com/iib0011/omni-tools) which wraps some pdf, image, and text tools into one local service. It reminded me of another service I run locally that I get a lot of utility from, [It Tools](https://github.com/CorentinTh/it-tools). 

I ssh'd into one of my raspberry pis at home using [JuiceSSH](https://juicessh.com/) over [Tailscale](https://tailscale.com/) and tried to build the container.

I hit a problem immediately, there was no ARM version for Omni Tools. 

What happened next embodies why open source is a powerful community. 


## Next Steps
- Checked to see if I did anything wrong, then looked at the issues in the repo
- Finding no open issues, I opened an issue asking for a ARM focused docker version to be made available
- Within 20 minutes I had a response from the dev asking me to try again
- Successfully built the service from the passenger seat of my car
- Verified the service worked by navigating to the Tailscale address and port

## Take a Penny, Leave a Penny PR 

I was stunned and delighted with the quick turn around on this response and I also thought it was very cool to do it all from within a moving car. I wanted to contribute something back to the repo. 

I noticed there were options for docker but not a proper docker-compose.yml file. I prefer to run things with docker-compose, so I don't have to type out my commands every single time. I think this is a bit of a standard for a lot of people running homelab services

### The PR (with an AI assist)
- Took the docker command and had AI generate a docker-compose file using the ChatGPT 
- Tweaked the docker-compose.yml because some of the parameters were not quite right
- Opened a PR to add the docker-compose.yml example to the repo's Readme
- Viola it was approved!

## Final Thoughts

I respect how quickly they responded to my issue and I just wanted to add some value back. Which, I think, it is part of the open source community's very essence. We all benefit from one another's work. Also, how cool is it to be able to manage servers and services while sitting in a car going 70 mph from your phone? 

## Other Random Asides

No, AI is not perfect and probably was overkill for something like this. I love Tailscale and worry it will do a heel turn like [Plex](https://gizmodo.com/plex-is-going-to-make-you-pay-for-its-best-free-feature-2000578442). 

The PR itself was low hanging fruit and I am glad the developer found it appropriate to add. 

