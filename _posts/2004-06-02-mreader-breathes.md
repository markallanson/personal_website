---
id: 111
title: mReader Breathes!
date: 2004-06-02T23:27:12+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=111
categories:
  - Tech
---
After laying dormant since [August 23rd last year [mReader 1.01]](http://www.markallanson.net/archives/000030.html), I have finally got around to decompiling the mReader from binary form and have thrown it all into the Eclipse 3.0 IDE. Wow, was I blown away by the new version of Eclipse. What a great IDE. I have been using the version 2.xx incarnation at work to do Java work and while great, the new Eye-candy in the version 3.0 incarnation is truly fantastic.

Now, back on topic. For those who don&#8217;t know, I lost the mReader souce in a Windows incident about 3-4 months ago. I used [Jode](http://jode.sourceforge.net/) (Thanks, Rich Fuller for pointing me to it) to decompile the mReader binaries, and it has done a servicable job. After about 10 minutes of playing around Eclipse is finally happy with the java source. I have had to chop out some bits that didnt decompile properly, and will have to re-implement them in the next few days. Jode also pulled some very interesting little things out of its decompiler hat, for example:

<pre>public void ImportOPML() {
&nbsp;&nbsp;&nbsp;object = object_1_;
&nbsp;&nbsp;&nbsp;break;
}</pre>

<pre>public void Add(RssItem newItem) {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;object = object_0_;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;break;
}</pre>

<pre>public progressCanvas(Display display) {
&nbsp;&nbsp;&nbsp;this.display = display;
&nbsp;&nbsp;&nbsp;screen = screen;
&nbsp;&nbsp;&nbsp;if (!this.isDoubleBuffered())
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;offscreen = Image.createImage(this.getWidth(), this.getHeight());
}</pre>

So where to from here? I am going to clean up the code, replace the chunks that didn&#8217;t decompile correctly and put it all up in a sourceforge project. I have had a lot of requests for the source over the last few months and I may aswell give something back.

Ill keep you posted.