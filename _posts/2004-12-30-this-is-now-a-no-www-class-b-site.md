---
id: 131
title: This is now a no-www Class B site
date: 2004-12-30T19:45:44+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=131
categories:
  - Tech
---
[<img src="http://no-www.org/images/type1/class-b.png" border="0" />](http://no-www.org/)After stumbling across no-www.org, I have added [no-www](http://no-www.org/) Class B support to markallanson.net.

What does this mean? Well its really quite simple, any request that comes in to markallanson.net with the www prefix will politely be redirected to its no-www equivilant. For Example, &#8220;http://www.markallanson.net/&#8221; will be automatically redirected to &#8220;http://markallanson.net&#8221;. This is done via modifications to the apache .htaccess.

[Head on over to no-www for more information&#8230;](http://no-www.org/)

PS: I will have a bit of work ahead of my to change all my hyperlinks to remove the www., however I will get around to this in due course. (Note however, that the apache redirection works for the hyperlinks too)