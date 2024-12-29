---
title: "RSS Updates, Read-It-Later, and Being Precious"
date: 2024-12-29
---

# RSS Updates, Read-It-Later, and Being Precious
This is a follow up to the post [My RSS Set Up](https://joethor.dev/2024/03/28/my-rss-set-up.html).  
Also, this is part of the [purging my drafts sprint](https://joethor.dev/2024/12/26/Purge-Your-Drafts.html) at the end of the year.

tl;dr: I switched the default. Previously, I treated everything as precious. Now I have to mark things as precious.

## Problem
I have several hundred feeds I manage through my FreshRSS instance. It is my window into the internet and the world.  However, midway through this year, I realized I was feeling overwhelmed by the"unread" count constantly going up.  

## Solutions
I made several changes that have helped me manage this.

The biggest one is that I enabled "mark an article as read by scrolling" which gets rid of anything I scroll past. You cannot be precious with everything. 

I also read the documentation on how [extensions work within FreshRSS](https://github.com/FreshRSS/Extensions). I now can read the entire headline of an article while on mobile by enabling the "Title-Wrap" extension. I downloaded and unpacked the zip file in the Docker container in the `./extensions` directory. I need to add this step into the docker-compose.yml so it does not get lost.

Finally, instead of assuming I will read everything later, I have embraced a bookmarking and read-it-later app called [Linkding](https://github.com/sissbruecker/linkding). I am able to integrate it directly into FreshRSS using their [custom sharing options](https://freshrss.github.io/FreshRSS/en/users/08_sharing_services.html). Now that the count of unreads in FreshRSS has been tamed, I find myself time to actually read the articles I have set aside. I am opting into being precious with the things in my read-it-later app. 

