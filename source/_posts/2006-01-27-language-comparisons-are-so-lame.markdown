--- 
title: Language comparisons are so lame...
layout: post
---
Yet [another mostly pointless language comparison](http://www.dmh2000.com/cjpr/index.shtml) using a single example that attempts to make some kind of conclusions others should listen to hit [Digg](http://digg.com) this evening.

From a Ruby programmer's perspective, I was a little upset that this guy clearly didn't know how to program, or at least use Ruby. So, I've taken the liberty of cleaning up the Ruby example and posting the [revised version here](http://cbcg.net/code/RedBlackTree.rb)

He made a claim that Ruby was the second longest example due to all the *end* lines. Here's the count using my updated version of his code:

``` sh
aluminum:~> grep -v '^#' *.py | wc -l
     213
aluminum:~> grep -v '^\/\/' *.java | wc -l
     282
aluminum:~> grep -v '^\/\/' *.cpp | wc -l
     325
aluminum:~> grep -v '^#' *.rb | wc -l
     170
aluminum:~>
```

P.S. Lazyweb, anybody know of a more idiomatic method of doing what he does with the copy method? I replaced some of his calls with Object#dup, but some were basically reinitalizing self, which dup doesn't do.
