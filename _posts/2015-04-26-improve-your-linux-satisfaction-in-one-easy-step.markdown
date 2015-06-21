---
layout: post
title: Dramatically increase your Linux satisfaction in one easy step!
date: '2015-04-26 10:10:08'
---

####Install [Xfce](http://www.xfce.org/).
I've been wanting to dump Ubuntu's default window manager, [Unity](https://unity.ubuntu.com/), for months now. It's buggy and bloated, and (in my opinion) not even particularly visually appealing. Since it's been a few weeks now from my transition away from Unity, I can't actually remember what the catalyst was that pushed me to make the change, but something gave me that nudge. 

I spent the time to really _thoroughly_ rip out Unity and all the [Gnome](https://www.gnome.org/) elements from my Ubuntu install. I don't actually have anything specific against Gnome, but I wanted to yank _everything_ out and see how I liked a "pure" Xfce/[GTK+](www.gtk.org/) environment. I admit I'm missing a couple of Gnome's desktop apps and settings managers, but Xfce does a pretty good job overall of exposing configuration options to the user through the GUI.

Finally, before I get into the things that I really liked about my new Xfce environment... Here's a tease -- I _did_ break something and describe that experience at the end.

####Performance
This shouldn't come as a surprise to anyone familiar with Linux windows managers, but Xfce/GTK+ is significantly lighter on resources than Unity. After a fresh reboot it saves me a couple hundred megabytes of ram. I'm ashamed to admit I'm typing this booted into Windows, but because I like to provide evidence for claims, I'll fire up a [VM](https://www.virtualbox.org/)... for Science!

I can't boot up my Unity desktop now, so you'll have to take my word that I relatively recently was checking memory usage after fresh boots (more out of curiosity and comparison to Windows than anticipation of swapping window managers) and recall my usage pre-Xfce being just shy of 600MB after a reboot. My current usage, running Xfce after a fresh boot is a little under 400MB. That, in my eyes, is a pretty significant difference. I mean, even with my usual paltry 8GB of ram, 200MB is only 2.6% of my total memory, so maybe it's no big deal on my primary two computers. But I also occasionally plug this Linux thumbdrive in to a work computer with only 4GB of ram, or run it as a VM with anywhere from 1-4GB of ram, so 200MB could be 5%, or up to even 20% of my total memory sometimes.

I will acknowledge right now that this number *may* not be an absolutely fair portrayal of Unity, since it was not anything close to a fresh install of Ubuntu (maybe 12-18months old at this point) and has likely acquired some cruft. However, everything has consistently been kept up-to-date with (mostly) official packages, and Xfce is still running on top of that same crufty installation, just minus the Unity and Gnome (plus supporting) packages. 

I'll also add some subjective observations -- Xfce seems to load more quickly (I haven't timed it though), and feels much more responsive to user interactions.

####Fonts
Having fine-grained control over font selection and anti-aliasing makes a spectacular difference when it comes to an operating system (or any software) appearing polished and providing a pleasant user experience. It's possible that while I was using Unity I never found the right settings window, or the right combination of compositor, fonts, and font aliasing settings to make things look pretty. 

But now things are different, and I can't believe I tolerated that shitty, blurry interface for so long.

####Icons and Themes
It was relatively easy to install new sets of icons and themes for Xfce. I know that Xfce is not unique in this regard among Linux window managers, and that you can also install new themes and icons for Unity. However, in my opinion, Unity continues to look like Unity -- just with new colors and icons. In my experience, there are some elements that can't be modified, moved, or hidden, so unless you want to remove the functionality altogether, you're stuck with something that still looks like Unity.

Xfce, on the other hand, specifies few limits on how the user can customize "panels" (for the uninitiated, think Windows taskbar). You can add, remove, or even duplicate components in an infinite number of configurations. You can have multiple panels, with different plugins on different panels, or maybe an identical second panel on a dual monitor setup. And did I mention that these panels nicely conform to the same theme as everything else? Or they could be different -- if you want that *My Little Pony* screencap as your panel background, there's nothing stopping you!

The actual "window manager" portion of Xfce gets similar treatment. Colors, buttons, handles -- everything can be changed and themed. 

It all looks very, very slick when put together with a nice theme and icon set (and good fonts with the right aliasing settings), and has allowed me to poke around until I've got a desktop user interface that I'm actually (more or less) happy with. This all seems like an evolution of my tendency towards endless tinkering on my [World of Warcraft](http://www.worldofwarcraft.com) UI.  

####Not all roses
Xfce has it's quirks too -- like why bother with an `Appearance` settings dialog if the appearance settings are _actually_ going to be scattered in at least 3-4 different places. I see the ability modify the visual appearance of Xfce in `Appearance`, `Desktop`, `Panel`, `Screensaver`, `Window Manager`, and `Window Manager Tweaks` (Compositor settings). Don't get me wrong -- I _like_ the fact that Xfce (and Linux in general) is modular. I understand that these components and their accompanying settings dialogs may stand alone from each other, which may also justify a sometimes-awkward organization of configuration elements. But I can also acknowledge that it could be better.

####The ugly
In the process of ripping out Unity, Gnome, and all of their required/recommended packages, I also (unintentionally) removed my [display manager](http://en.wikipedia.org/wiki/X_display_manager_%28program_type%29)(DM) and [greeter/login](https://launchpad.net/unity-greeter) screen. 

Now technically it's not necessary to have a DM. I could just boot to the command line, log in, run `startx` and go from there (see [here](http://www.tldp.org/HOWTO/XWindow-User-HOWTO/cli.html) and [here](http://docs.xfce.org/xfce/getting-started#getting_started) for background and instructions). Still, even for a guy like me who loves his CLI, having a nice GUI login and the desktop environment fire up automatically is just a matter of efficiency.

So there I was, no DM, no way to graphically log in. Just a big fat error message. `Ctrl+Alt+F1` to the rescue... took a few minutes to make sure I had [LightDM](http://en.wikipedia.org/wiki/LightDM) and dependencies all installed (I can't remember if I had to actually re-install anything there or not), and then another quick `sudo apt-get install`  and I grabbed the Webkit greeter for a lightweight Gnome-free graphical login. No specific reson for Webkit -- it was just the first one I stumbled across that was clear of the dependencies I wanted to avoid, and looked lightweight, so it got installed.

Conclusion
---
I like Xfce. I will probably continue to use it in the future -- or at the very least I will probably never install a Unity desktop again. I might try playing around with [Manjaro](https://manjaro.github.io/) or [Xubuntu](xubuntu.org/) in a VM and maybe wipe/reinstall my thumbdrive (hell, maybe install to a permanent partition on my laptop) if I actually like one of them. Or I could go whole-hog and continue with that Arch Linux build I started...

> Written with [StackEdit](https://stackedit.io/).