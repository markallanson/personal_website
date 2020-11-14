---
id: 105
title: 'Asp.Net: Beware of the comment devil: How to save hours of time'
date: 2004-04-29T22:46:08+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=105
categories:
  - Tech
---
You are experiencing the following symptoms when trying to use an <asp:LinkButton> inside a Repeater, DataList or DataGrid.

<div>
  Javascript Error: Error On Page<br /> Line: 1<br /> Char: 1<br /> Error: Object Expected<br /> Code: 0<br /> URL: Your URL
</div>

When you place a LinkButton inside one of the databound repeating controls, asp.net generates a javascript function to deal with the OnClick event of each LinkButton it ends up placing on the page. (Note the number of LinkButtons will depend on how many items of data you are displaying)

<div>
  function __doPostBack(eventTarget, eventArgument) { &#8230; }
</div>

Please, oh please make sure that you have closed off all comments in your html <head> section. By failing to close off your comments in your head section you are effectively commenting out the javascript code that asp.net creates to handle your events on the Repeater/DataList/DataGrid Control. By commenting this function out it is now inaccessable during the processing of the OnClick event of the LinkButton, hence your page is broken.

Props to [Mun](http://www.munsplace.com "Muns Place") for helping me find this one.

Note: You can visit my [Marks Asp.Net Journals Post](http://www.markallanson.net/archives/000143.html "Mark's Asp.Net Journals") for an index of all the Asp.Net tips and tricks I have painfully learned during my Asp.Net Adventures.