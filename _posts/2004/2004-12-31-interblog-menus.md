---
id: 120
title: 'Interblog Menus'
date: '2004-12-31T01:02:08+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2004/12/31/interblog-menus'
dsq_thread_id:
    - '2056380755'
categories:
    - essay
tags:
    - 'web design'
---

A “recent comment”:http://joeyday.com/2004/12/29/delicious#comments from “Winslow Oddfellow II”:http://winslowslair.supremepixels.net/:

bq. By the way, how did you get that InterBlog thinger on your sidebar?

That’s a good question. It’s actually kinda funny, since right now my “Avocation” blog is powered by WordPress and my “Foundation” blog is still running on Movable Type. They refer to each other with what appear to be identical menus, but they are almost as different as night and day.

To achieve the correct output in WordPress, I created an “interblog.php” file that contains the following code:

bq.. &lt;?php require(‘./wp-blog-header.php’); ?&gt;

&lt;h2&gt;&lt;a href=”http://joeyday.com”&gt;Avocation&lt;/a&gt;&lt;/h2&gt;  
&lt;ul&gt;  
&lt;?php $posts = get\_posts(‘offset=0’); foreach ($posts as $post) : start\_wp(); ?&gt;  
&lt;li id=”post-&lt;?php the\_ID(); ?&gt;”&gt;&lt;a href=”&lt;?php the\_permalink() ?&gt;” title=”Permanent Link: &lt;?php the\_title(); ?&gt;”&gt;&lt;?php the\_title(); ?&gt;&lt;/a&gt;&lt;/li&gt;  
&lt;?php endforeach; ?&gt;  
&lt;/ul&gt;

p. In Movable Type, I created a custom template called “tpl-interblog.inc”, which outputs a static file called “interblog.inc”. It looks like this:

bq.. &lt;h2&gt;&lt;a href=”http://www.joeyday.org”&gt;Foundation&lt;/a&gt;&lt;/h2&gt;  
&lt;ul&gt;  
&lt;MTEntries lastn=”5″&gt;  
&lt;li&gt;&lt;a href=”&lt;MTEntryLink&gt;”&gt;&lt;MTEntryTitle&gt;&lt;/a&gt;&lt;/li&gt;  
&lt;/MTEntries&gt;  
&lt;/ul&gt;

p. both of them get included from the other blog using nearly identical code:

bq. &lt;?php requre (‘http://joeyday.com/interblog.php’); ?&gt;

As you can see, it’s all pretty straightforward, but it took me a few minutes of head-scratching to figure it out. Hope this is useful for others who wish to refer to entries between multiple blogs.