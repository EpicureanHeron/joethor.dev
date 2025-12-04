---
title: "Restart Flag Note in New Docker Service"
date: 2025-12-04
---
# Restart Flag Note in New Docker Service
When trying out a new Docker container, exclude the `restart: unless stopped` flag. Or any restart flag really. 

You will thank me! This is a post for me to reference in the future but maybe you will learn something too. 

This is especially important if you are running things on a lower powered device, such as a Raspberry Pi. 

## The Specifics 

I tried out [Stirling PDF](https://github.com/Stirling-Tools/Stirling-PDF), a service I hope to use in my homelab.

PDFs are terrible in general and the software built up around them is aggressively commercialized (*ahem* Adobe). 

I am more comfortable using docker-compose files over just using a docker command. 

In my experience, it is easier to replicate things by capturing the configs in the yml file instead of them being lost in the terminal history.

I converted the docker command into a docker-compose file and ran it.

The Pi I was using (along with the other containers) couldn't run it due to the required overhead. I think the CPU was the chokepoint as Stirling PDF uses Java, but I am not positive. 

I restarted the pi (forcibly removed the power cord, I know, bad practice). 

And then, upon restart...it became unreachable again because the CPU hungry service kicked off again. 

I finally had to forcibly reboot (sorry again), then ssh to the device as soon as possible, then I did `docker compose stop` from within the Stirling PDF directory to free myself from the disastrous loop. 

This has happened to me twice, and I'm writing it down here as a reminder.

## TL;DR
If you are testing out a service with docker, never add the `restart: unless stopped`. 
 
