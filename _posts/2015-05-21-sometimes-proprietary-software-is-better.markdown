---
layout: post
title: Sometimes proprietary software is better
date: '2015-05-21 18:45:22'
---

#### The situation
I've been working on my [résumé](https://dl.dropboxusercontent.com/u/99151/ErikWichernResume.pdf) as I work on my career transition into software development. I already (in the last several months) have put together something decent-looking -- especially in comparison to the 5-year-old abomination that was my original source material. However, I wanted to kick it up another notch and add some additional focus and visual appeal to the document. Of course, whether the end result succeeds or not may be up for debate, but that's not what this blog post is about.

#### LibreOffice is good at most things...
This blog post is about [LibreOffice](https://www.libreoffice.org) (or [OpenOffice](https://www.openoffice.org/) if you're still using things from 2010). LibreOffice is great. It's [free (speech + beer)](http://en.wikipedia.org/wiki/Gratis_versus_libre), implements [standards-based document formats](http://en.wikipedia.org/wiki/OpenDocument), and generally does most of the *essential* things you might want from an office suite. Note my emphasis there. 

What LibreOffice does not do very well are lots of fancy things that [Microsoft Office](https://products.office.com/en-US/) has been doing for 10+ years. Two examples:

* embedding audio files in powerpoint presentations - I've needed to do this for several classes during my academic career, and tried to find a (not-completely-shitty) way to do it in LibreOffice. I could not find a suitable method and ended up paying for an Office365[^n] subscription.
* Trying to create a colored background for the header of my résumé. This should not be a hard thing to do. 
	* Word will let you change page backgrounds and header backgrounds -- though header backgrounds don't go flush to page edges in Word either. However, it's much easier in Word (and functions as expected) to just create a text box with a background color and drag its borders to the edges of the page.
    * The same effect in LibreOffice requires creating a frame object and modifying a bunch of properties so that it properly extends to all the edges of the page, and then creating a table inside of the frame so that the margins match the rest of the page... So it's possible, it's just a pain in the ass.
* Something so simple as a horizontal rule... In Word you just insert and then choose a style for the line. In LibreOffice the best "solution" for this scenario requires that I futz around with paragraph styles on a block of whitespace and have to use a "border" element to create a decent looking line.

#### Conclusion
* The first takeaway is that ideological positions get tossed to the wind when I have an looming project deadline and the tools I have to work with aren't cutting it. Then I just need shit to work and as long as the tool wasn't built by children in [sweatshops in Malaysia](http://en.wikipedia.org/wiki/Zoolander#Censorship), I'm probably ethically comfortable with my choice.
* I would prefer if I could have a union of "all the things I need working all the time" and "this aligns with my ideological beliefs", and as an adult who is not broke, am possibly willing to pay for products that satisfy these criteria. Disclosure: I have not donated to the [The Document Foundation](https://www.documentfoundation.org/), so it's possible I'm part of the problem and if they had more money their "product" would meet my needs better. Chicken or the egg problem? `vOv` Doesn't really matter, because I use Google Docs/Drive 90% of the time anyways, and I'm not particularly inclined to donate when LibreOffice is 50% frustration when I do need to use it for anything beyond the most basic document editing.
* And finally, now that I'm more comfortable with Java, ranty posts like this make me feel like I should go take a look at the LibreOffice issues tracker and see if I can help out...[^n] 

######Notes
[^n]: I got a month free the first time I needed MS Office (some promotion/trial), and then the second time I needed it, I just shelled out the $70-80 for a 4-year academic license. $20/year isn't worth my time to troll around for hack solutions to LibreOffice shortcomings.
[^n]: This is going to be my life from now on, isn't it? I don't just get to be an annoying user who complains about software. At least as far as [FOSS](http://en.wikipedia.org/wiki/Free_and_open-source_software) is concerned, if something doesn't do what I want it to do or work quite the way I want it to work, the answer is always going to be "stop fucking bitching and fix it yourself!" Sigh.