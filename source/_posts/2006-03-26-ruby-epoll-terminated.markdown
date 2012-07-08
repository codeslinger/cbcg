--- 
title: ruby-epoll terminated
layout: post
---
The [ruby-epoll](http://rubyforge.org/projects/ruby-epoll) project has been terminated. Due to the current state of Ruby's internals, there is no way to implement the desired functionality without constantly conflicting with Ruby's use of select(2) everywhere. Zed hit the same problem when he tried to write [Ruby/Event](http://www.zedshaw.com/projects/ruby_event/), a wrapper for [libevent](http://monkey.org/~provos/libevent/) for use with Ruby. A shame. I might try again when [Rite](http://www.rubygarden.org/ruby?Rite) hits.
