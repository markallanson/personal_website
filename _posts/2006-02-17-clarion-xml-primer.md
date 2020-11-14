---
id: 158
title: Clarion XML Primer
date: 2006-02-17T22:33:37+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=158
categories:
  - Tech
---
**Note:** _This post was originally written about 3 years ago (my XML knowdledge is significantly better now, I promise) but always stored as a draft, never finished nor published. In fact, I forgot it existed until I switched over to WordPress and imported all my Movable Type entries into WordPress. Given I have not used the Clarion development environment at all in well over 2 years I cannot vouch for it&#8217;s accuracy with relation to current Clarion releases. I will however publish it now as it may help someone, somewhere, despite being incomplete._

A large part of my job is to work with a development environment called Clarion, by [SoftVelocity](http://markallanson.net/wordpress/wp-admin/www.softvelocity.com). Despite its many problems, Clarion is a fantastic tempalted RAD tool that has native database drivers for a large amount of databases, and ODBC access to the rest. Recently a spec was approved that requires the transform of some of our data from our Time in Attendance program to a XML supported by a Payroll System.

The latest version, Clarion 6 (which is still in beta, in fact they have recently made available their Release Candidate 1) contains a number of XML template wrappers that allow the conversion of native Queues, Groups, Views and Files into XML. For a Clarion developer this dramatically simplifies the creation of XML as it allows you to work with data structures you use in everyday development, and wrap them to create your XML output. Unfortunately these templated wrappers also come with some quite major drawbacks as of RC1, the major being:

  1. You can either work in &#8220;attribute mode&#8221; or in &#8220;tag mode&#8221;, you cannot mix and match modes. 
    Any XML tag can contain any number of attributes that specify in more detail the type of information contained within a tag. If you are at all familiar with HTML you will know how attributes work and what they are for. Here are some examples of what Clarion can and can&#8217;t do with its templates, using a simple customer file as an example.
    
    <div class="code">
      <strong>Figure 1: Attribute Mode Example </strong><Customer LastName=&#8221;Allanson&#8221; FirstName=&#8221;Mark&#8221; /></p> 
      
      <p>
        <strong>Figure 2: Tag Mode Example</strong>
      </p>
      
      <p>
        <Customer><br /> <LastName>Allanson</LastName><br /> <FirstName>Mark</FirstName>;<br /> </Customer>
      </p>
      
      <p>
        <strong>Figure 3: Mixed Tag/Attribute Mode (Not Possible)</strong>
      </p>
      
      <p>
        <Customer type=&#8221;Simple&#8221;><br /> <LastName>Allanson</LastName><br /> <FirstName>Mark</FirstName><br /> </Customer>
      </p>
    </div>

  2. You cannot wrap nested Groups and Views to create multi-tiered XML files.Its not very often that you will want a single-tiered XML file, or rather, it won&#8217;t be long before you need to use multi-tiered XML files. Any time you need to represent a mix of data you will need more than one. For example, the following Clarion group structure cannot be represented within the constraints of the Group wrapper. For the purposes of this example I will add a ContactNumber data field. <div class="code">
      <strong>Figure 4: Nested Clarion Group Structure</strong>Customer GROUP<br /> Name GROUP<br /> First STRING(50)<br /> Last STRING(50)<br /> END<br /> ContactNumber STRING(20)<br /> END</p> 
      
      <p>
        <strong>Figure 5: Potential XML output (Not Possible)</strong>
      </p>
      
      <p>
        <Customer><br /> <Name><br /> <Last>Allanson</Last><br /> <First>Mark</First><br /> </Name><br /> <ContactNumber>555-2336</ContactNumber><br /> </Customer>
      </p>
    </div>

Note that there are more limitations than these two, however for the purposes of the specific XML export I had to perform, these were the two killers that caused the wrappers to be unusable. For more information on how the wrappers work, and the rest of the limitations please refer to the [Clarion XML Support Reference Guide](http://www.softvelocity.com/c6ea/pdf/c6cpxml.pdf) [www.softvelocity.com]

Since the use of the wrappers was a dead end I thought that it was game over for our XML interface, I would have to program a simple one myself. After some queries on the Clarion 6 XML newsgroup \[news:discuss.softvelocity.com\] (purchase of Clarion 6 Early Access is required) and some digging around inside the C6\LIBSRC directory I discovered that the higher level Clarion XML API&#8217;s actually make use of some as-yet undocumented lower level msxml (SAX) wrapper classes. These functions are undocumented to the point that you have to develop using only the inc files as your point of reference. Using these lower level API wrappers you can get the type of control of XML output that you need if you are going to develop non-trivial XML interfaces.

The lower level APIs provide access to the Document Object Model (DOM) via a number of different classes. The base class for most of these is the Node class. The three classes you will use more than any other are the Document, Element and Text classes. These classes are directly responsible for the the bulk of data content creation within the XML file itsself.

The Document class provides access to the collection of Elements (Tags) within the XML document, and provides the means to create new Elements, Texts aswell as providing access to detaching and attaching collections of Elements.

<div>
  Performing a simple XML export using the example Customer data structure
</div>

The Customer data structure I have been using to this point has been rather simple, and for the sake of this example it will stay that way. Instead of using a group as our customer data structure we will use a simple queue, and the intended output will be as per figure 3 above, a mixed tag/attribute XML file. To keep this example as simple as possible I have not split the code up into procedures, instead everything is coded inline. It would be possible to create your own simple wrappers that would make this code look a neater and nicer to use in a production environment.

The first step is to create a new Application, or Procedure that will perform the Export of our sample information. Once you have done this you need to Add the following lines of code into the Global Embeds of your application, inside the embed.

<div class="code">
  Include(&#8216;xmlclass.inc&#8217;)<br /> Include(&#8216;cpexml.inc&#8217;)
</div>

These two include files contain all the declarations needed to use the low and high level clarion API&#8217;s and wrappers with relation to XML. These are the two files you can look at to find procedure definitions so you know exactly what procedures are available to you. By including them in the Global Embeds you are making the procedures accessable to your entire application. If you only want specific procedures to have access to the XML API&#8217;s then you should place these two include lines inside the Local Data section of each procedure that will be making use of XML.

Next you need to declare a number of variables/objects that will be used to represent the XML file we are going to create. Most of these need to be created as References because the Clarion XML classes deal mainly with references. These declarations need to be placed inside the procedures Local Data section. As an alternative to delcaring the CStrings manually you could use the Clarion IDE Data section of your procedure. You cannot declare the rest of them using the IDE however because Clarion doesnt let you use the LIKE/Base Class combination data type with reference variables (From memory the IDE lets you do it but the compiler will give an error).

<div class="code">
  DOMImp &#038;DOMImplementation ! Used to create our initial DOM<br /> DOM &#038;Document ! Stores the entire Document Object Model<br /> DOMType &#038;DocumentType ! Stores the type of XML document<br /> Root &#038;Element ! Will store the Root element of the document<br /> eCustomer &#038;Element ! Will Store the Customer<br /> eTagName &#038;Element ! Will store the Name Tag<br /> eData &#038;Element ! Re-usable, will store various Tag Data<br /> tText &#038;Text ! Re-usable, will store tag data<br /> XMLWriter &#038;DOMWriter ! Used to write the DOM to a file<br /> TagName CString(255)! Used to assign Tag Names<br /> AttributeName CString(255)! Used to assign Attribute Names<br /> AttributeData CString(255)! Used to assign Attribute Data<br /> Command CString(10) ! Used to store misc commands passed to functions<br /> XMLFileName CString(255)! Used to assign the file we want to write to
</div>

The above declarations provide us with access to the Document Object Model, aswell as some objects that can be used to store various Elements (Tags) within the XML document. Note that in production code you would most likely use more generic functions hence not require so many Element objects. Due to the fact that the above classes are wrappers to the msxml API, all string based parameters need to be passed in as CStrings. Unfortunately this makes code a bit messier, but there is no way around this.

Many thanks to GÃ¸ran Thomassen for his help and example code that helped me wrap my brain around this without any documentation.

<!-- technorati tags begin -->

<p style="font-size: 10px; text-align: right">
  technorati tags: <a rel="tag" href="http://technorati.com/tag/Clarion">Clarion</a>, <a rel="tag" href="http://technorati.com/tag/Xml">Xml</a>, <a rel="tag" href="http://technorati.com/tag/Primer">Primer</a>
</p>