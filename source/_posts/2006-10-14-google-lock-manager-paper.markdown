--- 
title: Google Lock Manager Paper
layout: post
---
Google published  a paper on their [Chubby lock manager service](http://labs.google.com/papers/chubby.html) in preparation for OSDI '06. The most interesting thing about this paper is the [Paxos](http://research.microsoft.com/users/lamport/pubs/paxos-simple.pdf) algorithm for distributed consensus. I do agree with [Greg Linden](http://glinden.blogspot.com/), in that the tone of the paper is somewhat derogatory towards other Google programmers. Perhaps this is an indication of the culture loss that comes when you grow too large, too fast?

_UPDATE: I saw the presentation of this paper live at [OSDI 2006](http://www.usenix.org/events/osdi06/).  Turns out that Mike Burrows is British and the tone of the paper was just some self-deprecating British humour for us ;)_
