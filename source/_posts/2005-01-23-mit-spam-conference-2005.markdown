--- 
title: MIT Spam Conference 2005
layout: post
---
I just got back from the MIT Spam Conference 2005, which is put on by Paul Graham and Gilberte Houbart.

Jonathan Zdziarski's talk on [Bayesian Noise Reduction](http://bnr.nuclearelephant.com/) was easily the most technically-interesting talk of the entire conference. The idea is to find contexts in the message so that out-of-context text can be ignored with respect to the classification of said message. I highly recommend reading the paper or at least checking out the presentation.

Also interesting was the dissertation on the trial of [ROKSO](http://www.spamhaus.org/rokso/)-listed spammer Jeremy Jaynes (a.k.a Gaven Stubberfield) by [Jon Praed](http://www.i-lawgroup.com/). [Project Honeypot](http://www.projecthoneypot.org/) also seems to be coming along quite well under the direction of [Matthew Prince](http://unspam.org/). Finally, [John Graham-Cumming](http://jgc.org/) discussed the interesting, if somewhat informal, results of his [People and Spam](http://www.jgc.org/pdf/spamconf2005.pdf) survey. An interesting point from that: he found that 1% of the men who had used computers for 10+ years had also bought something from spam.

Brian McWilliams gave a pretty interesting look at his book, [Spam Kings](http://amzn.to/MeHA70). He gave away some free copies, but I couldn't get down there fast enough (people were hijacking the free books in the middle of his talk ;-). In case you haven't heard, the book is about the lives and motivations of some big spammers.

[MailFrontier](http://mailfrontier.com/) got two talks in this year's list, and both were somewhat disappointing. The first was about using Bayesian classification applied to phishing, but the results were somewhat obvious. The main thing that came from the talk was that one should have a corpus for spam and another for phish, as opposed to having an integrated corpus for both. The audience decided that the spam is to ham, as phish is to "phowl", which was pretty funny. The second talk was weaker, as the speaker misspelled the title of his own talk and also refused to give details on their implementation. It was about using lexicographical distance to normalize tokens. For example, there are 6 quintillion+ ways to form the word "Viagra" in a recognizable manner; it would be useful to see all of these tokens as "Viagra" for the purposes of token frequency counts. So, the idea is to make edits to a token until it reaches a certain threshold of edits; if then it resembles a known token, it is that token; if not, its not.

John Graham-Cumming then stated during the QA session that, in [POPfile](http://popfile.sourceforge.net/), they are sorting the letters of words with 6+ letters and using the sorted result as the token. It turns out, he said, that there is a very small chance of collision using that technique given the low probability of those words having anagrams in English and doing so defeats attempts at misdirection via misspelling words.

The IBM and Cisco talks were not very interesting: a form of both talks had been at either or both of the previous Spam Conferences. Cisco is basically advocating that everyone use DomainKeys and IBM has figured out how to put a bunch of filtering technologies together to create a more accurate filter. I really wonder why either of these talks were accepted...

[Gordon Cormack](http://plg.uwaterloo.ca/~gvcormac/) came down from the University of Waterloo to talk about Standardized Filter Evaluation. It was a fairly obvious intersection of testing methodologies and anti-spam filters and there were some obvious problems with it, as well.

The rest of the talks were pretty bad.

Dave Mazieras described [MailAvenger](http://www.mailavenger.org/), an MTA that is both individual-user-configurable and also does SMTP CBV; that didn't go so well for him. It does lots more than that, but he chose to focus on that and got the results that you'd expect. I brought up the fact that Verizon does this to Paul personally while standing in the back, but I was surprised that no one in the audience told the speaker about Verizon's use of this technology and the problems it causes. Paul commented that whatever heat Verizon got for doing that obviously wasn't enough to make them stop, to which I could only shrug agreement.

Rui Dai gave a talk about Regulation, where they proposed that spam was such a problem because spammers could not effectively find targets and thus needed to blast all of their spam runs to everyone on their lists. He then proposed a third-party arbiter that would help spammers target likely recipients better and this would in theory reduce the overall volume of spam. As expected, this was met with more than a little trepidation from the audience, and wasn't described very well in the talk to begin with.

Oscar Boykin discussed using social network graphs for determining spam, but failed to realize that this is almost exactly what [PageRank](http://en.wikipedia.org/wiki/PageRank) did for Google and further failed to realize why it [could be just as easily killed](http://jeremy.zawodny.com/blog/archives/000751.html).

The Distributed Quota Management talk never came off, as the speakers could not be found.

I've been to every one of the MIT Spam Conferences, but I'm not sure if I'm going to go next year. The palpable undercurrent of the conference was that Bayesian filtering was the solution to spam (John Graham-Cumming basically came out and said this during the final QA session at day's end), and that's just not true. Furthermore, I know for a fact that they will reject papers that are too far off-topic with filtering in general, thus lessening the potential worth of the conference as a place for the discovery of new ideas.

Now, the muffins and coffee are very good and its good to meet people and if I lived in Boston or near there I would probably continue to go. But for me to attend next year, I need to see a list of *very good* papers on topics that are not necessarily related to statistical filters. This will probably only happen when someone other than Paul Graham or one of his fans select the papers for this thing. As it stood this year, I had already read Jonathan's paper on Bayesian Noise Reduction before I came, and that pretty much made my trip up there almost entirely unnecessary.
