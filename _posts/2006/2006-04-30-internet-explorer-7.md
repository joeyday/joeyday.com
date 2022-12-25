---
id: 198
title: 'Internet Explorer 7'
date: '2006-04-30T15:14:51+00:00'
author: joeyday
layout: post
guid: 'http://www.joeyday.com/2006/04/30/internet-explorer-7'
permalink: /index.php/2006/04/30/internet-explorer-7/
dsq_thread_id:
    - '2147585896'
categories:
    - essay
tags:
    - internetexplorer
---

<div class="rpic">[![Windows Internet Explorer 7](/images/ie7beta2.png)](http://www.microsoft.com/ie)</div>I took the plunge today and installed “Internet Explorer 7 Beta 2”:http://www.microsoft.com/ie. I tried it on a brand new desktop computer here at work first so I could test what the uninstall process was like. Turns out it’s completely painless. IE7 uninstalls and restores IE6 as if nothing ever changed.

I was also more than a little worried that it would break my “IE Tab”:http://ietab.mozdev.org/ extension in Firefox, but I was pleasantly surprised after installing to find that IE Tab still functions and even uses the IE7 rendering engine. Slick!

The only issue I encountered was that a few of the sites I need for work were failing because they didn’t recognize the IE7 user-agent string. I fixed that by spoofing the IE6 user-agent string using some registry keys. If you find yourself needing to do this, simply download the following registry entry files:

<div class="filetile">[![ie6ua.reg - Registration Entries File](/images/reg.png) ie6ua.reg](http://downloads.joeyday.com/ie6ua.reg)  
Registration Entries  
1 KB</div><div class="filetile">[![ie6ua-undo.reg - Registration Entries File](/images/reg.png) ie6ua-undo.reg](http://downloads.joeyday.com/ie6ua-undo.reg)  
Registration Entries  
1 KB</div>As should be self-explanatory, double-clicking the first file (ie6ua.reg) will edit your registry to spoof the IE6 user-agent string, while double-clicking the second file (ie6ua-undo.reg) will restore the default IE7 user-agent string.

I may write more about IE7 after I’ve used it for a bit. So far I’m not blown away. Don’t get me wrong, I think it’s a huge improvement over IE6, but nothing about it has really made me get up out of my chair or smack my forehead. It’s just another tabbed browser — no bells and whistles to set it apart from the crowd. But, as I said, give me a few weeks to play with it and maybe I’ll write up a formal review.