---
id: 221
title: Windows Vista on an Alienware Area-51 m5550
date: 2006-12-27T17:23:23+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=221
categories:
  - Tech
---
I have been using the RTM of Windows Vista on my Alienware since it was released to MSDN in November &#8217;06. Generally, everything has gone smoothly, however there are a few problems. As I find the solutions to these problems I will post them up here for the benefit of others.

The official Alienware support channels are pretty bad from experience so far, especially their drivers section, so generally don&#8217;t expect a solution from them.

**Problem: The headphone jack doesn&#8217;t work when using a normal set of headphones with a phono plug.**

Solution: You are correct, this did not work for me either with the out-of-the-box Vista drivers. The chipset seems to be a Realtek chipset, and Vista installs generic &#8220;High Definition Audio Device&#8221; drivers, which don&#8217;t work with headphones (The inbuilt speakers work fine, and I have not tested the S/PDIF output, so im unsure as to whether they work or not).

The Alienware website doesn&#8217;t have drivers for this Realtek chipset&nbsp;- so the way I got this working was to install the Realtek drivers supplied on the &#8220;m5550i &#8211; R3 Series Support CD Revision 1.1&#8243; disk (the title of yours might vary). After the install of these drivers (and system reboot), you will get a warning about program compatibility of the Realtek control panel application that loads at startup. This program isn&#8217;t needed for operation of the soundcard, so you can just stop it from loading at startup using Windows Defender.

**Question: Does the&nbsp;hardware&nbsp;Fan button (reduce performance to reduce fan noise) do anything in Vista?**

Answer: I&#8217;m not entirely sure based on evidence I have seen so far about how much of an impact this button actually has. I specced my laptop with a 2Ghz Core&nbsp; 2 Duo processor, and when running normally the [WCPIDCLK](http://www.h-oda.com/ "H-Oda's WCUID Homepage") application reports the speed as circa 1995Mhz.

<a href="/blog/wp-content/uploads/2006/12/WindowsLiveWriter/WindowsVistaonanAlienwareArea51m5550_F40A/WCPUIDCLK_Before.jpg" atomicselection="true"><img style="border-right: 0px; border-top: 0px; margin: 0px 25px; border-left: 0px; border-bottom: 0px" height="140" src="/blog/wp-content/uploads/2006/12/WindowsLiveWriter/WindowsVistaonanAlienwareArea51m5550_F40A/WCPUIDCLK_Before_thumb.jpg" width="392" border="0" /></a> 

After pressing the Fan button, WCPUIDCLK reports a slight drop in CPU performance, circa 1932Mhz.

<a href="/blog/wp-content/uploads/2006/12/WindowsLiveWriter/WindowsVistaonanAlienwareArea51m5550_F40A/WCPUIDCLK_After.jpg" atomicselection="true"><img style="border-right: 0px; border-top: 0px; margin: 0px 25px; border-left: 0px; border-bottom: 0px" src="http://markallanson.net/wordpress/wp-content/uploads/2006/12/WindowsLiveWriter/WindowsVistaonanAlienwareArea51m5550_F40A/WCPUIDCLK_After_thumb.jpg" border="0" /></a> 

I also ran a few tests using [CPU-Z](http://www.cpuid.com/cpuz.php "CPU-Z Homepage") and it comes up with the same results &#8211; so it seems like it does do something, but not&nbsp;a lot, and certainly not enough to make the laptop turn off the fan.&nbsp; I&nbsp;haven&#8217;t run these tests on WindowsXP&nbsp;however, so am unsure as to whether&nbsp;it has more of an effect on that OS.&nbsp;