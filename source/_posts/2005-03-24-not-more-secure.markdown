--- 
title: Not more secure
layout: post
---
This morning, [Microsoft sockpuppet Dave Massy](http://blogs.msdn.com/dmassy/archive/2005/03/22/400689.aspx) posted a reply to an article with Mitchell Baker regarding [Mozilla's security relative to IE](http://news.zdnet.com/2100-9588_22-5630529.html). I will reply to Dave's egregious misuse of communication inline.

> That's an argument we can spend a great deal of time on and still not prove one way or the other.

This is proven over and over again all the time. Count up the number of security holes that were/are in IE versus the number in Mozilla, weight them by severity and IE is a clear loser by any metric.

> Now I'm pretty confident that Mitchell doesn't actually know the details of how IE is developed so I don't fully understand the basis of the statement. As we develop IE we go through very thorough and stringent security reviews to ensure that every change is secure and does not expose the user to attack.

Who is this supposed to impress? The fact that Mozilla's process is open to world review is a tremendous advantage over the closed-source development model of IE. As well, since it can be reviewed by anyone, security holes can be fixed much faster than that of IE's, some of which are years old and will never be fixed, by Microsoft's own admission. This would never stand in the OSS community. Also, on that same note, how can we be sure that the process is "thorough and stringent"? It might just be a guy in a room going to Yahoo! and if that works, testing is done... we don't know. Finally, there cannot possibly be as many people reviewing IE's code as there are Mozilla's and therefore security bugs will be found quicker and fixed quicker than IE. Unless, of course, you open the source to IE...

> The security of any browser is irrelevant to if it is part of the operating system.

What? In fact that's extremely relevant. If Mozilla has a buffer overflow, it can't affect the video driver or USB subsystem, for example. This is because its a normal process, confined to its own address space and nothing more. If IE, on the other hand, has some kind of overflow or corruption issue, the potential exists for a massive stability or security problem because some IE code runs in a IA32 CPU ring other than 3. Exactly how is that not pertinent to a discussion about IE's relative security?

> If we are to debate security of browsers then let's bring in relevant arguments...

Yes, let's. That includes you, as well.

> ...and accurate details about different possible attacks rather than rely on the irrational fear that because IE is part of the operating system it must be exposing OS functionality to the web. This is not the case as any software has access to the same set of OS APIs and can therefore expose the same set of OS functionality as IE.

So, let me get this straight: your argument is, since you expose kernel functionality for browsers for everyone, but you're the only ones stupid enough to use them, somehow that's better? Exactly how does the above statement make any sense??

Dave, please, before you post next time, make sure you've read what you've written. Other people will if you don't and you'll get more of this type of response.
