---
layout: post
title: Vagrant and development environments
date: '2015-06-08 16:04:30'
---

Disclaimer: I am not an expert in this area. It's something that I would like to put into my workflow though, just as soon as I find the time to learn enough of the basics and get it set up.

#### Quick problem summary

Essentially, the "problem" to be solved boils down to this: Production environments for deployed software often don't precisely mirror the development environments that are used to write, update, or maintain the code. This problem manifests in a number of ways, but I'll generalized again with a suuuuper basic example. 

Say maybe I wrote some software that passed all my unit/integration/system tests in my development environment, but when I deploy to the production environment things go sideways and I'm faced with some gnarly errors/failures. Obviously there are a number of steps I would take at that point to rectify the situation, but those steps might make the problem even harder to solve. That is, if I have to roll back the production environment to maintain continuity of service, I now have no way to reproduce the error and do some debugging to figure out what's causing it -- unless I have a way to exactly mirror/reproduce my production environment.

Of course, if I _did_ have a way to exactly mirror or reproduce my production environment, well then I probably ought to be using that as my development environment in the first place. And in that case, I would have already discovered and fixed the fault, preventing my problem from ever happening in the first place!

#### Which brings us to VMs and Vagrant

So VMs are a thing. I've [mentioned](http://usingname.space/tag/virtual-machines/) them once or twice before in other, limited contexts. In fact, this blog is running on a VM somewhere in one of [Digital Ocean's](https://www.digitalocean.com/?refcode=0034f576b0ae) datacenters[^n]. And I hear that people *do* use virtual machines to maintain development environments without any fancy software to help smooth out the process. But this is 2015 -- we have [Vagrant](https://www.vagrantup.com/). 

I keep hearing how great this Vagrant thing is, not only for maintaining development environments, but also for deploying to production so that the environments are identical and all the hard work that went into an application doesn't get wiped out by the wrong version of PHP[^n]. However, to date I had not stumbled across a guide/article that gave me a good overview of what a workflow utilizing Vagrant actually looks like[^n]. Sure, *lots* of articles essentially describing the "Hello World" of Vagrant setups, but how does this thing work when rubber meets pavement?

So finally I got off my butt, put some proper search terms into google, and boom, relevant information. Amazing how search engines work better with better search input. `o_O` While not a tutorial, I found [this article](https://www.andrewmunsell.com/blog/development-environments-with-vagrant-and-puppet) particularly helpful as a description of how Vagrant integrates into a workflow and a (very) top-level overview of how a person might set up a development box for a project.

#### This post is (also) not a tutorial
Unfortunately I still haven't had the time to actually play around with this stuff, but I've been reading/thinking about it, and wanted to write things down while they were on my mind. The [examples](https://github.com/patrickdlee/vagrant-examples) that were linked from the Munsell article look like a good place to start, and my not-crappy search terms kicked up a couple other decent resources as well, so now I think I might have the framework for making this happen the next time I have some spare moments.

Last little tidbit: in the comments of that same article, someone asks one of the big questions I had about this whole concept (but thought was maybe a dumb question[^n]). 

> ###### Richard • 4 months ago

>This sounds great but where do you edit the code as you are developing?
Is it still done on your host machine then somehow deployed to the virtual machine?

> ###### Rizart Dokollari -> Richard • 4 months ago

>That's the beauty of it. You can edit your code from either your host or the virtual machine. You specify a folder which is shared from both the host the virtual machine. I really love it when I have to dev from Windows OS--I can easy ssh to a virtual machine containing Ubuntu and just use vim for coding. :P

I feel less like it was a dumb question since obviously someone else had the same question. However, I feel a bit slow for not realizing/remembering (having used [VirtualBox](https://www.virtualbox.org/) before) that shared folders would be an option and could be used to edit the project. Oh well. Now I have my answer and can put one of my hesitations about the Vagrant idea to rest!

I'll have more to say once I've got something set up so that I can test it out as part of my development workflow...

[^n]: side note: love them for hosting
[^n]: promise I'm not picking on PHP, just the first thing that came to mind.
[^n]: Admittedly, I really wasn't looking that hard
[^n]: sure, sure, "there are no dumb questions." whatever!