---
id: 218
title: Late Binding Sample
date: 2006-12-05T23:40:21+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=218
categories:
  - Tech
---
I did up this small late binding&nbsp;sample for a colleague last night and I thought I may as well share it with the rest of the world. If you have ever wanted to see how late binding to a COM object works this sample solution is the place to look.

The solution includes two projects, one a sample COM object to late bind to, the second is a console application that late binds to the COM object and makes a method call.

I know this stuff is not rocket science, and is even explained (somewhere) in MSDN, this should save some digging and time.

Of course I should mention the pitfalls that can occur with this type of late binding. It&#8217;s slow, very slow, very very slow compared to early binding, so use it wisely, and only after careful consideration.

**<font size="4"><a title="Download Late Binding Sample" href="http://markallanson.net/markallanson.net/files/technical/c.net/examples/latebinding/LateBindingSample.zip" rel="nofollow">Download Late Binding Sample</a></font>**