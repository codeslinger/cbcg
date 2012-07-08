--- 
title: ruby-sendfile 0.0.1 released
layout: post
---
I just released the alpha tarball of [ruby-sendfile](http://cbcg.net/code/ruby-sendfile-0.0.1.tar.gz). The package gives you an interface for Ruby's IO class to use the sendfile(2) system call on Linux, FreeBSD and Solaris. (not tested yet on Solaris, but should work)

By interfacing with the platform's native sendfile(2) system call, ruby-sendfile provides a "zero-copy" way to transfer the contents of a file to the network. In this case, "zero-copy" really means as few copies as is possible.

Here's a contrived example to bore you:

``` ruby
require 'socket'
require 'sendfile'

File.open("sometextfileinthisdir") do |f|
  TCPSocket.new("yahoo.com", 80).sendfile(f)
end
```

This will send the contents of the file _sometextfileinthisdir_ and send it to Yahoo!'s webserver. This will, of course, produce an error since what is in the file _sometextfileinthisdir_ will probably not be a valid HTTP request, but hey, it got there, didn't it?

I would appreciate someone giving this a go on Solaris and seeing if it blows up or not. Thanks.

__P.S. I already know that there was a project also called ruby-sendfile on RAA, but its dead like Max Headroom, so I'm using the most obvious name for the project.__
