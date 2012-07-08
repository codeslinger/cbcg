--- 
title: Evidence Based Scheduling
layout: post
---
[Joel Spolsky](http://www.joelonsoftware.com) has an intriguing new article on one of the new features in [FogBugz 6.0](http://www.fogcreek.com/FogBugz/) called [Evidence Based Scheduling](http://joelonsoftware.com/items/2007/10/26.html).

I've actually had some experience with parts of this technique before, as I used it on a project while I was at Symantec. In my estimation, the project went much better because of this technique, partly because of the much better granularity afforded by this technique and the constant feedback given to myself and my superiors.

I also felt much better about my progress, both because I was completing tasks much faster (since they were smaller) and I had a much better handle on the scope of each task. It also did force me to think about the implementation issues ahead of time, something that Joel mentions and I think  a lot of us gloss over and hand-wave away when dreaming up schedules and project plans. 

Credit goes to [Ross Fubini](http://www.linkedin.com/in/fubini) for being the first at [Symantec](http://www.symantec.com/) to implement this style of project management.

One thing we didn't do at Symantec was the the statistical dispersion of potential completion dates. Using a Monte Carlo simulation would indeed give you a much better feel for progress and allows for more realistic estimates of project health. We use statistical analysis at work quite frequently but it had never occurred to me to apply it to the software development process. Hindsight's always 20-20, eh? Kudos to Joel for having the insight to apply this technique to software engineering.

As I am now responsible for the delivery of commercial software, I look for things of this nature to aid in the day-to-day engineering of projects. Based partly on my experiences and partly on the elegance of the idea, I do believe that EBS is very valuable and those responsible for shipping software should give it some serious consideration. You don't even need FogBugz 6.0 to do it: an Excel spreadsheet or wiki software can be used to track the tasks and associated times and you can use [R](http://www.r-project.org/) to do the Monte Carlo simulations.
