---
id: 132
title: Back into my PalmOne Tungsten E + Rss
date: 2005-02-08T22:38:10+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=132
categories:
  - Tech
---
So, whilst preparing to go to Barcelona last week I decided to fire the Tungsten E back into life (haven&#8217;t touched in at least 6 months) so I could install the brilliant [Metro](http://nanika.net/Metro "Metro") for a bit of navi-help. As it turns out I didn&#8217;t get around to syncing Metro, and lived without it (not enough time to sync), but I was once again wowed by how nice the screens are on the current gen PalmOne devices. The font is so smooth and readable.

So. I had to find a use and get back into the PDA thing, despite what [Russell](http://www.russellbeattie.com/ "Russell Beattie") is preaching about the death of the PDA. I have had, and hated an Orange SPV E200, although I have never extensively used a Symbian based phone, I am thinking my next may be a Symbian.

Anyway I have gone off topic. So what it comes down to is there&#8217;s no good free Rss aggregator / Offline Rss reader for PalmOS. I challenge someone to prove me otherwise. I don&#8217;t want no Java, I want native. Oh, I also want it to sync my unread items with Rss Bandit.

So, [Plucker](http://www.plkr.org/ "Plucker") is pretty cool it will let me sync online content to my Tungsten, but that alone aint going to do the job, it doesn&#8217;t understand xml. It certainly doesn&#8217;t understand Rss. Luckily however you can provide a &#8220;Pre-Spider&#8221; program to run before the spidering engine does it job. and the spidering engine can spider local content. This smells do-able to me.

<div>
  <img src="http://www.markallanson.net/images/weblog/RssBandit2Plucker.png" alt="RssBandit2Plucker Screenshot" border="0" />
</div>

Enter RssBandit2Plucker.

When performing a sync of a channel in Plucker, it will automatically launch RssBandit2Plucker, which will analyse Rss Bandit&#8217;s unread items, and generate a collection of HTML on the local disk that is representative of the unread items in Rss Bandit. From here Plucker takes over, processes the HTML, downloads the images from the web and dumps it out as a palm database file (pdb) that, once synced will appear within the Plucker application on the device.

It&#8217;s not quite ready yet, the setup program is mostly done, however I have a few things left to sort out with auto configuration of Plucker. My aim is to make it seamless, no manual configuration (Other than selecting a PalmOS device to sync to which is asked the first time you attempt to sync the channel in Plucker.

Im not sure how big the audience is for this (its pretty specialised, linking in only with RssBandit, though im sure it could become quite extensible to handle an arbritrary desktop aggregator without too much effort.