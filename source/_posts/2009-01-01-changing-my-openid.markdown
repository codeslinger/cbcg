--- 
title: Changing my OpenID
layout: post
---
After consolidating my sites recently, I noticed that I could no longer log in to sites with my old [OpenID](http://openid.net). After a moment's reflection, I realized that the traffic for the OpenID was being redirected to the new site and thus looking to an OpenID provider as if my OpenID was, in fact, the new homepage URL. Oops! :)

To rectify this, I had to do a couple of things:

First, I installed a [YADIS](http://yadis.org) service discovery file in the docroots of both sites:

``` xml
<xrds:XRDS xmlns:xrds="xri://$xrds" xmlns="xri://$xrd*($v*2.0)" xmlns:openid="http://openid.net/xmlns/1.0">
  <XRD>
    <Service priority="1">
      <Type>http://openid.net/signon/1.0</Type>
      <URI>http://www.myopenid.com/server</URI>
      <openid:Delegate>
        http://tobydipasquale.myopenid.com/
      </openid:Delegate>
    </Service>
  </XRD>
</xrds:XRDS>
```

Then, I installed [nginx](http://nginx.net) rewrite rules on both sites to handle OpenID providers seeking authentication:

``` sh
if ($http_user_agent ~* openid) {
  rewrite   ^(.*)$    /yadis.xrdf   break;
}
if ($http_accept ~* application/xrds\+xml) {
  rewrite   ^(.*)$    /yadis.xrdf   break;
}
```

This gives me two OpenID's, one for the old site and one for the new, both of which are backed by the same OpenID provider and delegate. All set, right?

As it turns out, though, [Clickpass](http://www.clickpass.com/), which I use for [Hacker News](http://news.ycombinator.com/), does not support YADIS. I had to install the following rewrite rule in both sites to have my OpenID work correctly with Clickpass:

``` sh
if ($http_user_agent ~ URI::Fetch/0.08) {
  rewrite   ^(.*)$    /index.html   break;
}
```

I installed this rule under the others so that if Clickpass ever gets their act together, they will get the YADIS file instead.

As well, for the old site, I had to add a dummy index.html, and install the old method of OpenID delegation on both sites by adding the following tags to the head section of the HTML:

``` html
<link rel="openid.server" href="http://www.myopenid.com/server" />
<link rel="openid.delegate" href="http://tobydipasquale.myopenid.com/" />
```

This works, but sucks because an OpenID provider has to suck down the whole page in order to get those two lines.

In any case, both of my OpenIDs are working now. I hope this post will help others change their OpenIDs sanguinely!
