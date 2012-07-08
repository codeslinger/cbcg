--- 
title: ruby-epoll update
layout: post
---
Two things:

1. ruby-epoll is now hosted on [RubyForge](http://rubyforge.org/projects/ruby-epoll). Thanks to the RubyForge guys for hosting this project :)
1. I released another [alpha of ruby-epoll](http://cbcg.net/code/ruby-epoll-ALPHA002.tar.bz2) last night. This release cleans up the handling of the fd->IO map and also hooks epolled IO objects to do automatic cleanup when the IO is closed.

Big shoutout to [Why the Lucky Stiff](http://redhanded.hobix.com/) for writing the YAML libraries in such an instructive manner ;-) Speaking of that, Why, do you know that you're YAML::Syck extension is the only thing in the standard distro to use the rb_define_attr() function? (1.8.3)

I should have some tests and documentation up within a day or two and a beta release out shortly after that. I would like to get some outside testing of this library once that happens, to work out any major bugs or kinks. If anyone's interested, just send me email with your results/questions/comments. I will probably also start a mailing list for this project on RubyForge once I publish the first beta.
