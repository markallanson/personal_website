---
id: 22
title: mReader v1.0 online
date: 2003-07-19T19:40:42+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=22
categories:
  - Tech
---
[Update: If you have come from Lockergnome you might want to know that v1.0 of mReader is deprecated and [version 1.01 has been available as of 23rd August 2003](http://www.markallanson.net/archives/000030.html)]

Okay, I have put a version of the mReader jar online. To get a copy of it point your J2ME midp enabled devices web browser to http://mobile.markallanson.net, alternatively the direct link to the jar file is [http://mobile.markallanson.net/j2me/mReader.jar](http://markallanson.net/markallanson.net/tracker/down.pl?ID=10 "mReader 1.0 JAR").

The jar file is 42kb in size, most of this comes from the kXML2 and XmlPull libraries I am using for XML processing. I might try and cut out a bunch of functionality from these libraries in the future to make the jar smaller.

**Features so far**
  
1. Processing of RSS 0.91, 1.0, 2.0, RDF. In case you are interested, the processing for each of the above formats is identical.
  
2. Importing of an OPML outliner file from the web. For [SharpReader](http://www.sharpreader.com) users (and any others who use a reader that can export to OPML), ftp your exported OPML to a website and point mReader to it to download a list of existing feeds.
  
3. HTML tags are stripped out of post descriptions. Later versions will have a &#8220;link list&#8221; functionality for a post so you can see what links the post contains.

**Limitations/Annoyances at the moment**
  
1. You can only store up to 50 Feeds in your feed list.
  
2. mReader will only allow you to view the first 50 items in a downloaded feed.
  
3. Once a feed is in your list, you can&#8217;t remove it. (this will be fixed in a later version)
  
4. mReader doesnt handle some feeds too well due to the way I currently make use of the kXML2 parser. If you try to load a feed and you get a blank list of items, then mReader has most probably had an error trying to download. Email me a copy of the RSS file (or weblog URL) and I will see whats going on.
  
5. mReader does not display any &#8220;I am currently downloading&#8221; type messages. Once you have selected a Feed, wait a while, I can assure you it hasn&#8217;t crashed!
  
6. mReader currently doesnt look at content:encoded fields for post text. it uses the description tag instead. For memory reasons.

I have currently tested this jar on the default color phone provided with Sun&#8217;s Wireless toolkit, aswell as the Nokia 7210 emulator (the phone I use).

Note that there is currently minimal error checking in the app, so you may get an exception every now and then.

If you have any problems, please [email me the details](mailto:mark@markallanson.net).