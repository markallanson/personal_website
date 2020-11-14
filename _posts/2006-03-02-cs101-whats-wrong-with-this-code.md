---
id: 164
title: 'CS101 &#8211; Whats wrong with this code?'
date: 2006-03-02T23:05:26+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=164
categories:
  - Tech
---
Today I stumbled across something similar to the following chunk of c# code.

<pre style="border-style: solid; border-color: silver silver silver navy; border-width: 1pt 1pt 1pt 2pt; padding: 0pt; background: white none repeat scroll 0% 50%; font-family: Verdana; font-size: 8pt; color: black; -moz-background-clip: -moz-initial; -moz-background-origin: -moz-initial; -moz-background-inline-policy: -moz-initial; margin-left: 20pt; margin-right: 20pt" class="code"><span style="color: teal">   19</span>         <span style="color: blue">private</span> <span style="color: blue">static</span> <span style="color: blue">void</span> DoStuff(<span style="color: blue">object</span> o)
<span style="color: teal">   20</span>         {
<span style="color: teal">   21</span>             <span style="color: green">// Do Some Work...</span>
<span style="color: teal">   22</span>             <span style="color: blue">object</span> newObject <span style="color: red">=</span> CheckObject(o);
<span style="color: teal">   23</span>             <span style="color: green">// More Work...</span>
<span style="color: teal">   24</span>         }
<span style="color: teal">   25</span>
<span style="color: teal">   26</span>         <span style="color: blue">private</span> <span style="color: blue">static</span> <span style="color: blue">object</span> CheckObject(<span style="color: blue">object</span> param)
<span style="color: teal">   27</span>         {
<span style="color: teal">   28</span>             <span style="color: blue">if</span> (<span style="color: red">!</span>(param <span style="color: red">==</span> <span style="color: blue">null</span>))
<span style="color: teal">   29</span>                 <span style="color: blue">return</span> param;
<span style="color: teal">   30</span>             <span style="color: blue">else</span>
<span style="color: teal">   31</span>                 <span style="color: blue">return</span> <span style="color: blue">null</span>;
<span style="color: teal">   32</span>         }</pre>

There is something wrong here&#8230;

  1. 5 points for leaving a comment with a more readable implementation.
  2. 5 points bonus points for also telling me what language the original author of this code most feels at home writing.

Interestingly the .net 1.1 c# compiler does not automatically optimize this code, I wonder why?

<span style="font-size: 65%">Disclaimer: Points cannot be exchanged for cash. Points have no material value and are actually worthless.</span>