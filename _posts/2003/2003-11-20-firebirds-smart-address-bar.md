---
id: 31
title: 'Firebird&#039;s Smart Address Bar'
date: '2003-11-20T23:44:04+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2003/11/20/firebirds-smart-address-bar'
permalink: /index.php/2003/11/20/firebirds-smart-address-bar/
dsq_thread_id:
    - '2089658859'
categories:
    - essay
tags:
    - mozilla
---

I used to think I knew all of the cool reasons to use Firebird, but I just discovered one more: Firebird has an extremely intelligent address bar.

For instance, type “microsoft.com” into your Internet Explorer address bar and the URL will quickly be corrected into “http://www.microsoft.com”. As you would expect, Mozilla Firebird behaves in the same manner. But type simply “microsoft” into your IE address bar and you’ll get an MSN Search page for the term microsoft. Type “microsoft” into Firebird’s address bar and it is appropriately changed to “http://www.microsoft.com”.

This also works for multiple word phrases. For instance, type “Joey Day” into Firebird’s address bar and you’ll get “http://joeyday.com”. It also works for .net and .org addresses for which there is no corresponding .com address. In other words, it defaults to .com, but if that doesn’t exist it will try .org and .net as well (I’m not sure which order though — haven’t done enough experimenting).

Another cool thing you can do involves what are called “keywords”. You can assign a keyword to any of your Firebird bookmarks. Then, you can simply type the keyword into your address bar instead of the whole URL. For instance, if you don’t particularly like typing “joeyday.com” into your address bar, you can give it the keyword “jd”, and save yourself from getting carpal tunnel (this obviously has more of an advantage for longer URLs, but as I write this I’m having trouble coming up with a long URL that I visit often).

Even better, Firebird has a handful of smart keywords built in. For instance, type “dict sesquipedalia” into the address bar and you’ll be taken straight to the definition of sesquipedalia at [dictionary.com](http://www.dictionary.com). This works for any word you can think of. Knowing that, you should be able to figure out what typing “google george bush” might do. You guessed it, it looks up George Bush on [Google](http://www.google.com). These and a few other smart keywords are located on your favorites bar under the folder “Quick Searches”.

You can create your own smart keywords fairly easily. All you do is alter the URL of your bookmark so that the special code, “%s”, is placed in the spot where you want the custom string to go. For instance, I created a smart keyword to look up Bible verses on [Bible Gateway](http://www.biblegateway.com). The standard URL for a scripture verse looks something like this:

bq. @http://www.biblegateway.com/cgi-bin/bible?passage=john+3:16@

I simply replaced the verse reference in my bookmark’s URL with the special string variable code like this:

bq. @http://www.biblegateway.com/cgi-bin/bible?passage=%s@

Then I set the bookmark’s keyword to be “bible”. Now I can look up Ephesians 2:8-9 by typing “bible eph 2:8-9”. I’ve also set up a smart keyword that uses Bible Gateway to find specific words in the Bible. As you can imagine, smart keywords can be used for millions of things.

You can read more about Mozilla’s smart keywords (with tips and ideas) at the following sites:

\# “[Netscape Devedge: Bookmark Keywords](http://devedge.netscape.com/viewsource/2002/bookmarks/)”  
\# “[How Cool Are Custom Keywords?](http://www.mozilla.org/docs/end-user/keywords.html)“