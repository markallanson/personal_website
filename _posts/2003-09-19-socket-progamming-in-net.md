---
id: 42
title: Socket Progamming in .NET
date: 2003-09-19T23:30:37+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=42
categories:
  - Tech
---
I am trying to write a simple tracert program in .net and have come across a problem. Assume that the rest of the packet data is correct.

I set the sockets TTL to 10 using the following code:

<div>
  socket.SetSocketOption(SocketOptionLevel.Socket, SocketOptionName.IpTimeToLive, 10);
</div>

Then send data out of the socket using an Echo request, then receive data from the socket. Now effectively the ref EndPoint remoteEP should now be set to an end point matching the 10th hop on its route to the destination, instead it contains an end point matching the actual destination.

Anyone got any idea on this?