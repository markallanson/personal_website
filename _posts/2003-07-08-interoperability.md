---
id: 16
title: Interoperability
date: 2003-07-08T21:30:42+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=16
categories:
  - Tech
---
Over the past few days at work I have been involved in the testing of an interop module that links our Point of Sale system to a 3rd Party Accounting and Hotel Reservations system. Development for this interface took place on our behalf a number of months ago.

The unique thing about this particular interop process is that the owner of the company we are developing with wouldn&#8217;t give us first hand access to the development staff of his product. Any liaison between ourselves and his development staff had to be piped through him to &#8220;protect&#8221; his development staff from distractions. (gee, they must be a pretty distractable mob)

This was unusual, but acceptable, as they provided us with a simple spec of the interface and data they expected from our system. The spec was programmed, with a few questions being piped through our human interface with their development staff. An initial testing phase was planned.

The interop works in duplex mode. We have to retrieve configuration data from their system, and we have to write sales information back to their system. Initial tests seemed fine, our system was retrieving all configuration data correctly. Our first sales export seemed to go okay, with a bit of tweaking.

We are then presented with a 20-30 page document. This new document (which seems like a bit of a novel), documents the rest of the interfaces we have to test. In short, 2 brand new interfaces were presented to us. The document is dated 4th July, 2003. Confusion crosses their faces, as we explain to them that we had not received this new specification. Aparently their development staff were supposed to forward this specification to us at a previous time. (a break in protocol?)

I can only blame us for this situation. We never have met with their development staff, and still never have. We should have insisted, but never did. Whenever interfaces are being developed you need people with intimate knowledge of each system to be involved in the design of the interface. I know that I know every part of every program I work on better than any manager or tech support technician ever could. Even 3 years after development has finished.

If direct interaction between development staff&#8217;s is not attainable, then specifications **must** be detailed with ultra-fine granularity and signed off as correct by a number of parties, especially developers. There is no use in just specifying &#8220;The amount of the discount is expected in this field in this format&#8221;, you need to know how subtle changes to the amount will effect the operation of the system you are interoperating with. Does the discount effect tax values, if so, under what circumstances should they be modified.

Lessons Learned
  
1. Always make sure specifications you create are correct, and have a ultra-fine granuarity.
  
2. When developing interoperability guidelines between 2 systems, always join all development parties at least once, and decide on interop standards.
  
3. Never trust other specifications written by a 3rd party, always look for the holes.
  
4. Always jump on the holes before testing begins, in a small ISV situation most of the time the first sales have been made by the time testing starts. Revenue, and your next pay packet may depend on it.