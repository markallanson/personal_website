---
id: 162
title: Personalized Meme Tracking in RSSBandit
date: 2006-02-19T23:52:55+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=162
categories:
  - Tech
---
In his post <cite><a href="http://www.25hoursaday.com/weblog/PermaLink.aspx?guid=96bc9d08-aee6-4f39-a7db-f4a2941d4700" /></cite>[Jubilee Thoughts: Tracking Hot Topics](http://www.25hoursaday.com/weblog/PermaLink.aspx?guid=96bc9d08-aee6-4f39-a7db-f4a2941d4700), Dare Obasanjo, creator of RSSBandit has a post discussing his thoughts on personalized meme tracking, and how to integrate it into the next release of RSSBandit. 

<blockquote cite="http://www.25hoursaday.com/weblog/PermaLink.aspx?guid=96bc9d08-aee6-4f39-a7db-f4a2941d4700">
  <p>
    <em>On a related note, I&#8217;ve recently been using meme trackers like Memeorandum and TailRank which try to show the interesting topics among certain technology blogs. I think this is very powerful concept and is the next natural evolution of information aggregators such as RSS Bandit. The big problem with these sites is that they only show the current topics of interest among a small sliver of blogs which in many cases do not overlap with the blogs one might be interested in. For example, today&#8217;s headline topic on Tech.Memeorandum is that a bunch of bloggers attended a house party which I personally am not particularly interested in. On the other hand, I&#8217;d find it useful if another way I could view my subscriptions in RSS Bandit pivoted around the current hot topics amongst the blogs I read. This isn&#8217;t meant to replace the existing interface but instead would be another tool for users to customize their feed reading experience the same way that newspaper views and search folders do today. </em>
  </p>
</blockquote>

<p class="citation">
  I think personalized meme tracking is a great thing to integrate into RSSBandit, but from my perspective I would love this type of feature to introduce me to new writers/bloggers, rather than just aggregate existing content from my list of feeds. I guess, this would also enable me to pair down my existing feed list to a selection of core bloggers, and allow me to investigate content from other bloggers as and when they draw me in.
</p>

<p class="citation">
  Now, I understand this type of feature cannot be provided by a client-side only product like RSSBandit (it only knows about one&#8217;s own feeds) and would require some hefty server-side processing in order to generate this type of data in near real time. Maybe this is a service that the existing meme trackers could start providing, and by exposing an API allow client aggregators to hook into the service.
</p>

<p class="citation">
  How do I see this working from a user interface perspective? Well, at the end of a post in the view pane (or in newspaper view), you could have a "related conversation" section that lists people that have also been writing about the same topic along with a short blurb from each person. Clicking on the person would open up their permalinked post, and maybe also provide a small "subscribe" button to allow you to subscribe to that blog&#8217;s RSS feed.
</p>

<p class="citation">
  However, I digress, this type of functionality requires a number of entities working together, and nothing like this is ever done quickly. To answer Dare&#8217;s comments directly with relation to his proposed implementation.
</p>

  1. [Nik&#8217;s](http://www.mackmo.com/nick/blog/tech/2006/2/13/Personalized-meme-tracking.html) UI is about spot on, but integrate this with my suggestion above by having this information attached to the end of an individual post showing other content related to the post I am currently reading. Expand the Discussion section by default, but include a blurb from each discussion. 
  2. No change of ranking based on previously read topics, just notification via a different color that the discussion is partially read.
  3. Definately have a mark discussion as read feature. 

&nbsp;
  
<!-- technorati tags begin -->

<p style="font-size:10px;text-align:right;">
  technorati tags: <a href="http://technorati.com/tag/Meme" rel="tag">Meme</a>, <a href="http://technorati.com/tag/Tracking" rel="tag">Tracking</a>, <a href="http://technorati.com/tag/RSSBandit" rel="tag">RSSBandit</a>, <a href="http://technorati.com/tag/Tracking%20Hot%20Topics" rel="tag">Tracking Hot Topics</a>, <a href="http://technorati.com/tag/memeorandum" rel="tag">memeorandum</a>, <a href="http://technorati.com/tag/TailRank" rel="tag">TailRank</a>
</p>

<!-- technorati tags end -->