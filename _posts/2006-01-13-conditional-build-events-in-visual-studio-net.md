---
id: 154
title: Conditional Build Events in Visual Studio .NET
date: 2006-01-13T10:44:04+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=154
categories:
  - Tech
---
I ran across an situation today when I wanted to do a build event, but only if my solution was in a specific configuration. Specifically, when the project was in the UnitTest configuration, I wanted to copy a unit test assembly into the main projects output folder so that a number of plugin classes provided by the unit test assembly could be used by the main project. I also wanted to copy in some unit test based configuration.

Unfortunately Visual Studio .NET does not keep Pre and Post Build Events within a configuration&#8217;s settings, they are stored globally across all configurations. Thankfully, given that build events simply get written to a batch file, then invoked you can use your 3L337 batch file skillz to perform conditional build events.

<div class="code">
  IF NOT $(ConfigurationName) == UnitTest GOTO end</p> 
  
  <p>
    :: copy unit test assembly to the service folder.<br /> echo Copying &#8220;$(TargetDir)UnitTests.dll&#8221; to &#8220;$(ProjectDir)..\MyProject\bin\debug\&#8221;<br /> copy &#8220;$(TargetDir)UnitTests.dll&#8221; &#8220;$(ProjectDir)..\MyProject\bin\debug\&#8221;
  </p>
  
  <p>
    :end<br /> echo Finished Post Build Event
  </p>
</div>

So, what does this bit of script do? Firstly it compares the current configuration to the configuration that I want to perform my build event for. Secondly, it negates this comparison, so that if the configuration is not what i&#8217;m looking for the branch jumps to the end without executing the build event. Lastly, if the configurations match, it performs the real actions of the build event.

It is a bit of a pain having to write this within a build event. It would be less of a pain if they pointed out a way of doing it within the help file for the build event editor. Configuration-based build events would be perfect, so the logic is performed by Visual Studio!