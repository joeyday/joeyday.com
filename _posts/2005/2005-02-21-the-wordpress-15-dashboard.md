---
id: 136
title: 'The WordPress 1.5 Dashboard'
date: '2005-02-21T10:28:20+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2005/02/21/the-wordpress-15-dashboard'
permalink: /index.php/2005/02/21/the-wordpress-15-dashboard/
dsq_thread_id:
    - '1744275301'
categories:
    - essay
tags:
    - wordpress
---

I must say, the dashboard in WordPress 1.5 is a welcome addition. I’m not sure what all the hype is about, though, since Movable Type has had the same thing for as long as I can remember.

I had a few quibbles with how it was originally configured, so I’ve made a few modifications to mine.

First off, those news boxes were butt-ugly. I commented out the CSS that makes them ugly in `wp-admin/wp-admin.css`, and they are now a simple unordered list.

Second, the information presented was drastically unbalanced. They give you 23 WordPress news links, but only five of your most recent posts and comments. Plus, the site stats box is simply too narrow. I again edited the CSS to make the box 40% wide instead of 27%, and tweaked the `wp-admin/index.php` file so I get 15 of my recent posts and comments. I don’t know about you, but 30 of my links and 23 of theirs seems like a better balance to me.