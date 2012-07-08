--- 
title: Starbucks WiFi Woes
layout: post
---
For those of you who hit up the T-Mobile WiFi access points at your local Starbucks at various points, I've found two things to watch out for:

* T-Mobile proxies port 25 (SMTP) traffic. This wouldn't be horrendous if they didn't fail to also proxy the SMTP AUTH commands. Anyone shipping their outgoing mail over port 25 and needing authentication is hosed. If you can, submit your mail over the alternate submission port (587) if your ESP supports it.
* The layout of the stores was not well regarded when Starbucks Corporate decided to install those new sandwich microwaves. As such, any place within about a 60 degree fan-out in front of the cooker will lose WiFi due to microwave interference while it is running. This is quite frequently between the hours of 7 and 11 AM (and even more extended on weekends) so plan to either sit outside or somewhere way off to the side of the microwave unit.

As well, the service is pretty expensive (on the order of a landline broadband connection) and not very fast. But, it does in a pinch. Tim Bray says [Boingo is much faster](http://www.tbray.org/ongoing/When/200x/2007/10/20/Boingo) (and cheaper) but I've yet to find a place that had this service around me.
