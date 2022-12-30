---
id: 11
title: 'Relative Links for Dummies'
date: '2003-10-03T11:11:07+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2003/10/03/relative-links-for-dummies'
dsq_thread_id:
    - '1744278565'
categories:
    - essay
tags:
    - 'web design'
---

I’m feeling extremely stupid right about now. Here I am coding away in strict XHTML, and I just learned how relative links work. :O

Now, I sortof understood how relative links worked before, but I never used them because I never saw the usefulness of them. Relative links are meant to make it easier to move things around, but I always thought people who said that were smoking crack. If you move a page up or down a directory, all your relative links are broken! Consequently, I always preferred using static links for all of my content, like this:

bc. ![Avatar](http://joeyday.com/images/avatar.gif)

However, I just learned that the following relative link does the *exact* same thing no matter what level the current page is in the heirarchy:

bc. ![Avatar](/images/avatar.gif)

What I never knew is that there is a pretty clear distinction between a relative link that starts with a forward slash and one that doesn’t. The starting forward slash tells the browser to start at the root of the site. I can’t believe I never caught onto this before. Sheesh. 😮