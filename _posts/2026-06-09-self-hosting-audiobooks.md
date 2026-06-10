---
title: "Self-Hosting Audiobooks"
date: 2026-06-09
---

# Audiobooks

I enjoy listening to audiobooks. It allows me to engage with a book while I do something else. Specifically, I enjoy listening while cleaning, running, or on long car rides. I do not like having all of the books I have purchased locked behind licenses. Here is my current set up for self-hosting audiobooks.

## Libation 
### Getting Your Titles
I found [Libation](https://github.com/rmcrackan/Libation) a while back. It is, "a free, open-source application for downloading and managing your Audible audiobooks. It decrypts your library, removes DRM, and lets you own your audiobooks forever." 

It was shockingly easy to set up. I initially installed it on my Ubuntu laptop and when I add a title, I run the importer. It then delivers a DRM free version of my title

## Audiobookshelf
### Hosting Your Titles

[Audiobookshelf](https://github.com/advplyr/audiobookshelf) is pretty much Plex or Jellyfin but for audiobooks and podcasts.

They have a docker container, which I am running on my Raspberry Pi 4 for the server. 

It was very straightforward to set up. 

### Listening To Your Titles
They also have an incredibly performant [Android App](https://play.google.com/store/apps/details?id=com.audiobookshelf.app&hl=en-US&pli=1) (especially compared to Audible's). 

I was able to point to my Tailscale address for the audiobookshelf docker container from the app's interface. Now I have all my audiobooks on the go without any pain. It saves my spot, has great metadata, and has features I have not even played around with. 

Additionally, I set it up to capture podcasts which I want to have a personal archive of from the podcatcher interface. 



## Do Not Sleep on the Library
### Libby

Usually I do not re-listen or re-read books. There is just too much out there to experience. That is why I love the library. I use [Libby](https://libbyapp.com/interview/welcome#do-you-have-a-card) which allows you to check out audiobooks using your local library. Unless a book is an exclusive on Audible or another service, or the library in question does not have the title, Libby is my first stop. It is a phenomenal service. Libraries are amazing. And you do not need to own everything.

