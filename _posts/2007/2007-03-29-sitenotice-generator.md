---
id: 651
title: 'Sitenotice Generator'
date: '2007-03-29T17:00:17+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2007/03/29/sitenotice-generator'
dsq_thread_id:
    - '1931369309'
categories:
    - essay
tags:
    - development
    - plugin
    - project
    - sitenotice
    - sitenotice-generator
    - wordpress
---

As far as I could tell, \[WordPress\] doesn’t have any kind of global [sitenotice feature](http://meta.wikimedia.org/wiki/Site_notice) like [MediaWiki](http://www.mediawiki.org), but I needed one to promote my upcoming ride in the [2007 MS Bike Tour](http://joeyday.com/2007/03/27/ms-bike-tour-07), so I wrote my own quick-and-dirty plugin.

I’m in the process of submitting this to [wp-plugins.org](http://www.wp-plugins.org) so I can start some more serious and stable development, but if you’d like to try it out in the meantime, feel free to download the alpha version:

\* [sitenotice-1.0alpha1.zip](http://downloads.joeyday.com/sitenotice-2.0.zip)  
\* [sitenotice-1.0alpha1.tar.gz](http://downloads.joeyday.com/sitenotice-2.0.zip)

To use the plugin, you’ll need to add a new template tag to an appropriate place where you’d like the sitenotice to appear when it’s enabled (I have mine right at the end of my header.php template file). The new tag is `<?php get_the_sitenotice(); ??>`. The plugin adds a new admin panel called “Sitenotice” to the WordPress options menu, from which you can edit the sitenotice message and configure other features.

This is alpha software, so if you install it, realize you’re using it at your own risk. If you do try it out, let me know if you have any feature requests or find any bugs I should squash! :syzygy: