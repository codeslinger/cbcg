--- 
title: Nettica DNS and Amazon EC2
layout: post
---
When I started using [Amazon's EC2 service](http://aws.amazon.com/ec2) I realized pretty quickly that the traditional load-balancing solution of putting a big, honkin' [F5 BIG-IP](http://www.f5.com/products/bigip/) in front of the servers wasn't going to work out. Amazon doesn't currently rent F5's.

So, I went looking around for a DNS-based load-balancing solution that would be flexible enough to deal with the dynamic environment that EC2 provides. However, I pretty quickly found that the existing dynamic DNS APIs of most of the providers were not up to the task of programmatically updating a DNS record the way I needed. Specifically, I wanted to be able to register and deregister an EC2 instance with a round robin A record automatically upon instance startup and shutdown.

In the end, I was only able to find one dynamic DNS provider whose API was up to this task: [Nettica](http://www.nettica.com/).

Once I found them, it was pretty easy to wrap their SOAP-based API into a binary to drive this type of dynamic management of my DNS records. [Apache Axis](http://ws.apache.org/axis/) took care of turning the WSDL into Java (the only library that could do so across three programming languages, by the way) and the code for driving that wrapper was pretty simple. The end result of that effort is now [open sourced for all to use](http://code.google.com/p/netticadns).

The way I use the new Nettica client is to have the init script automatically register an instance on startup with the Nettica service. However, I remove the instance from Nettica a bit before shutting down the instance itself in order to deal with DNS caches that sustain the now-removed IP for longer than the specified TTL value. You might be able to automate this by throwing a `sleep LARGENUMBER` into the shutdown portion of the init script, but I haven't tried this yet.

In any case, I hope people find this client helpful when using EC2. I look forward to hearing about experiences with it and improving it for others. I'm planning for a release pretty soon to add support for RPM packaging, as most of the [AMIs](http://docs.amazonwebservices.com/AmazonEC2/dg/2007-01-19/CreatingAndBundlingAMIs.html) used today appear to be RedHat RPM based. Watch this space for updates.
