--- 
title: "Python up, Ruby down: If that runtime don't work, then its bound to drizzown"
layout: post
---
This past week, I switched from programming in [Ruby](http://www.ruby-lang.org/) to programming in [Python](http://www.python.org/). Why did I do that? Well, that's a story with a bunch of background.

Coming to bat
-------------

I started playing with Ruby in 1999-2000 at [Villanova](http://www.villanova.edu/) for small stuff. I had read that seminal Dr. Dobb's article by the PragProg guys. I bought the first edition of the Pickaxe book and then had to buy it again after I destroyed it from reading/referencing it too much. At one point there, I was running the first FTP mirror for the Ruby sources in the Western hemisphere. I also met [David Black](http://dablog.rubypal.com/) way back in 2001 at a Ruby Tuesday's (pun intended) in Trenton back when he was still a Communications professor at [Seton Hall](http://www.shu.edu/) and I was still a college student. That was the only meeting of the "East Coast Ruby Users Group" ever held.

I thought Ruby had a lot of really cool concepts in it. (built-in coroutines, true OO, closures, heavy-duty metaprogramming, etc.)  I also had little experience with Perl so I didn't appreciate how similar they were. Villanova was a Java school and Ruby was like a real breath of fresh air compared to the Machiavellian verbosity imposed by that language. I was really just struck with the compactness of the language and how much you could pack into a very short amount of code.

Strike one
----------

After school, I got an internship then real job with a local startup working in the now-hot email reputation/authority space. [My boss](http://www.brussin.com/) there was also a Ruby fan and recognized its ability to really pound out some serious stuff in a very short amount of time. This is something you require in a startup situation.

We were using Ruby as a systems administration glue language at first here and there, but when we started building the [SpamSquelcher](http://loosewire.typepad.com/blog/2004/07/symantec_quietl.html) prototype, we decided to use Ruby for its Web interface. We chose what was basically the only option for a Web framework at the time in Ruby, a compact MVC piece called [Roach](http://raa.ruby-lang.org/project/roach/). Now that I go searching for the URL for Roach, I can see that it hasn't moved even a patch ahead of where it was since we started using it. Funny. I think maybe [IOWA](http://enigo.com/projects/iowa/tutorial/what_is_it.html) was out at the time, too.

Roach was supposed to be MVC, but the "M" part was lacking as it had no integrated database functionality. However, for our purposes (controlling an embedded appliance), this did not matter at all so we had no issue with this limitation. Development went quickly, but there was a nagging issue with a memory leak. Every hit to the app server would irrevocably raise its memory usage and nothing we tried ever made a big difference. We could see no problem with the Ruby code itself, neither ours nor Roach's, but there were no tools for diagnosing memory problems in Ruby apps. There still aren't any.

We eventually had to just ship it with a hard memory limit under [daemontools](http://cr.yp.to/daemontools.html) so that it would never chew up too much RAM on an appliance where RAM was already at a premium. So, when we became [TurnTide](http://www.turntide.com/) the interface was rewritten in PHP and one of the reasons for it was this issue. I never did figure out what the problem was, either.

Strike two
----------

So, later, a while after [Symantec](http://www.symantec.com/) had purchased TurnTide, I was looking at ways to process our very large amount of data from the [Brightmail](http://www.brightmail.com/) and TurnTide streams. While we didn't require anywhere near the truly massive powers that Google needs, I was (and still am) enamored by their internal architecture and sought to replicate that for our use. I didn't find out about [Nutch and Hadoop](http://lucene.apache.org/hadoop) until much later. So, I basically rebuilt all of the functionality of [Google File System](http://labs.google.com/papers/gfs.html) and their [MapReduce](http://labs.google.com/papers/mapreduce.html) framework in Ruby in about 5 weeks.

However, it never actually worked. The tests passed and the functionality was good, in terms of correct Ruby code, but the "chunkserver" nodes would very rapidly just start using all the RAM on the box and freeze up when the filesystem became even moderately loaded. I was not able to determine the cause of this issue at the time and the project was cancelled. I came to find out later [what its cause was](http://osdir.com/ml/lang.ruby.mongrel.general/2007-01/msg00033.html) but it was too late. This remains my only professional failure to ship to date.

Some light in this tunnel
-------------------------

It wasn't all bad. Most of the Ruby I was writing was working out fine. It was small scripts to do this or that and the productivity was great. Its especially awesome for text processing because its just as handy as Perl but more readable when you want to reuse a script six months later.

Also, I wrote a small [Rails](http://www.rubyonrails.org/) app to manage our PXE installations of appliances in a day that saved us all any more trips to the server room to reinstall a box. That was a big boost. Rails is pretty great framework and I wasn't even using it for the kind of thing it was designed for. (no RDBMS in my app)

Strike three; you're out
------------------------

Segue to this past week. I was writing a internal cross-platform utility to do some HTTPS communication and it had to run on multiple platforms, including Windows. Most of our people run Windows, so supporting this platform is a stone-clad requirement. I had finished the utility in a pretty quick amount of time and was planning on packaging it up for Windows with rubyscript2exe. However, when I started testing on Windows, I found that the program would just hang when it got to the final HTTPS request.

Turns out that the One-Click Installer version of Ruby on Windows has a known (!!) problem with combinations of Ruby threads and I/O. Given that the net/protocol.rb library that underlies all of Ruby's standard Internet protocol functionality wraps most calls in a Timeout::timeout() call and that call is implemented with a Ruby thread, the problem seemed pretty large. But, I found a post denoting the problem and indicating that Ruby built under [MinGW](http://www.mingw.org/) did not exhibit this issue.

I think, if you've read this far, that you can probably tell that it, in fact, does exhibit this issue. Both the binary package I downloaded (ruby 1.8.4) and the one I built from source under MinGW/MSYS (ruby 1.8.6). I [posted to ruby-talk](http://www.ruby-forum.com/topic/105212) about it, citing the hope-rendering link from ruby-talk about MinGW.

Enter the Python
----------------

At this point, I was looking at having to do some serious Ruby internals hacking on a platform that I know little to nothing about or rewriting the utility in a different language. I was T minus 2 days to deadline. I chose the latter and was able to rewrite and finish the whole thing in Python in a day and a half without ever having touched Python before.

Obviously, most of the speed of this rewrite was due to the fact that I was merely porting it to Python from an existing Ruby implementation. I am not making any claims of Python having greater productivity than Ruby in the development cycle. I am claiming two things, though:

1. Python was very productive, despite having never used it before, and
1. The end result actually fucking worked

That last one is kind of big with me.

Python? Really?
---------------

I had given some thought to doing the rewrite in Perl but two things stopped me from going that route. I really did not want to have to support any Perl code over any length of time as it really (to me) is a butt-ugly language and is mnemonically taxing. Also, the [perl2exe](http://www.indigostar.com/perl2exe.htm) compiler to produce Windows executables costs money. Python has the [py2exe](http://www.py2exe.org/) package that did the job very nicely and is free. C was obviously out due to time constraints even though I know that language better than any other.

Plus, Python seemed a more natural fit for a port from Ruby as I knew it contained most of the high-level constructs I had come to love in Ruby. There was only one function that I had to truly rewrite due to Python's lack of "blocks", or one-way coroutines. 

I had heard at some point in the past that Guido was planning on getting rid of the map(), filter() and reduce() functions in Python 3000 and always wondered what he would want to do that for. Now I get it: Python's [list comprehensions](http://www.network-theory.co.uk/docs/pytut/ListComprehensions.html) can perform all of those jobs in a natural syntax. 

The regular expression support is not as natural as Ruby's or Perl's but its not significantly more verbose or hard to work with. 

My only beef was the lack of YAML support in the Python standard library, but I was using YAML in Ruby for a configuration file and Python's [ConfigParser](http://docs.python.org/lib/module-ConfigParser.html) turned out to work just fine in its stead.

One thing Python has all over Ruby is documentation. I used the Python docs from python.org almost exclusively and that was good enough to get the job done. Their documentation is first-class and this is an area where Ruby knows it needs to catch up.

And, there are a bunch of things available to a Python guy that Ruby just can't compete with that are of particular interest to me. Two that come to mind immediately are [Twisted](http://twistedmatrix.com/trac/) and [Stackless Python](http://www.stackless.com). The former was used by others at TurnTide for creating a really powerful SMTP testing tool and the latter was used by TurnTide's competitor [IronPort](http://www.ironport.com/) to build one of the industry's best MTAs. 

Along this same vien, I had previously tried creating a binding for [Linux's epoll(4) facility for Ruby](http://cbcg.net/blog/2006/03/26/ruby-epoll-terminated/) but was stymied by Ruby's internal workings. A [far better programmer](http://www.zedshaw.com/projects/ruby_event/index.html) than I also fell victim to this same issue.

The Fundamental Issue
---------------------

In case you somehow missed it, the fundamental issue above in all three of the problems was the Ruby runtime. I have no qualms with the language and I think its got tons of great things going for it. However, the runtime sucks. I've said this privately for some time but now I'm going on record.

The community seems to realize this and is moving in a number of different directions, most notably the YARV runtime. However, I fundamentally disagree with this direction. YARV will remove two of the awesome features of the language, continuations and green threads, and it will *keep the same GC model*. This makes no sense to me, as the GC is clearly one of the weakest parts of the current runtime. As well, [Erlang](http://www.erlang.org) and Stackless draw their powers from *NOT* supporting native threads as part of the language and they are far better suited to the future of heavy concurrency than Ruby. [Rubinius](http://blog.fallingsnow.net/rubinius/) is far more interesting to me but they have a much longer climb up the hill towards usefulness.

What about the Twitter phenomenon?
----------------------------------

Some might say that I should have [stepped up and fixed the issues](http://www.loudthinking.com/arc/000608.html) I was having and not just complain about them on my blog. To them, I'd say that in the first two cases I tried and in the third I didn't have the time. I'm not taking a "wait and hope" attitude like some others, hoping that someone else will fix my problems. I'm circumventing them altogether. Above all other things professional, I have a job to do and employers to report to.

And furthermore, for me, programming languages and their runtimes are tools. I think they are for a lot of us. You wouldn't continue to use a hammer whose head keeps flying off when you take a swift backswing, would you?

So, no more Ruby? Really?
-------------------------

I will probably still fall back on Ruby for text-processing scripts as its always been stellar for those kinds of tasks. But, I have to say that any real software I write will no longer be in Ruby for the foreseeable future. I am discounting Rails here: I think Rails is great for what it is and I've had nothing but good experiences with it precisely because it is so "opinionated". Its a very productive environment and manages to successfully avoid the runtime problems that I've personally hit in the past. I hope that the Ruby community can really bang out a worthwhile runtime in the coming year and if they do, I'm back on board. If I get some time, I might even help out where I can.

For now, though, I am looking forward to using more and more Python and getting to know that language, as well as some Erlang in there somewhere, too. I have the beta of the new Armstrong book and am tearing through it with the same rapaciousness as I did the first edition of the Pickaxe.
