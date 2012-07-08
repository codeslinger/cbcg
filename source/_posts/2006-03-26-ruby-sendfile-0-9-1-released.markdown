--- 
title: ruby-sendfile 0.9.1 released
layout: post
---
Just released version 0.9.1 of ruby-sendfile. A lot of changes:

* Added README and Changelog
* Added full test suite
* Works equally well now with blocking and non-blocking sockets
* Passes all tests on Linux (x86 and AMD64, both 2.6.x) and FreeBSD.
* Packaged into RubyGem, available on Rubyforge.org

Check out the [main project page](http://rubyforge.org/projects/ruby-sendfile) for files and forums and such, or just 'gem install sendfile' to get started using it. It should autoinstall the rdoc action (ri IO#sendfile) to see how to use it.

To get to 1.0, I will either test or have someone else test on Solaris, although it should work on Solaris as is. As well, I am thinking about allowing you to pass a file path instead of an open file as the first argument and just having the library open and close the file for use with sendfile(2). Also, I might allow you to pass a Range as the second argument, instead of having to use the offset and count parameters. Finally, I might investigate what it would take to support TransferFile() on Windows, but don't anyone hold their breath. I will accept patches, however.

With luck, Zed might use this in [mongrel](http://mongrel.rubyforge.org) to really speed up static file transfers.
