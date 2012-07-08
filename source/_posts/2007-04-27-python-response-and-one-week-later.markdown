--- 
title: "Python: Response and One week later"
layout: post
---
My [last post](http://cbcg.net/blog/2007/04/22/python-up-ruby-down-if-that-runtime-dont-work-then-its-bound-to-drizzown) somehow managed to create quite a stir on [Reddit](http://reddit.com) and [Hacker News](http://news.ycombinator.com). This was not my intent, since I was pretty sure no one actually read my blog and this is the first of my articles to make it to any news distribution site. I'd like to take this opportunity to respond to some of the comments and also share some of my experiences with the first week of Python.

First of all, thanks to all the people with encouraging comments. I really appreciate all of the support as this was not a decision I made lightly. I have a lot of experience with Ruby and had a lot invested in it so moving to Python was a big thing for me.

I'd also like to respond to some of the recurring themes in the comments:

* As for my use of "stone-clad": obviously, that makes no sense unless you're talking about dinosaur fossils. Thanks for pointing that out. Doh!
* This somehow became a bone of contention on the Reddit comment forum: Ruby's blocks are, in fact, a form of coroutine. Please refer to [this page on coroutines](http://en.wikipedia.org/wiki/Coroutine) if you need some help with their definition.
* As for my like of user-level threads over native threads: This is a complicated issue, but I'd rather have the option of both than just one. Using a lot of cheap cooperative threads over a few native threads yields big scalability and performance and softens the blow of concurrent programming. If I had to choose one, I'd choose cooperative threads and just spawn processes to account for multiple cores. Check out how [Erlang](http://www.pragmaticprogrammer.com/titles/jaerlang/) does it to see why I prefer this mode.
* As for Python's whitespace: I tend to like it. It makes Python slightly more annoying to write, but I think it pays bigger dividends when it comes to readability. However, I may just be blowing smoke here since I've only been using it for a week ;)
* Some Perl people came to its defense in the comments. I don't begrudge you or anyone else their choice of language and I know some really great programmers that love Perl (big up, [MCT](http://michael.toren.net/)). Perl has a solid runtime, its very flexible and has a ton of good documentation and libraries that make it a real contender for almost any task. To them, I'd say that _I_ find it to be less than sublime to program in but I respect what can be done with if you're willing to put in the time to really come to grips with the language.
* Apparently, there are now tools to debug memory issues in Ruby, most notably [Rublique](http://rublique.rubyforge.org). Thanks for pointing those out.
* A filesystem can indeed be written in lots of languages that you might not think of since it will be I/O-bound most of the time. This makes raw speed of execution less important. Particularly in the case of a system like GFS where you have disk and network I/O that are sucking up the vast majority of wall-clock time. It may never be as fast as GFS or Hadoop, but it can work quite well regardless. I plan to redo that effort in either Stackless or Erlang at some point in the future.

And some specific responses:

* Fitzgerald Steele: You had me rolling on the floor laughing :) I wasn't sure anyone would get it :-P
* Matt S Trout: The Perl2exe that I was referring to was [this one](http://www.indigostar.com/perl2exe.htm) which doesn't appear to come from ActiveState. However, your point is well taken.
* n d: I never even got to the point of using rubyscript2exe. My tests exposed the issue on Windows before I even had the chance to try to package it into a Windows executable.
* winston: I'm pretty hurt. I pumped Rubinius in my post and I didn't submit this to any news site, nor did I expect anyone but a few friends to read it. As for your main point, I would prefer to use the Ruby _language_ for most of my stuff, but the _runtime_ beat up on me too many times.
* David: By your rational, we should all be using Algol or Fortran since they have *really* deep roots. Somehow, I don't see that happening.
* The guy on Reddit who said the title was a "like a textual goatse": That was even funnier than Fitzgerald Steele's comment!

I've been using Python for a little over a week now professionally and I've come to find out more about it. So far, its going pretty well. Some points:

* The [ZSI](http://pywebsvcs.sourceforge.net/) interface is not as nice as [SOAPpy](http://pywebsvcs.sourceforge.net/) when you just want to get something going. SOAPpy is really, really nice. Plus, the current version of ZSI (2.0) doesn't support SOAP headers which makes it pretty useless for real-world SOAP to a big, public API right now. If you have to work with SOAP, stick to Python <= 2.4.x as long as you can so you can keep using SOAPpy. 
* Python's object attributes seem to be somewhat lamer than Ruby's. Using `property()` and creating getter and setter methods is less handy-dandy than Ruby's `attr_*` helpers. This may not be required, but I don't know any better right now.
* The reference material says that the .pyc and .pyo objects created by a higher version should be importable by a lower version, but I've found this not to be the case.

That's about it for insights so far. I'm really liking it. I thought I'd miss some beats switching to Python but so far its been more than sanguine.
