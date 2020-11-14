---
id: 137
title: Converting Feeds to Feedburner
date: 2005-03-15T23:32:26+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=137
categories:
  - Tech
---
[![](http://feedburner.com/fb/images/headerlogo-b.jpg)](http://feedburner.com "Feedburner Website")I have just swiched over to using [FeedBurner](http://feedburner.com "Feedburner Website") for distribution of my RSS and ATOM feed. This looks quite interesting. Getting it working took a bit of fiddling though, with Feedburner at one point telling my my feed was eating itsself (recursive reference).

The trick is that you need to let Feedburner know when you update your feeds, however at the same time redirect any requests that are made for your original source file to the new Feedburner url. The problem being that Feedburner needs to access the original url for its source of information. My original attempt was just to add a bunch of lines to my .htaccess file so that all requests for the old urls got redirected to Feedburner instead, as below.

<div>
  Redirect temp /markallanson.net/weblog/rss2.xml http://feeds.feedburner.com/Markallansonnet<br /> Redirect temp /markallanson.net/weblog/atom.xml http://feeds.feedburner.com/Markallansonnet<br /> Redirect temp /markallanson.net/weblog/index.rdf http://feeds.feedburner.com/Markallansonnet<br /> Redirect temp /markallanson.net/weblog/index.xml http://feeds.feedburner.com/Markallansonnet
</div>

Now, Feedburner was configured to use my Atom feed as it&#8217;s data source. The redirect was causing problems. The answer to this problem was simpler than I originally thought. Make my MovableType Atom template simply write to a brand new url, and make Feedburner consume the new URL. Redirects for the old ones will continue to be redirected to Feedburner which pulls new content from the new source.