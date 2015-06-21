---
layout: post
title: Operation too slow.
date: '2015-03-24 01:30:00'
---


I've been playing around with Linux VMs, and encountered this problem updating via [pacman](https://wiki.archlinux.org/index.php/Pacman) in [ArchLinux](https://www.archlinux.org/). Here's the error message that kept popping up:

```
error: failed retrieving file 'extra.db' from "insertMirrorNameHere" : Operation too slow. Less than 1 bytes/sec transferred the last 10 seconds
```

The [solution I found](https://bbs.archlinux.org/viewtopic.php?id=142891)  basically said to try updating the [mirror list](https://www.archlinux.org/mirrorlist/?country=US) to try pulling from other mirrors... Since I prefer to work smarter (not harder), and someone else has already put in the elbow grease, I used an existing automated tool to do this (see:  [Reflector](https://wiki.archlinux.org/index.php/Reflector)) The fix for me required the following sequence of commands:

First, I had to install Reflector.

```
sudo pacman -S reflector
```

Made a backup of my old mirrolist.
```
sudo mv /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak
```

And finally, reflector filters the first 20 mirrors, sorts by download rate, and saves the result to  `/etc/pacman.d/mirrorlist`.
```
sudo reflector --verbose -l 20 --sort rate --save /etc/pacman.d/mirrorlist
```

Then I tried to update again using `sudo pacman -Syu`. I still got a couple of the same error messages -- apparently at least one of my *new* mirrors was still timing out. However, pulling from different mirrors allowed the pacman operation to complete successfully despite a couple stray error messages.

Now the next time this happens I won't have to dig up instructions again. 
:-)

Cover photo: <a href="http://www.flickr.com/photos/beraldoleal/8681754154/">Beraldo Leal</a> / <a href="http://creativecommons.org/licenses/by/2.0/">CC BY</a>