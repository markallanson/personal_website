---
id: 175
title: Creating InfoPath 2007 Beta 2 Template Part Files in VSTO
date: 2006-06-29T16:24:15+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=175
categories:
  - Tech
---
If your developing template parts for InfoPath 2007 using Visual Studio Tools for Office (VSTO) then you will probably hit a stumbling block when you find there is no way to generate the .xtp file required for adding the Template Part into the VSTO ToolBox.

I couldn&#8217;t find a way of doing this within VSTO, so after a bit of poking around, it seems that .xtp files are just cabinet files containing a bunch of the raw data. Thankfully creating cabinet files is simple as there are a couple of command line tools to create them shipped with various SDKs.

So, to generate your .xtp file that you need for the toolbox, just add the following as a post build event. All the files you need for a .xtp file are in the &#8220;InfoPath Form Template&#8221; subfolder of your template part project.

<div class="code">
  cabarc N &#8220;$(TargetDir)$(ProjectName).xtp&#8221; &#8220;$(ProjectDir)InfoPath Form Template*.*&#8221; >> &#8220;$(TargetDir)BuildXtp.log&#8221;
</div>

This will drop a .xtp file into the target directory (ie bin\debug) when you rebuild your template part. It will also drop a log file in the same location.

If anyone knows of a way to create a .xtp file automatically using built in tools that I have been unable to find please let me know.

<p style="font-size: 10px; text-align: right">
  technorati tags:<a rel="tag" href="http://technorati.com/tag/InfoPath">InfoPath</a>, <a rel="tag" href="http://technorati.com/tag/2007">2007</a>, <a rel="tag" href="http://technorati.com/tag/XTP">XTP</a>, <a rel="tag" href="http://technorati.com/tag/VSTO">VSTO</a>, <a rel="tag" href="http://technorati.com/tag/Visual%20Studio">Visual Studio</a>, <a rel="tag" href="http://technorati.com/tag/missing">missing</a>, <a rel="tag" href="http://technorati.com/tag/.xtp">.xtp</a>
</p>

<!-- technorati tags end -->