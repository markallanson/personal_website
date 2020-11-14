---
id: 167
title: Databinding custom list to a ListView in WPF
date: 2006-05-01T01:16:32+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=167
categories:
  - Me
---
In order to save yourself hours of frustration, when writing a simple sample to test out data binding, please, please, please make sure that the class you are data binding to uses Properties instead of Fields.

<p align="left">
  If you use Fields, your data binding will not work, you will just get empty rows (rows will be there, just no data will be in them). As soon as you encapsulate those fields into a property, things will just magically start working.
</p>

<p align="left">
  Someone should write a big disclaimer in the documentation for Windows Presentation Foundation. If your data binding to a custom object is not working, then use Properties, Dummy!
</p>

<p align="left">
  Lesson Learned.
</p>