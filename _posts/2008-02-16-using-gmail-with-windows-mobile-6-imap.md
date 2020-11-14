---
id: 228
title: Using GMail with Windows Mobile 6 IMAP
date: 2008-02-16T23:04:39+00:00
author: Mark
layout: post
guid: http://markallanson.net/wordpress/?p=228
categories:
  - Me
  - Stuff
  - Tech
---
If you are a software engineer then most likely you subscribe to a number of email lists, or get regular daily / periodical email updates that can clog up your email inbox.Â  Also most likely you use Outlook, connected via POP to download your email, and have a myriad of rules that move messages into folders to keep everything as organized as possible.

Late last year I moved email hosting for @markallanson.net emails over to [Google Apps For Your Domain](http://google.com/a "Google apps for your domain") in order to make use of GMails excellent online client, search ability and also to ensure reliable and \*fast\* email access both online and offline. When I switched to Google Apps I altered my Outlook client to use POP to download the mail, and kept all of my rules in Outlook. This has been working perfectly since, but a few weeks ago I got myself a [HTC Touch Dual](http://www.europe.htc.com/en/products/htctouchdual.html "HTC Europe - Touch Dual") and wanted to get it to sync with my mail hosted on Google.

Ever since moving to Google Apps and using their online client the one thing that bugged me was that all mailing lists appeared in my main inbox. I switched outlook to connect via IMAP and sure enough the same thing happens, all emails were being synchronized to the single inbox folder. I synchronized Windows Mobile on the Touch Dual via IMAP and the same thing happens, as expected. The noise is too much to deal with on a mobile device so it&#8217;s time to start categorizing email &#8211; but on the server side in GMail &#8211; not using Outlook.

GMail supports filters and labels for categorizing email. You can tag an email with as many labels as you like and then view slice and dice via a labels. When tagging an email with a GMail label it appears in Outlook as a separate folder. The same thing happens on your windows mobile device. I tagged all emails from the WiX-Users mailing list and a WiX-Users folder appears in Outlook and Windows Mobile. Unfortunately however the same email also stays in your inbox and the noise is still there.

GMail also allows you to perform actions on arriving email in a similar way to Outlook rules so assigning labels automatically upon email arrival was trivial using the Filters functionality. Still this does not solve the noise problem.

In order to remove the noise, there is an option you must set on each incoming message filter. Once the filter criteria has been set up you must also check the box that tells GMail to archive the email once the filter has been applied.Â  Now archiving to me originally sounded like too much of a &#8220;Final&#8221; operation, so I ignored the option, but in effect ticking the archive box just removes it from your inbox. The labels applied via the filter are still usable, and the email can still be searched, but the noise is removed from the inbox.

So, to have a usable version of your email on WinMo6 via GMail you need to do the following.

  1. Switch to using IMAP to synchronize Windows Mobile and GMail.
  2. Move your Outlook rules into GMail, adding a Filter for each rule, and applying labels in order to categorize.
  3. Ensure that your filters archive all email that is labeled to remove it from the inbox as part of the filtering process

One final thing: When you set up a sync in Windows Mobile by default only the last N days of headers are synced from the server. I had some emails that I needed to have available at all times, such as all emails relating to my upcoming trip to Florida. The way I did this was to apply a Holiday\_Orlando label to each of the emails that I needed to have on the phone always. At the next sync Windows Mobile created a new folder called Holiday\_Orlando with no messages (none were newer than 3 days). I then had to modify the Holiday_Orlando folder synchronization options to add an override for that folder which told it to sync all messages in the folder.Â  Voila, all messages about the vacation are now available, with their attachments!

God knows how non-techies are supposed to ever figure this stuff out! (and apologies for the random rambling format of this post, I just \*had\* to write this down for others wanting to do the same thing.)