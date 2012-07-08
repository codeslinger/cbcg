--- 
title: Web shells clean better than SOAP
layout: post
---
There seems to be a rash of these Web-based shells and command line interpreters lately. I found three of them so far, two that hit [del.icio.us](http://delicious.com) today:

* [JS/UIX](http://www.masswerk.at/jsuix/) - really, really high on the cool factor
* [WebCmd](http://a-i-studio.com/cmd/) - not as cool as JS/UIX, but interesting in that it embraces its HTML roots more
* [Yubnub](http://www.yubnub.org/) - named after the Ewok sound

WebCmd is based on AJAX and the author's own XMLHttpRequest wrapper library, which seems to be all the rage right now. JS/UIX is even cooler for not using AJAX (it was written before the current interest in such); it seems to be completely client-side JavaScript.

Yubnub is a little different than the first two. Its a simple site that allows you to enter a human-created command into an input box and be redirected to the results. For example:

![Yubnub command line](/images/yubnub001.png)

This is a command line to look for pictures of the US Open 9-ball tournament. 'gim' directs the query to Google Images search; the rest of the command is the search query to be passed to Google Images. All of Yubnub's commands are like this.

Users can make a new command at will on Yubnub. All they need is a name for the command, the URL to use in the redirection and optionally comments as to how to use the command or what it does. The Yubnub service is pretty simple from there: you just type in one of these commands and some terms after the command (optional; some commands don't need them) and hit Enter. Yubnub resolves the command to the URL that maps to it, inserts your arguments in the URL where the command author put the '%s' sequence when the command was created and your browser is then redirected to the finished URL. Very simple and very useful... 

...potentially. I could definitely see putting a little input box at the top of my screen, accessible from a hotkey, for this very sort of thing. Having a commandline-esque interface to the Web is a very powerful idea. Yubnub is even talking about doing pipelines in the future, which would basically geometrically increase the power of the Web. I'm sure you can all think of examples of pipelines you'd want to run if you could... At any rate, given this run of services like this lately and the potential power of Yubnub, it occurred to me that SOAP was supposed to be the protocol for doing this sort of thing. It might even be the thing that eventually makes a 'Web pipe' possible. 

But the simplicity of these shell services is too intriguing to ignore. I'd be much more inclined to script some commands for a Web-based shell to grab some quick results than to learn a bunch of SOAP specs and try to ram them together (and probably still not get what I really wanted). By the same token, a simple and clean command interpreter engages people to more freely experiment with the exported services of a particular Web application or series of applications. How many casual UNIX users can put together a shell script to perform some simple task? How many of those same users would dive deep into some Javadocs for a few hours to decipher a SOAP interface to perform the same task?

For Yubnub, in particular, I don't think they can last as they are currently. They have two problems right now:

1. Anyone can make commands without even logging in
2. There's no way to find a command other than listing them all and reading the entire list

The first point is already yielding many repeated commands under slightly different names and also a bunch of junk commands that are little more than redirects, akin to a mnemonic version of TinyURL. This, however, exacerbates the second problem in that, since the only method of finding a command is to read through a list of them, the more commands there are, the worse off the average experience will be. This is not a problem without a solution, however. They can make some (implementing command completion and/or an apropos(1)-style command) and get this under control but also keep that del.icio.us-style community aspect. In any case, even if they go away completely, services like this will continue in some form because the benefits are too numerous and the model fits too well with what we're used to to give up on it altogether.

_UPDATE: Turns out that you can use the 'ls' command in Yubnub to search for terms in existing commands. That goes a long way towards the kind of discovery that I was referring to above. Kudos!_

_UPDATE: Well, apropos was a command in Yubnub two days before I blogged this..._
