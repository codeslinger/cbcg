--- 
title: Hooplah over Hybrid RIAs
layout: post
---
A [buddy](http://whatcomesnext.brussin.com) just sent me a link to [Joyent Slingshot](http://joyeur.com/2007/03/22/joyent-slingshot) which is a new service/application from Joyent that allows you to create hybrid web/desktop applications that automatically update to the latest version and synchronize the data between desktop and cloud. Adobe's [Apollo](http://labs.adobe.com/wiki/index.php/Apollo) framework has the same intentions. While these are making a lot of noise on the blogs lately, I'm not so sure that they are going to live up to the hype.

The reason I say that is that [Java Web Start](http://en.wikipedia.org/wiki/Java_Web_Start) has been around since Java2 and its never taken off. I semi-tracked its progress since it came out, since I thought it was really cool stuff. However, it was always puzzling to me to watch this neat technology go fallow for most applications.

I think the reason that Slingshot and Apollo are not going to be gihugic are that its harder than advertised to create a hybrid RIA and that most applications simply don't require a "disconnected" operation mode. What functionality would you be able to use from a disconnected Amazon or Netflix? For PIM/collaboration apps, this mode makes sense and would be a real boon for apps like Gmail/GDocs or the other Office 2.0 suites out there. But I think  that developers will find that the added complexity of synchronization won't pay dividends for most of the applications they write, assuming those apps look moderately like the ones being written today. Of course, I've been wrong before...
