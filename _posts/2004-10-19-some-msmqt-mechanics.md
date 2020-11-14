---
id: 123
title: Some MSMQT Mechanics
date: 2004-10-19T13:54:30+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=123
categories:
  - Tech
---
This thread in the Biztalk.General newsgroup</a> explains some of the dynamics behind MSMQT operation and also makes clear why the active/dehydrated instances of MSMQT receive locations stay in the HAT tool once all orchestrations and messaging instances have finished with it. To quote the important part in this regard:

<div>
  Second, InReleaseT. Because MSMQT needs to guarantee ordered delivery, at<br /> any point in time only one thread on only one computer in the group must<br /> process messages that are delivered to a specific queue. This thread works<br /> on some persistent data that is saved and loaded from the database. We call<br /> this a MSMQT instance. When the thread is running on a specific computer,<br /> we say that the MSMQT instance is &#8220;Active&#8221;. When the data is persisted in<br /> the database and there is no one working on it we say that the instance is<br /> &#8220;Dehydrated&#8221;. An active MSMQT instance maintains a lock on the queue object<br /> in the database, so that no other active instance on any other computer can<br /> work on this queue. For load-balancing purposes and to save memory, active<br /> MSMQT instances are dehydrated if the queue wasn&#8217;t used in a while.
</div>

Good to note this information comes straight from the horses mouth.