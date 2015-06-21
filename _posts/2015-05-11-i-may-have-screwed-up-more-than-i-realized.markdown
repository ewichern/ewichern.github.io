---
layout: post
title: I may have screwed up more than I realized...
date: '2015-05-11 08:34:01'
---

###### Remember that [post](http://usingname.space/2015/04/26/improve-your-linux-satisfaction-in-one-easy-step/) about ripping out Gnome when I installed Xfce?

Well, every once in awhile I stumble across an unintended consequence. Like tonight, when my wifi didn't automatically connect... I recently upgraded my [LG G2](www.lg.com/us/mobile-phones/g2) to [Lollipop](https://www.android.com/intl/en_us/versions/lollipop-5-0/) (5.0.2 is all I got, but I'll take anything for a 2013 phone), and in the process my hotspot information got reset. So (unsurprisingly) the saved network information that linux has been using to automagically connect to wifi doesn't work for that hotspot anymore. I've been using the ethernet jack recently, so hadn't noticed or needed to fix it, but tonight I didn't feel like plugging in... which was a problem.

I went poking around the Whisker menu for a network configuration manager -- and find nothing. It began to dawn on me that I may not have one installed at all if Xfce didn't come with one by default (it does not). Shit. So, I fell back on the rallying cry of linux geeks everywhere, "to the command line!"

Obviously (and annoyingly), I also couldn't look anything up (besides linux [man pages](http://en.wikipedia.org/wiki/Man_page)) on the laptop itself, so I was poking around on my phone while I attempted to figure out exactly which command line utility would allow me to reconfigure my wifi network. In the end, the internet actually wasn't even very helpful, and it *was* the man pages after all that held the solution to my problem. After peeling back some layers (`ifconfig -> iwconfig -> nm-tool -> NetworkManager`) I finally stumbled upon the `nmcli` utility which allowed me to modify my wifi configuration from the command line.

The command that did the trick was:
`nmcli dev wifi connect 'insert-SSID' password 'insert-WPA-key' wep-key-type key`

Anyone who wants to investigate further can find read more detail by typing (on a linux system) `man nmcli` and then `\wifi connect` (man pages use many [vim-style commands](http://tnerual.eriogerg.free.fr/vimqrc.html), e.g. backslash to search). Or find a copy of the man page here: http://linux.die.net/man/1/nmcli

In my case the wifi hardware was recognized, had a driver installed, and was enabled. It just didn't have the right information to authenticate to the hotspot, and no GUI to notify me or allow easy input/modification. So nothing too difficult to fix this time -- I have *horror* stories about drivers for network adaptors, both wired and wireless, but thankfully linux network drivers have matured quite a bit over the last 10-15 years.

The lesson here is to not indescriminately `apt-get remove` every trace of gnome from a linux computer! At least not without carefully considering all the places you don't think about where a distro is using little gnome apps... 