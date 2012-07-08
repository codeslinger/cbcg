--- 
title: Google AppEngine Thoughts
layout: post
---
I just read a little bit about the recent announcement of [Google AppEngine](http://code.google.com/appengine/) and I think its a pretty good service overall for certain kinds of Web applications. Unlike the rumors that were floating about prior to its announcement, its not a competitor to [AWS](http://aws.amazon.com) directly, nor even a competitor to [Ning](http://www.ning.com) as some have also claimed. To me, it seems more directly in competition with [Heroku](http://heroku.com/) if such a thing could even be said. It is clearly based on [Bigtable](http://labs.google.com/papers/bigtable.html), though, so that part of the rumor appears to have been true.

Being so simple has some advantages and presents some interesting constraints. Because you don't have root and can't run the "box" yourself, you're forced to think simply about the app itself. This seems as if it would be quite a welcome constraint for a lot of Web developers who don't care about running a network. But the constraint really serves to enable Google-style scalability at its heart. As well, the use of CGI allows Google to run your code wherever they deem it best at the moment underneath, without you having to care about that sort of thing. This is something they already do quite well.

As well, the lack of a traditional RDBMS is something that obviously works well in a shared-nothing environment and makes a lot of sense since Google's infrastructure is already based on such. This gives real credence to the idea that the RDBMS isn't the be-all-end-all and will introduce a lot of developers out there to this new way of thinking.

A few things I don't like:

 * Users of an AppEngine app must login with Google Accounts
 * You do have to upload your Python source to Google and this leads to obvious privacy and IP concerns
 * No recurring job scheduling (essential for lots of different kinds of apps)

One more obvious thing is that an application built on AppEngine is one that is much, much easier for Google to acquire than one that is not. Don't underestimate that piece of it, as its likely this service will be a loss-leader for Google.

Finally, I think this announcement will be very good for Python. As AppEngine only supports Python right now and for the foreseeable future, anyone interested in AppEngine will have to learn some Python. This will shed some more light on Python for people who might not have otherwise given it a try. 

*UPDATE:* Apparently, [others agree](http://staticallytyped.com/2008/04/08/googles-plans-for-app-engine/) about the acquisition potential of apps on AppEngine. Good stuff.
