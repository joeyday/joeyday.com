---
title: Interblog Menus
date: 2004-12-31T01:02:08+00:00
author: Joey
categories:
  - essay
tags:
  - web design
id: 120
guid: http://www.joeyday.com/2004/12/31/interblog-menus
dsq_thread_id:
  - "2056380755"
---

A [[2004-12-29-delicious#comments|recent comment]] from [Winslow Oddfellow II](http://winslowslair.supremepixels.net/):

> By the way, how did you get that InterBlog thinger on your sidebar?

That’s a good question. It’s actually kinda funny, since right now my “Avocation” blog is powered by WordPress and my “Foundation” blog is still running on Movable Type. They refer to each other with what appear to be identical menus, but they are almost as different as night and day.

To achieve the correct output in WordPress, I created an “interblog.php” file that contains the following code:

```
<?php require('./wp-blog-header.php'); ?>

<h2><a href="http://joeyday.com">Avocation</a></h2>
<ul>
<?php $posts = get_posts('offset=0'); foreach ($posts as $post) : start_wp(); ?>
<li id="post-<?php the_ID(); ?>"><a href="<?php the_permalink() ?>" title="Permanent Link: <?php the_title(); ?>"><?php the_title(); ?></a></li>
<?php endforeach; ?>
</ul>
```

In Movable Type, I created a custom template called “tpl-interblog.inc”, which outputs a static file called “interblog.inc”. It looks like this:

```
<h2><a href="http://www.joeyday.org">Foundation</a></h2>
<ul>
<MTEntries lastn="5">
<li><a href="<MTEntryLink>"><MTEntryTitle></a></li>
</MTEntries>
</ul>
```

both of them get included from the other blog using nearly identical code:

```
<?php requre ('http://joeyday.com/interblog.php'); ?>
```

As you can see, it’s all pretty straightforward, but it took me a few minutes of head-scratching to figure it out. Hope this is useful for others who wish to refer to entries between multiple blogs.
