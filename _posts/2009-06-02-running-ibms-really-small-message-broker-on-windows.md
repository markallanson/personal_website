---
id: 244
title: 'Running IBM&#8217;s Really Small Message Broker on Windows'
date: 2009-06-02T17:29:08+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=244
categories:
  - MQTT
  - RSMB
  - Sensors
---
Since getting a [CurrentCost CC128](http://currentcost.com/product-cc128.html) &#8220;smart&#8221; electricity meter a few weeks ago the hacker in me has had a resurgence and I have started writing hobby-code again on top of my day job. There seems to be a small industry of software for interacting with these smart meters, and publishing and recording the data to various sources such as [Pachube](http://pachube.com) that allow you to share your electricity consumption data with others. At the consumer/home level things seem to still be targeting tinkerer&#8217;s like myself, rather than the general consumer. Most of the tools seem to be centered around the linux and java community, which is all well and good, but why can&#8217;t us Microsoft .Net folks get in on some of the action.

Microsoft&#8217;s Windows Home Server is a perfect platform to act as a hub for this type of stuff. It&#8217;s designed to be always on, with an add-in model that allows extensions, so I decided to embark on using my HP MediaSmart EX470 to publish the CC128 sensor data in a variety of ways.

As part of IBM&#8217;s work surrounding telemetry and sensor messaging they have made, freely available, what they are calling a &#8220;nano broker&#8221;, the [Really Small Message Broker (RSMB)](http://alphaworks.ibm.com/tech/rsmb). This broker talks the [Message Queue Telemetry Transport (MQTT)](http://mqtt.org) protocol, designed again, by IBM (the brainchild of [Andy Stanford-Clark](http://stanford-clark.com/), IBM Master Inventor and illustrious enough to have his own [wikipedia page](http://en.wikipedia.org/wiki/Andy_Stanford-Clark)). The idea is that you can publish data on a specific **Topic** to the RSMB via MQTT, and the RSMB will then distribute that data to any &#8220;client&#8221; that is **subscribed** to that topic. Being IBM, the code is primarily targeted at the linux community, however they are also nice enough to provide a Windows console application binary.

Getting a console application to run when Windows Home Server boots is not as simple as putting it in the Start menu, or in one of the myriad of &#8220;Run&#8221; registry sections. Fortunately, Microsoft provides two executables, instsrv.exe (service installer) and srvany.exe (run any program as a service) as part of the [Windows Server 2003 Resource Kit](http://www.microsoft.com/downloads/details.aspx?familyid=9d467a69-57ff-4ae7-96ee-b18c4790cffd&displaylang=en), and these can be used to run any program as a service, which means that you can get IBM&#8217;s RSMB running at server boot without having to have a user logon session.

The following steps will allow you to run the RSMB on Windows Home Server so that it starts up at server boot. These instructions assume you have installed the Windows Server 2003 Resource Kit in the standard location, and you have unzipped the RSMB to C:\RSMB. Alter the instructions for your paths if they vary. You&#8217;ll have to do all this by logging onto the server using the remote desktop client, not the standard windows home server console.

**1. Use InstSvc.exe to install an SvrAny.exe based service.**

_32bit Windows Server (ie, HP MediaSmart EX470 etc)_

<pre>"C:\Program Files\Windows Resource Kits\Tools\instsrv" RSMB "C:\program files\Windows Resource Kits\Tools\srvany.exe"</pre>

_64bit Windows Server_

<pre>"C:\Program Files (x86)\Windows Resource Kits\Tools\instsrv" RSMB "C:\program files (x86)\Windows Resource Kits\Tools\srvany.exe"</pre>

**2. Alter the registry to let SrvAny.exe know that it should run the broker.**

Note the important part here is setting the AppDirectory, without which the RSMB will mysteriously start and then immediately stop because it can&#8217;t find it&#8217;s Messages file.

Windows Registry Editor Version 5.00

<pre>[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\RSMB\Parameters]
"Application"="C:\\rsmb\\broker.exe"
"AppDirectory"="C:\\rsmb\\"</pre>

[Registry File](http://markallanson.net/wordpress/wp-content/uploads/2009/06/setupreg.zip)

That&#8217;s all there is to it. If you go into Computer Manager and the services browser, you should be able to start the RSMB service and the broker will be running silently in the background. You can check this out by looking at Task Manager, Processes Tab, where you will see both the SrvAny.exe and Broker.exe processes. You can also run _netstat -an_ in a powershell or cmd.exe window to check that the server is listening on port 1883.

The only thing that you should do on top of this is to change the service to run with a non administrative account with locked down settings (read/write access to the RSMB folder and the ability to listen to connections on port 1883 should do the trick).