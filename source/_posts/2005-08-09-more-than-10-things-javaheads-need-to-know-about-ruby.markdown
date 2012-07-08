--- 
title: More Than 10 Things Javaheads Need to Know About Ruby
layout: post
---
I recently got to read [Ten Things a Java Programmer Should Know About Ruby](http://jimweirich.tadalist.com/lists/public/14055) that everyone's been linking to lately. As someone who knows Ruby well and uses it everyday but also comes from a Java background ([VU](http://www.villanova.edu/)'s whole CS curriculum went to Java the year I started), I was amused at the kinds of things that I now take for granted. However, I have some comments that might clear things up for Java programmers even further.

_Boolean methods end in ?. Dangerous methods end in !_

What he means here is that methods ending in '?' are used as conditionals and methods ending in '!' modify the receiver.

_you can fit in your mind and write code without looking at the docs every six minutes_

This is the foremost reason to learn Ruby. Only Lisp is simpler in terms of core language to keep loaded in Mental RAM&trade;.

_Discipline. Because of its inherent flexibility, Ruby require more self-discipline_

A lot of vendor-loving Javaheads will not enjoy this at first, because their normal bouts of writers block staring at that blank file will be worse since there are many more ways to get things done in Ruby.

_Everything is an Object_

Despite what you've read, this is not true of Python.

_Ruby has O/R mappers, so find your Ruby "hibernate", but drop any preconceptions._

[Rails](http://www.rubyonrails.com). Nuff said.

_Enjoy closures and blocks_

These are extremely powerful and useful constructs that are totally missing in the C-inspired world. Anyone familiar with Lisp or Smalltalk knows that these are like your first car: once you start driving, you can't go back to riding your bike to get around and places you could never go before are now just a short trip away.

_No method overloading_

Don't worry about this: what you _can_ do is better.

_Don't worry about interfaces, enjoy Duck Typing._

Duck typing is a phrase bandied about the Ruby community which basically means that if it walks like a duck and talks like a duck, then its a duck, regardless of what it really is. Going further, having an object that responds to a method is all you need: if you have an array of objects that all respond in the same fashion to the "append" method, why would you care what class they are? This is the core idea when people are talking about Duck Typing, but [Programming Ruby](http://pragmaticprogrammer.com/titles/ruby/index.html) has a very enlightening chapter on the subject.

_Reflection in Ruby is much easier than in Java, and more deeply into the language than the java.lang.reflect tack-on._

You won't really get the benefit of this until you get deeper into the dynamic language mindset (I didn't), especially considering the butchering that Java does to the concept. However, this, like closures, is a big productivity booster, as well.

_local_variable, @instance_variable, $global_variable, Constants, (and @@class_variables)_

This may seem ugly at first, but you will get used to it quickly and just as quickly learn to appreciate the mnemonic hint that you are given when reading others' Ruby code. Similarly, Python's mandatory whitespace stance puts a lot of people off at first, until you realize that because of that stricture, it is nearly impossible to write Python code that someone else who knows Python can't read.

_you can have variable number of parameters, and multiple return values_

This will really kick your ass at first, especially when trying to read some non-trivial Ruby code. The power it brings more than makes up for it.

_REXML vs. JAXP. I rest my case._

REXML is Ruby's ultrasimple XML parser library, now standard with the inception of 1.8.x. While I've never used JAXP, I have used Java and can therefore guess that its nowhere near as easy to use as REXML.

_you cannot rely on the compiler to catch trivial mistakes_

On the other hand, you'll be writing far less code, so there will be far less of those mistakes to catch.

_ruby has shortcuts for accessor methods which reduces alot of redundant coding in java_

Beans... pheh. Try this:

``` ruby
class JavaBean
  attr_accessor :x, :y, :z
end
```

I've just created a class called JavaBean with three instance variables, x, y and z. The use of 'attr_accessor' there means that they all have getter and setter methods automatically. See a constructor anywhere? ;-)

_Ruby classes are always "open"._

This means they can be extended (methods added, variables added, etc) at any time.

_C extensions/wrappers are *much* easier in Ruby than JNI interfaces in Java_

How very, very true this is. C extensions in Ruby are so simple they make you want to write one... on the other hand, you get pissed at Sun when you have to write one for Java.

_In Ruby data is strongly typed, but variables are *not*_

This is a very important thing to keep in mind when learning Ruby and will help you muddle your way in from Javaworld.

_ri is your friend. irb is your other friend._

ri is the "man page" for Ruby, if you will: a command-line Javadoc, if you won't.

irb is the read-eval-print loop for Ruby, one of the things that makes Lisp so fast to code in. Ruby fully exploits its interpreted nature whenever possible to save programmer time.

_the builtin classes are much faster because they're written in C and not Ruby_

This always bit my ass and was the reason I always used the IBM JDK.

_method_missing_

Attempting to call a method that doesn't exist in Java will get either a compiler or runtime error, depending on whether or not reflection was involved. In Ruby, you can define a method called method_missing and do something intelligent when this happens (e.g. a default method for a particular area of code, containment in an app server, etc).

_It's super productive (like Perl, Python and Smalltalk)- maybe 5-10x Java._

This claim is highly-dependent on how productive you are in the first place.

_HEREDOC strings with variable interpolation make large chunks of output really easy to construct._

I use this all the time; very handy.

_Secure_

I believe he was referring to no buffer overflows here, but Java is the same kind of "secure" in that sense.

Why are you still reading? Jump on over to [Ruby's home page](http://www.ruby-lang.org/) and get started with Ruby!
