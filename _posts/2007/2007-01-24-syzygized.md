---
id: 560
title: Syzygized
date: '2007-01-24T13:25:39+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2007/01/24/syzygized'
dsq_thread_id:
    - '4473022944'
categories:
    - essay
tags:
    - avocation
    - blogging
    - export
    - foundation
    - import
    - 'joey day'
    - syzygy
    - wordpress
    - xml
---

My blogs have finally been combined into one. [WordPress 2.1](http://www.wordpress.org) was released a few days ago with a shiny new import/export feature (among other cool updates). Nothing could’ve been slicker about the migration. It was as easy as clicking a button on my other blog, then selecting the downloaded file and clicking a button on this blog. Not only are posts copied over, but complete comments, custom fields, and categories as well.

Actually, the description above is a bit simplistic. I had a harder time than I probably should’ve had. When you do the export, you get an XML file that contains all your blog data. My XML file was initially 10 MB, the problem being that most web servers will only let you upload a maximum of 2 MB over HTTP before throwing a time-out error. So at first I tried to think of ways to hack the import feature to look for a local file instead of an uploaded file (that way I could just upload the file to the server using FTP).

When I couldn’t figure that out, I decided to chunk the XML file out into 6 or 7 pieces under 2 MB each. This is no simple task, as the chunks have to be split in logical places and the header and footer info from the big file needs to be replicated across all the chunks. Anyway, as I was mucking around with these chunks, I started noticing that a good portion of the data was comment spam from my moderation queue. I went back to the old blog and deleted everything that was in the spam quarantine and re-exported. This time the file came out to 0.7 MB—I had over 9 MB of comment spam! With the file size cut down so considerably, the import became the simple one click operation I described above.

So, what should I do with joeyday.org? I’m positive it will one day be the home of my own non-profit philanthropic institution working to cure cancer or aids or the hiccups or something, but let me know if you have any good ideas for what purpose it might serve in the meantime.

Oh, and if you’ve got a little time, check out some of my classic posts from the old blog here at their new home:

\* [Is Paid Ministry Unbiblical?](/2005/06/03/is-paid-ministry-unbiblical)  
\* [The First Verb You Learn](/2005/03/03/the-first-verb-you-learn)  
\* [The Symbol of the Cross](/2005/03/02/the-symbol-of-the-cross)  
\* [What’s in a Name?](/2005/01/14/whats-in-a-name)