---
id: 127
title: Cleaning up your Xml Serialization output
date: 2004-12-07T22:18:17+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=127
categories:
  - Tech
---
Serialization is a great thing, except when you can&#8217;t get it to do what you want it to do. Case in point: I was serializing a small class that was going to be farmed off to a logger, which took the data and stored it in a logging database sitting on SQL Server. If you have ever done any serialization before, you will know that when you use the System.Xml.XmlSerialization.XmlSerializer to serialize a class you get a number of artifacts in the resultant xml, something along the lines of that below: (note I was serializing a class called ContextItem)

<pre class="cf">&lt;?xml version="1.0" encoding="utf-16" ?&gt;
&lt;ContextItem
xmlns:xsd="http://www.w3.org/2001/XMLSchema"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
MatchRule="0"
TimeStamp="2004-12-06T12:39:42.0951250-00:00"
FixType="Retry"
FixTime="2004-12-06T12:39:42.0951250-00:00"
RetryCount="1" /&gt;</pre>

The artifacts are the xml processing instruction as the root node of the serialized class, and the declaration of the xsd and xsi namespaces within the ContextItem node.

In the case above, serialization was done using an System.Xml.XmlTextWriter combined with the XmlSerializer, and the artifacts are due to a combination of the two working together. The Xml processing instruction is placed in the resultant output by the XmlTextReader, and the xsd and xsi namespace delcarations are placed in the resultant output by the serializer.

<pre class="cf">public static string Serialize(ContextItem i)
{
// Write the serialized result to a string builder
XmlSerializer serializer = new XmlSerializer(typeof(ContextItem));
StringBuilder sb = new StringBuilder();
StringWriter sw = new StringWriter(sb);
XmlTextWriter tw = new XmlTextWriter(sw);

// get rid of xml Processing Instructon declaration
tw.Formatting = Formatting.None;
tw.WriteRaw(String.Empty);

// get rid of xsd/xsi declarations
XmlSerializerNamespaces xsn = new XmlSerializerNamespaces();
xsn.Add(String.Empty, String.Empty);

// serialize and return the result
serializer.Serialize(tw, i, xsn);
return sb.ToString();
}</pre>

**Removing the xml processing instruction**

Seeings as the XmlTextReader is responsible for writing the xml processing instruction at the top of the above document the trick here is to fool it into not writing the xml processing instruction. This is done by lines 6 and 7 in the above code snippet. Setting the formatting just tells the XmlTextWriter not to apply any type of formatting to the output document (the serialized output will be one long string). Line 7 however, puts the XmlTextWriter current node into mixed mode (the node can contain both text and child xml nodes), therefore causing the xml processing instruction not to be output.

**Removing the xsd and xsi namespace declarations**

I am not sure if the method I have used to remove the xsd and xsi declaraions is actually embedded in the implementation of the XmlSerializerNamespaces class or if it is an unintended side effect of the implementation. Maybe [Dare](http://www.25hoursaday.com/weblog/ " Dare Obasanjo aka Carnage4Life") could clear this up?

An overloaded method of the XmlSerializer.Serialize() function takes a third argument, specifically an XmlSerializerNamespaces object which is normally used as a container for a collection of namespaces and prefixes to use in the serialization of the object. To remove the xsi and xsd namespace declarations you need to create an empty XmlSerializerNamespaces class and add a single entry, specifying an empty namespace prefix and namespace uri as shown in lines 110-111 in the above sample.

Output after these two operations cleans up the xml nicely, ready for logging into a SQL server thousands of times if required. Final output is shown below.

<pre class="cf">&lt;ContextItem
MatchRule="0"
TimeStamp="2004-12-06T12:39:42.0951250-00:00"
FixType="Retry"
FixTime="2004-12-06T12:39:42.0951250-00:00"
RetryCount="1" /&gt;</pre>