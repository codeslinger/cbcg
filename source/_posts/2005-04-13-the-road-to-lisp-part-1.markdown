--- 
title: The Road to Lisp, Part 1
layout: post
---
Last weekend I was reading some [Paul Graham essays](http://paulgraham.com/articles.html) and I came across [this one](http://paulgraham.com/avg.html). I had read some endorsements of Lisp in the past, and even came across a professor or two who had a great love for Lisp (I'm looking at you, [Frank](http://www.csc.villanova.edu/faculty/facultyDetail.jsp?id=frank.klassner@villanova.edu)). I didn't really like the look of the language, and was frankly more enticed by lower-level systems programming at the time to seriously consider learning it. We dabbled in functional programming languages in our PL class, but that also didn't do much for me; actually, Prolog was more intriguing at that time because the project for that was writing a text adventure game. 

I also didn't fully understand the concept that all Turing complete languages aren't equal, with respect to concise expressiveness. I do now, as I am a huge fan of the [Ruby](http://www.ruby-lang.org/) programming language. Paul convinced me that I was missing out on something by not knowing Lisp, so I jumped online and grabbed a used copy of [ANSI Common Lisp](http://paulgraham.com/acl.html), which arrived today. I don't think I'll mind all of the parentheses that much, since I've already learned from the mistake of judging a language by its syntax with Python. I cracked it and started reading a bit and it seems pretty good so far. There's a lot to Lisp that's intriguing and elegant.

For example, here's an example from the introduction. This function will take a number _n_ and returns a function that will add _n_ to its argument.

``` common-lisp
(defun addn (n)
    #'(lambda (x)
        (+ x n)))
```

Read that sentence above again: this function _returns a function_. This is not expressible in C, C++, Java, etc because those languages don't have support for lexical closures (Ruby does, though). Closures are hot; I can't wait to get to macros ;-)

I don't know enough about Lisp yet to say if I'll like it enough to use it a lot, nor whether or not it will replace Ruby as my favorite language of late. But, I figure that if its got a chance to make programming even more fun and fast than Ruby can, its worth a shot. I'll be chronicling my journey here when something interesting or cool comes along during the process. It will also keep me reading and coding so I can put some observations up here (for all three of you reading).

On a more ironic note, the Mac's in my house now outnumber the Linux boxes, I use a PowerBook running Panther at work and I'm learning Lisp. Cheers, Dr. K.
