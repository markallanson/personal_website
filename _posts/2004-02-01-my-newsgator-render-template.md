---
id: 88
title: My NewsGator Render Template
date: 2004-02-01T23:43:44+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=88
categories:
  - Tech
---
This template (sort of) makes the Post view within Outlook look like the &#8220;News Page&#8221; displayed when you select the root NewsGator folder.

To Install:

  1. [Download the template \[Marks_NewsGator.zip\] (3kb)](http://markallanson.net/tracker/down.pl?ID=6 "Mark's Newsgator Render Template").
  2. Unzip the files into your Newsgator\Render folder.
  3. Inside Outlook, Press the NewsGator button on the NewsGator toolbar, then select Options&#8230; from the drop down menu.
  4. Switch to the Rendering tab, and select &#8220;Marks_NewsGator&#8221; from the drop down list. (Note you can also set the rendering template up on a feed-by-feed basis, look at the NewsGator documentation for info on how to do this)
  5. Restart Outlook.

To get the text centered next to the NewsGator logo at the top I have had to use a 12px top margin. For some reason I couldn&#8217; get the vertical-alignment: middle; CSS style working. If someone wants to have a look at the CSS and XSLT files for the template and tell me what i&#8217;m doing wrong I would greatly appreciate it, i&#8217;m still an infant when it comes to CSS.