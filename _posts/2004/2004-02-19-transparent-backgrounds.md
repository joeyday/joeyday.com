---
id: 51
title: 'Transparent Backgrounds'
date: '2004-02-19T14:05:31+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2004/02/19/transparent-backgrounds'
permalink: /index.php/2004/02/19/transparent-backgrounds/
dsq_thread_id:
    - '1744275480'
categories:
    - essay
tags:
    - 'web design'
---

==

<div style="position: relative; float: right; margin-left: 10px; width: 150px; height: 100px; border: 1px black solid; background: url('/images/flowers.jpg');"><div class="tintedwhite" style="position: absolute; top: 20px; left: 20px; width: 110px; height: 20px; padding: 20px 0px; text-align: center; border: 1px white solid; color: black;">*It’s Magic!*</div></div>==

I’ve written before about [alpha transparency in PNG images](/archives/individual/000475.php). I’ve always wanted to use the effect to give a semi-transparent background to divs on my site. Unfortunately, since IE can’t render PNGs properly, the appearance of the site would break for 90% of all Internet users.

I’ve been designing a new site for the Crimson Nights events that UPC sponsors, and I really wanted “cool factor”. So I went snooping and found [this](http://www.daltonlp.com/daltonlp.cgi?item_type=1&item_id=217). It’s a blog entry that describes a proprietary technique to load a PNG with full alpha-transparency in IE. It looks like this:

bq.. `.tinted {`  
`filter: progid:DXImageTransform.Microsoft.AlphaImageLoader (enabled=true, sizingMethod=scale, src='black75p.png');`  
`}`

*\[Note: everything from “filter” to the semicolon should be on a single line.\]*

p. Unfortunately, it is only supported by IE. To get other browsers to display the background, you simply use the standard background property, like this:

bq. `.tinted {`  
`filter: progid:DXImageTransform.Microsoft.AlphaImageLoader (enabled=true, sizingMethod=scale, src='black75p.png');`  
`background-image: url('black75p.png');`  
`}`

Unfortunately, as soon as you apply the standard background property you end up undoing all the hard work it took to convince IE to display the graphic properly. To overcome this difficulty, we need a way of passing something to all browsers except IE. Since IE is not compliant with standards, the solution is not very difficult. We simply add an [attribute selector](http://www.w3.org/TR/REC-CSS2/selector.html#attribute-selectors) to the tinted class. Since all of our tinted divs will use the class attribute, our new selector will always be applied in browsers that support attribute selectors, thus excluding IE. The final code looks like this:

bq.. `.tinted {`  
`filter: progid:DXImageTransform.Microsoft.AlphaImageLoader (enabled=true, sizingMethod=scale, src='black75p.png');`  
`}`

`.tinted[class] {`  
`background-image: url('black75p.png');`  
`}`

p. Since all the other major browsers (Mozilla, Mozilla Firefox, Netscape, and Opera) can read the second selector, they will apply the background image with full alpha-transparency and ignore the silly image filter that IE is dependent upon.

I’m excited to unveil the new site. I think I acheived the “cool factor” I was looking for.