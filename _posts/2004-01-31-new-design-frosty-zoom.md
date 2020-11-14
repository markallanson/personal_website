---
id: 86
title: 'New Design: Frosty Zoom'
date: 2004-01-31T20:14:08+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=86
categories:
  - Tech
---
As you can see (if you are [viewing in a browser](http://www.markallanson.net/)) I have created a new website design. Not much of the MovableType templates are left.

The new design is a pure CSS based design. There should be no font tags anywhere, and the only table that exists on the entire site is the standard MovableType calendar. I don&#8217;t think i&#8217;m quite ready to try and de-tablify that yet.

I have tested this site design in Mozilla Firebird 0.7 and IE 6.0.2800. It /almost/ looks the same on each browser, the only difference being the menu bar at the top (which is actually an unordered list). On Mozilla there is some padding between each menu item that i&#8217;m not quite sure how to get rid of (maybe some css guru out there can give me a point in the right direction?). It wasn&#8217;t to hard getting both browsers looking very similar, but by the same token my design isn&#8217;t exactly pushing the boundaries of CSS.

For best effects you should have the [Lucida Grande](http://www.markallanson.net/resources/lucida_grande.zip) font installed on your system. If you don&#8217;t have Lucida Grande (which incidently is one of the fonts that makes OSX look gorgeous) it will default to Verdana.

To give the transparent effect I have had to use a halfscreen light grey image. I can&#8217;t wait till you can do something like this though:

<pre>.blogbody
&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;background-color: #666666;
&nbsp;&nbsp;&nbsp;background-opacity: 20%;
&nbsp;&nbsp;&nbsp;}
</pre>

If anyone notices anything that doesn&#8217;t work on their particular browser (havent tested on opera yet, or any mac or linux browser like konqeror) then please [drop me an email](mailto:mark@markallanson.net) so I can have a look at the stylesheet.

Update: I am still working on the photo gallery template page. Note that although it doesnt currently fit together very well, it does actually work.