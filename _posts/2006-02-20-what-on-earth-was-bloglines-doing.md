---
id: 163
title: What on Earth was Bloglines Doing?
date: 2006-02-20T23:04:25+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=163
categories:
  - Tech
---
I was having a browse through my referrer logs, and to my surpise I noticed that a single IP address was responsible for consuming 1.16GB of data during the month of January! 

Here is the stat listing from AWStats&#8230;&nbsp; 

<table width="100%" cellspacing="0" cellpadding="2" border="1">
  <tr bgcolor="#ececec">
    <th>
      Host
    </th>
    
    <th width="80" bgcolor="#4477dd">
      Pages
    </th>
    
    <th width="80" bgcolor="#66eeff">
      Hits
    </th>
    
    <th width="80" bgcolor="#2ea495">
      Bandwidth
    </th>
    
    <th width="120">
      Last visit
    </th>
  </tr>
  
  <tr>
    <td class="aws">
      65.214.39.151
    </td>
    
    <td>
      2843
    </td>
    
    <td>
      2843
    </td>
    
    <td>
      1.16 GB
    </td>
    
    <td>
      31 Jan 2006 &#8211; 23:32
    </td>
  </tr>
</table>

Doing a reverse lookup on this IP using tracert, we can see that this is the Bloglines Crawler&#8230; 

<p class="code">
  &nbsp;19&nbsp;&nbsp;&nbsp; 98 ms&nbsp;&nbsp;&nbsp; 99 ms&nbsp;&nbsp; 104 ms&nbsp; crawler.bloglines.com [65.214.39.151]&nbsp;
</p>

I can&#8217;t for the life of my fathom why bloglines would need to consume 1.16GB of bandwidth during a single month! Looking at this a little bit further, i&#8217;m going to out the worst of those bandwidth consumers. 

  1. 1.16GB: Bloglines Crawler.
  2. 534MB: Something under Optimum Online (ool-435525cb.dyn.optonline.net). Seems to be an service provider. 
  3. 414MB: Omni Explorer (Could be a spambot, [see the Spamhuntress entry for Omni Explorer](http://spamhuntress.com/wiki/Omni-explorer "Spamhuntress on Omni Explorer")).
  4. 255MB: Gemstar TVGuide Inc.

I have a very small readership, hardly worth agressive crawling, so I can&#8217;t imagine what kind of attention popular bloggers are getting from these guys!

<!-- technorati tags begin -->

<p style="font-size:10px;text-align:right;">
  technorati tags: <a href="http://technorati.com/tag/Bloglines" rel="tag">Bloglines</a>, <a href="http://technorati.com/tag/Bandwidth" rel="tag">Bandwidth</a>, <a href="http://technorati.com/tag/Hog" rel="tag">Hog</a>, <a href="http://technorati.com/tag/Omni%20Explorer" rel="tag">Omni Explorer</a>, <a href="http://technorati.com/tag/Optimum%20Online" rel="tag">Optimum Online</a>, <a href="http://technorati.com/tag/Gemstar" rel="tag">Gemstar</a>, <a href="http://technorati.com/tag/TVGuide%20Inc" rel="tag">TVGuide Inc</a>
</p>

<!-- technorati tags end -->