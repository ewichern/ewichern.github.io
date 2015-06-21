---
layout: post
title: Let the spam begin
date: '2015-03-27 16:09:26'
---

I added [Disqus](http://disqus.com) comments to the website today. It was relatively easy to do. See:

* http://support.ghost.org/add-disqus-to-my-ghost-blog/
* https://help.disqus.com/customer/portal/articles/565624-adding-comment-count-links-to-your-home-page
* http://blog.christophvoigt.com/enable-comments-on-ghost-with-disqus/

I followed the guides in these links, and won't write another "how-to" because there's no reason to duplicate what has already been well (and clearly) documented. 

I will, however, *add* one or two things to these instructions.

First - The code for comment count links needed to go in `/var/www/ghost/content/themes/casper/partials/loop.hbs`, not `/var/www/ghost/content/themes/caster/index.hbs` as was described in a couple of the guides above -- I think one did get it right, or I found it in another blog/how-to via google, but no matter, it works now!

Second - if you follow these instructions, the Disqus comment area will probably not be styled appropriately since the `<div>` tag in the provided code is not assigned a class (and even if it were, that class might not be present in your stylesheet). So when you insert the actual comment system code in `post.hbs`, change `<div id="disqus_thread">` to `<div id="disqus_thread" class="whateverYouWant">`. Then edit `/var/www/ghost/content/themes/casper/assets/css/screen.css` and add a `.whateverYouWant` section with some appropriate style elements to format the comments section. Personally, I just copied the formatting for the `.post` element from the stylesheet and pasted it into a new `.comments` element.

Those things done, reboot ghost (`service ghost restart` works on my DigitalOcean Ghost droplet -- not sure if that works elsewhere) and things should all be working. It was very easy. I'm sure within hours my blog will be swimming with offers to buy viagra from online pharmacies and $0.99 iPad knockoffs from lolauctionbay.com.