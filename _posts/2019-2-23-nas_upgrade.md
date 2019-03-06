---
title: Upgrading my Network Attached Storage
layout: projects
categories: projects
---

After a year or so of trusty service as a personal fileserver, my Raspberry Pi deserved an upgrade to its capacity and I implemented some rudimentary data redundancy.

<!--more-->

As a university student who is a little too paranoid of their data privacy, there's not too many options for me to turn to for centralized, dedicated file storage that I can access from anywhere. Dropbox and Google Drive exist, but I don't necessarily trust either of those services to respect my privacy. [Mega.nz](https://mega.nz) exists -- and has considerably robust security too -- but you have to pay to store more than 15 gigabytes of data. For my intents and purposes, I decide it would be fun to take a crack at hosting my own personal files.

The Raspberry Pi 3 proved to be the best solution for what I needed, since it takes up such a tiny footprint in my room and uses very little power. Although I've learned from [the datahoarder subreddit](https://www.reddit.com/r/datahoarder) that the Raspberry Pi uses the same data bus for the networking *and* moving around local data; for the budget and size limitations I'm working under the Raspberry Pi fits my purpose very well.

My personal cloud started out as an old external hard drive plugged into a powered USB hub, but as it became filled up with more and more precious data I began thinking ***"What if this drive fails? All of my data could be lost in an instant!"*** I could almost hear the dreaded _click of death_ in my dreams. This planted the seed of concern in my head, thus I began my research about different ways I could keep my data backed up in the event of a scenario like that.

After some brand research, I decided on purchasing two Western Western Digital 2 terabyte "Elements" external hard drive that would mirror each other.

![The two drives.](/assets/img/nas1.jpg){:height="60%" width="60%"}

Although I intend on getting a _'real'_ NAS when I figure that once I do the upgrade I can use the two external drives for cold storage in a fireproof safe.

![Network Attached Storage](/assets/img/nas2.jpg){:height="60%" width="60%"}

Luckily neither of the drives were dead on arrival and worked great with my Raspberry Pi; I secured everything together, formatted, and mounted both of them onto the filesystem. After about a night's worth of migrating all of my data over to the first drive the final step was to decide on how I was going to keep the drive back up. I decided to keep it simple and writing a simple script that ran the rsync utility:

```
#!/bin/sh
rsync -a --delete /mnt/drive1 /mnt/drive2
```

Everytime it's ran, it will check if there are any new files in drive1, if so it will copy the new ones over to drive2.
Conversely, if any files are deleted from drive1 that are in drive2 it will delete those files off of drive2.
I then set this script to be run every night at 4 AM on my crontab and it was all done and ready for use!

## Postmortem

Overall I learned a bit about data redundancy from making this upgrade, mostly thanks to the people over at /r/datahoarder. I'm happy with overall how this project turned out and I feel much more secure with important personal data in my NAS now. Although ideally I would like to have offsite backups to ensure my data is secure, perhaps sometime in the future I will find a way to implement that.
