---
title: "Lost Lube Saga"
date: 2025-11-07
---
# Lost Lube Saga
To quote my [last post](https://joethor.dev/2025/10/19/sd-card-died.html), "I got very lucky, nothing on the card was important data." 

Yeah, about that.


## LubeLogger
I was running a service that I have fallen in love with, [LubeLogger](https://lubelogger.com/), and it is NOT what you think.

I always found car maintenance daunting. My dad is very mechanically inclined. I am not. 

LubeLogger created a structure around basic car care and allowed me to feel like I could track things and, more importantly, know I had a single source of truth.

Anecdotally, it has saved me money. We have jumped between different mechanics and so, they do not have a whole history of our car. Being able to say that the differential fluid was actually flushed at a different shop, even though the manufacturer does recommend it is serviced at the current mileage reading, felt really validating. 

It even got me to replace the battery in the car myself on New Year's Day this last year. I felt like I could actually track this stuff and, because I could track it, I could potentially do some of it. 

Too bad I didn't back it up. 

## SD Card Died, Oh FSCK 
The micro SD card that powered the Raspberry Pi that I ran LubeLogger on died. I did try to restore it and I learned about some useful tools.  My approach lasted a weekend and was very scattershot. 

### TL;DR

I could not restore it. 

I did learn about `fsck`, `dd`, and `ddrescue` 

### The Details

I removed the card and tried to mount it on my laptop, which is running Ubuntu.

Here is the error message that popped up. 
```
error mounting /dev/mmcblk0p2 at /media/MYUSERNAME/rootfs: wrong fs type, bad option, bad superblock on /dev/mmcblk0p2, missing codepage or helper program, or other error
```
I did some research and found the following potential leads:

- https://unix.stackexchange.com/questions/315063/mount-wrong-fs-type-bad-option-bad-superblock

- https://unix.stackexchange.com/questions/494491/sd-card-recovery-without-data-loss-or-corruption


- https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step

I tried to get more info on my situation by running `lsblk -f`
```
sdb                                                                         
├─sdb1
│    vfat   FAT32 boot  29F5-65C4                             224.3M    12% /media/jft/boot
└─sdb2
     ext4   1.0   rootfs
                        cbe4d267-24de-4402-9a4b-1413a1da5eb8     
```


I started with DDrescue. 

### DDrescue
DDRescue can copy data and create an image from that data. Pretty cool! It also have utilities built in to try to fix corrupted data. 
- https://www.gnu.org/software/ddrescue/
- https://darwinsdata.com/how-to-use-ddrescue-in-ubuntu/
- https://linuxconfig.org/how-to-repair-and-clone-disk-with-ddrescue

I installed DDRescue  `sudo apt install gddrescue`

The goal at this phase was to dump the contents of the microSD card into an image that I could interact with rather than having to try to get the data off of a dying/dead microSD card every time I tried to restore the data. 

After reading the above, I tried `sudo ddrescue -d /dev/sdb backup.img backup.logfile` 

This was successful! I got an image of the corrupted card. 

I also tried to repair the image off the micro SD card (I should have, and probably could have done this with the image I just created).

`ddrescue -f -n /dev/sda /dev/sdb sda.img` 

The `-f` flag is for "force" which "Force overwrite of mapfile."
The `-n` flag is for "Skip the scraping phase. Avoids spending a lot of time trying to rescue the most difficult parts of the file. "

I'm not sure if those are the best flags to use, but the guides I read recommended them. 

This ran a long time. At one point, it said it was going to take at least 24 hours, but ultimately it finished in around hours. 



```

GNU ddrescue 1.23
Press Ctrl-C to interrupt
     ipos:   32026 MB, non-trimmed:        0 B,  current rate:  29687 kB/s
     opos:   32026 MB, non-scraped:        0 B,  average rate:   1514 kB/s
non-tried:        0 B,  bad-sector:        0 B,    error rate:       0 B/s
  rescued:   32026 MB,   bad areas:        0,        run time:  5h 52m 23s
pct rescued:  100.00%, read errors:        0,  remaining time:         n/a
                              time since last successful read:         n/a
Finished       
```

This looked promising! It said everything was rescued!

### DD 


I wiped the old micro SD card. 
I tried to use the very powerful `dd` to reflash the image on the recently wiped card. 

- https://linuxconfig.org/Dd

So I tried writing `sudo dd if=mmcblk0.img of=/dev/mmcblk0` 

This ran the on the old card, but resulted in the same issue. It could not mount the root file structure and the boot partition was in read only. 


### New Hardware 
I then bought a new microSD card and tried the same `sudo dd if=mmcblk0.img of=/dev/mmcblk0`, with the destination being the new card. 

The image was succesfully written, then I tried `fsck` the card to repair the corrupted partitioned. 

`fsck` is a file system check. It can also be used to repair file systems. 

```
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/mmcblk0

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/mmcblk0

```
## Summary 

So, after trying some command line incantations, buying new hardware, and lot of patience I am unable to recover any data from the card. I suspect I could pay some money to get the data back. If **you** have any suggestions, please reach out. 

Most of the important data from LubeLogger was transcribed from invoices I saved elsewhere. Other than that, it was a lot of data related to gas mileage. I will lose that, but I am OK with that. 

I need to re-enter the data I have, but that is fine. 

Now, that I actually lost data due to carelessness, I will set up a backup plan. I think I will start with some very basic rsync commands. But I learned some cool and potentially useful commandline tools along the way. 

