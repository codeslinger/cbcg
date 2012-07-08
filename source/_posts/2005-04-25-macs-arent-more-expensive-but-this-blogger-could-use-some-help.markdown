--- 
title: Macs aren't more expensive, but this blogger could use some help
layout: post
---
I found a blog post today regarding [Macs not being more expensive](http://www.classic45s.com/blog/2005/04/of-course-macs-are-more-expensive_24.html) than the counterpart hardware running Windows. While the majority of the assertions in this essay appear to be within reason, there are some technical facts that are just plain wrong.

> Windows 32-bit chips can address up to 3GB of RAM, and though that seems like a lot, it's a puny amount compared with the theoretical 1,000GB capability of a 64-bit chip.

Negative.

```
aluminum:~> bc
bc 1.05
Copyright 1991, 1992, 1993, 1994, 1997, 1998 Free Softw...
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'.
2 ^ 64
18446744073709551616
. / 1024 / 1024 / 1024 / 1024
16777216
quit
aluminum:~>
```

That's over 16 million terabytes. I'm guessing that the author has not been introduced to exponentiation.

Second, Microsoft just today released [64-bit versions of selected Windows operating systems](http://www.microsoft.com/windowsserver2003/64bit/x64/overview.mspx). This allows Windows users full 64-bit computing, if they need or want it. As well, Linux and the BSDs have both run on 64-bit architectures long before Windows and Mac OS X, both. Simply supporting 64-bit architectures is no longer a deciding factor in an OS purchase decision since they all now have support for it.

As well, the entire discussion of 64-bit architectures is a bit of a red herring, since:

1. The G5 is the only fully 64-bit chip available in Apple's whole line, and
1. The full power that 64-bit computing can yield is not yet available in hardware

This first point is illustrated as follows running some code on my 15-inch PowerBook G4:

``` c test.c
#include <stdio.h>

int main(void)
{
     unsigned long *a;

     printf("word size: %d bytes", sizeof(a));
     return 0;
}
```

And the output:

``` sh
aluminum:~> ./test
word size: 4 bytes
aluminum:~>
```

If the G4 were 64-bit, we would have seen '8' in place of the '4' that was printed.

The biggest technical issue with this post has to be this statement:

> Basically, for every 7 steps a RISC chip (like the G4 or G5) takes in completing a process, a CISC (complex instruction set computing) chip like Intel's or AMD's takes about 15. This does not translate precisely to a simple conclusion such as "Divide a CISC chip clock speed in half to see a clock speed that's comparable to a RISC chip," but it's close. What it does mean is that a consumer cannot look at a Dell laptop processor speed of 1.67 ghz and think you need an Apple processor speed of 1.67 to be comparable. In fact, a Dell laptop processor speed of 1.67 is roughly equivalent to an Apple processor speed of 1.0 ghz.

This is a gross oversimplification. If a CISC instruction can do more work than a RISC instruction, and the clock speed of the CISC chip allows it to execute more instructions per unit time than the RISC chip, how could it take the CISC chip more "steps" to complete a process?

_Note: ISA = instruction set architecture_

The answer comes from several points:

* x86 is an extremely register-poor architecture.

Without enough registers available for some simple tasks (forget about complex tasks), the x86 compilers are forced to generate code that hits main memory more often than one would like. This reduces performance because it forces more cache misses and DRAM access is slower than cache access. Put another way, the register-rich PPC architecture actually makes better use of the caches by keeping them hotter because code can keep temporary values in registers rather than cluttering up the cache with tempvars that will become stale frequently.

* Some instructions on a CISC ISA take more than one clock cycle to complete.

Even though the newer x86 chips can issue more than one instruction per clock (superscalar execution), some instructions take more than one clock cycle to complete. There's nothing that can speed that up; this is inherent in the complexity of a CISC ISA. More instructions doing more work means that each instruction is implemented less than optimally.

* Optimal performance on the x86 requires that the pipeline be full all the time.

The pipeline on the x86 is extremely long, and when it stalls it causes a major performance degradation because the pipeline has to refill before the CPU can execute those instructions. Code that defeats x86 branch prediction will run poorly for sure. On the other hand, a RISC ISA is more forgiving of pipeline stalls.

The most important thing to note here, though, is not technical: Intel spent a fortune on advertising that reinforced the link between clock speed and quality of a CPU in the mind of the consumer. They reduced it to one metric that was easily bandied about at the watercooler and in doing so, pulled off the greatest technical marketing coup of this last decade. Anyone who has tried to convince a semi-technical man in his 30's or 40's to buy an Athlon instead of a Pentium will be familiar with how successful Intel was in this endeavor.

On a more editorial note, I would have liked the author to have compared more than just Dell. While Dell is the biggest target, there are others that employ the same tactics. As well, it would be interesting to do this comparison with PCs offered at brick-and-mortar outlets like Best Buy or Wal-Mart. There are generally less confusing options available in a store, if you're willing to endure a higher-pressure sales experience.

I hope that people don't start quoting the original author's post verbatim, since it could easily be chopped apart by those who would do so.
