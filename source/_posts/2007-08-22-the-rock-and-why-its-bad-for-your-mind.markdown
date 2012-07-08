--- 
title: The Rock and Why Its Bad for Your Mind
layout: post
---
It would seem that Sun's new chip, dubbed the Rock, [will support hardware extentions for software transactional memories](http://www.theregister.com/2007/08/21/sun_transactional_memory_rock/).

I tend to think of this as not such great news.

Now, I'm all for helping programmers in their work (being one myself) and making it easier to work with the parallel systems coming down the pike. However, I don't see hardware [STM](http://en.wikipedia.org/wiki/Software_transactional_memory) support as a big step forward.

I do realize that people don't change overnight and that all of that legacy code can't be rewritten in a flash to take advantage of the newer, better ways always being introduced. I also realize that Sun is making the right business move in allowing their customers to "port" their code to these more parallel machines with the minimum of effort. That's all well and good and I applaud them being the first to market on this, both from a business and a technical perspective. I'm sure it wasn't an easy task, what they did. But making a big deal of this advance belies the ultimate truths involved here.

Its no secret that I'm a fan of message-passing concurrency in general and [Erlang](http://www.erlang.org/) in specific. I believe that this is the way to go for the industry going forward. You are free to disagree, but I feel that MPC is a safer and cleaner way to go forward for the future of the industry. It removes a lot of the issues that are still problems with STM, just hidden so that only the VM and compiler guys have to worry about them. (at least initially) Not that it doesn't introduce some of its own, but I find these to be preferable to the alternatives.

However, in the end, using STM doesn't force programmers to write concurrent code. They are not thinking concurrently, only thinking about what to mark as _atomic_. This is still sequential programming. People using SQL have been thinking this way for years and I'd hardly call it concurrency-oriented. Raise your hand if you've worked on a project where someone kills database performance with some poorly-written transactions. All hands up?

We're just going to have to go through this again later when the STM abstraction starts falling apart. Optimistic concurrency (the underlying premise of STMs) is only as good as the care taken to prevent lots of and/or many long transactions. Without this care, performance will suffer both in speed and concurrency. It is, after all, optimistic. Optimism just doesn't seem to scale.

You can argue that the best programmers will do this beautifully, and I agree. But how many of us get to work with the best programmers? How many more of us have to deal with a bunch of code written by people who couldn't wait to jump in their cars at five o'clock? To me, message-passing concurrency solves this problem in a more direct (if more initially brutal) method: it just plain forces the programmer to think concurrently. That's the real key. Don't mask it, make them face it.

STMs are essentially a stop-gap measure to stem the pain coming from the rise of multicore. But, like any drug, the effects will wear off and that pain will be felt. By using STMs, you're borrowing from the future. Personally, I would think it better to just rip off the band-aid now and start learning and using the message-passing concurrency mindset today.
