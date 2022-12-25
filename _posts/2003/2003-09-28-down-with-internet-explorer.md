---
id: 7
title: 'Down With Internet Explorer'
date: '2003-09-28T23:38:31+00:00'
author: joeyday
layout: post
guid: 'http://www.joeyday.com/2003/09/28/down-with-internet-explorer'
permalink: /index.php/2003/09/28/down-with-internet-explorer/
dsq_thread_id:
    - '1744278585'
categories:
    - essay
tags:
    - internetexplorer
    - 'web design'
---

I don’t know if it’s because I’ve been using Mozilla Firebird for the past month, or because I’ve been redesigning my site to be standards compliant, or if it’s some of the things I’ve read lately on [SitePoint](http://www.sitepoint.com) and [A List Apart](http://www.alistapart.com). It’s probably a combination of all three. At any rate, I don’t like Internet Explorer anymore — not one bit.

For starters, I just read about (and immediately fell in love with) the PNG graphic file format, which IE doesn’t support. PNG boasts a very slick little feature called alpha transparency. You might be saying, but wait, can’t you get transparency in a GIF? Sure, but you have to settle for binary transparency. What that means is that a pixel is either 100% transparent or 100% not. Alpha transparency means a pixel can be 50% transparent — or any other percentage you care to make it. This would allow whatever is behind the pixel to show through slightly. You don’t have to be a whiz web-designer to understand that you could create some cool effects with such a technology. What’s even better is that PNG has better compression, which means PNG’s are smaller than both JPG’s and GIF’s, making them *perfect* for web design.

PNG has been around since 1995, and every other browser in the world supports it. Actually, Internet Explorer does have partial support for PNG. It will load the image, but can’t handle the alpha transparency. You can see this effect with my new <q>Joey Day</q> logo in the top left corner of the page. If you are using IE, you’ll see a whitish colored box around the logo. In any other browser you’ll see the image seamlessly integrated with the background — shadowing, anti-aliasing, and all. IE was supposed to support PNG as of version 4.0, when Microsoft promised full support in a pre-release spec sheet. Now here we are four years after IE 4.0 came out and eight years after PNG was invented, and they still aren’t supporting it correctly.

Second, IE has crummy pixel rendering methods. It renders everything one pixel off from normal (normal being the way every other browser in the world renders things). This doesn’t make any difference if you aren’t worried about exact positioning of elements, and for the most part I’m not. However, I recently added a search box along the navigation bar, and I can’t quite seem to get it to look right in IE. I’ve got it positioned exactly 3 pixels from the top of the div in which it has been placed. In all other browsers this means it should be centered, and indeed, it looks great in Mozilla, Netscape, and Opera. However, IE is rendering it *four* pixels down. I’ll probably end up making the navigation bar a few pixels taller to give the box a little breathing room. I do like how it looks right now in Firebird, though. 🙁

Third, here’s a juicy tidbit: Microsoft just lost a lawsuit against a company called Eolas. Apparently, the owner of Eolas invented and holds several patents for plug-in architecture. What this means is that future versions of IE may not support quicktime movies, real one audio, acrobat reader, and even flash. Windows Media Player wouldn’t be affected because it could be built into IE and thus not be considered a plug-in. Depending on the complete outcome of the lawsuit, Microsoft may even be forced to send a patch through Windows Update that would cause current versions of IE to stop supporting plug-ins.

Here are a few articles about the lawsuit:

1\. <q>[How a patent suit by a technological David brought a Goliath judgment](http://seattletimes.nwsource.com/html/businesstechnology/2001739653_eolas220.html)</q>  
2\. <q>[IE patent endgame detailed](http://news.com.com/2100-1032_3-5074799.html)</q>  
3\. <q>[The patent fight that could disrupt the Internet](http://www.zdnet.com.au/newstech/ebusiness/story/0,2000048590,20278616,00.htm)</q>

Actually, the scary thing is that this isn’t just an IE problem. Eolas will be targeting other browser manufacturers next. Netscape will probably be their first target. Smaller browsers like Mozilla and Opera may be immune for at least a little while, but eventually all browsers may have to pay royalties to Eolas for the use of plug-in technology. Yikes. :S

\[Updated Feb. 9, 2004: Mozilla Firebird is now called [Mozilla Firefox](http://www.mozilla.org/products/firefox). I highly recommend you give it a try. Though it is still a preview release, it is already heads and shoulders above any other browser I’ve used.\]