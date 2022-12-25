---
id: 308
title: 'Blah blah blah'
date: '2006-10-11T06:44:20+00:00'
author: joeyday
layout: post
guid: 'http://www.joeyday.com/2006/10/11/blah-blah-blah'
permalink: /index.php/2006/10/11/blah-blah-blah/
dsq_thread_id:
    - '1744278557'
categories:
    - essay
tags:
    - calibri
    - cambria
    - css
    - firefox
    - ie
    - ie6
    - ie7
    - Opera
    - safari
    - siteupdate
    - Typography
    - webdesign
    - xhtml
---

A few more notes about the new design, and then I’ll stop yakking about it; I promise. I’ve now tested the site in Internet Explorer 6, Internet Explorer 7 (rc1), Firefox 1.5, Firefox 2 (rc2), Opera 9, and Safari 1.2. It passes with flying colors in all browsers, with the exception of IE6, where it doesn’t actually look half bad—the layout itself is fine but the PNG images puke big bluish blocks all over where they should be transparent. Sometime down the road I may decide to replace all the PNGs with something else in IE6 (using conditional comments or some other such hack), but [IE7 is coming this month](http://blogs.msdn.com/ie/archive/2006/10/06/IE7-Is-Coming-This-Month_2E002E002E00_Are-you-Ready_3F00_.aspx) and will be a critical automatic update, so I’m not going to sweat about it too much.

Unbeknownst to me, the new design wasn’t at first valid XHTML and CSS. I took care of that this morning by properly closing a few &lt;li&gt; tags, fixing a few tag IDs, properly enclosing a couple of comment form elements inside a block level element, and fixing a few malformed CSS statements.

Last but not least, I should mention that the new design uses a couple of new fonts: Cambria and Calibri. Microsoft is releasing six new fonts with Windows Vista and many people (myself included) are hoping they become widely distributed enough to use them in web pages. If you don’t have these fonts, the new design properly degrades to using Georgia and Trebuchet MS instead, which I think looks pretty good, so you’re not missing out on much. To get the full effect, however, I recommend you download the new fonts if you can. They have been released unofficially to the public in the Vista betas and can be found on the web with a little effort.