---
id: 230
title: Home Sensors
date: 2009-05-31T17:58:33+00:00
author: Mark
layout: default
guid: http://markallanson.net/wordpress/?page_id=230
---
This page shows **real-time live** data from Sensors in my house. 
([http://markallanson.net/sensor](http://markallanson.net/sensors)). You can view the Pachube page that hosts the 
underlying raw data at [Home Sensors on Pachube](http://www.pachube.com/feeds/2058).

The Electricity and Temperature data is obtained from a 
[Current Cost CC128](http://www.currentcost.com/product-cc128.html) Smart Meter. It sends updates to software running 
on my Windows Home Server (Small Sensor Publishing Engine &#8211; a small service I wrote that monitors sensors and 
invokes publishers) box every 6 seconds. The software monitoring the CC128 then transmits this data to Pachube using 
 their data API. Pachube aggregates the data and provides the various charts and geographical information.