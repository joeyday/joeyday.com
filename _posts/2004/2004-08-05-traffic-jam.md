---
id: 71
title: 'Traffic Jam'
date: '2004-08-05T12:31:33+00:00'
author: joeyday
layout: post
guid: 'http://www.joeyday.com/2004/08/05/traffic-jam'
permalink: /index.php/2004/08/05/traffic-jam/
dsq_thread_id:
    - '1744275640'
categories:
    - essay
tags:
    - 'web design'
    - wiki
---

I always thought it would be fun to administrate a high-traffic website. Now that I have one, I’m not so sure anymore.

The “Homestar Runner Wiki”:http://www.hrwiki.org has been getting more and more popular over the past three months, going from 8.38 GB of bandwidth in April to 15.39 in June and 25.96 in July. It continually breaks it’s own records, acheiving 1.34 GB in a single day on August 3 (the previous record was 1.07 on July 20). Don’t take my opening statement too seriously. I really do love administrating such a fun site; it’s exciting to see the numbers jump like they have.

Unfortunately, because of the high traffic, we’ve been experiencing a lot of slowing and time-outs. On Monday, August 2, the site was down for almost half an hour because the server had to reboot, and it was simply timing out for most of the day (at least whenever I tried). I think the real killer was the new “Peasant’s Quest”:http://www.homestarrunner.com/disk4of12.html game. Check out our top 10 search engine phrases for the month so far:

\# peasant s quest (1535 searches, 11.3%)  
\# homestar runner (1167 searches, 8.6%)  
\# homestar wiki (876 searches, 6.4%)  
\# homestar runner wiki (514 searches, 3.7%)  
\# hrwiki (422 searches, 3.1%)  
\# peasant s quest faq (375 searches, 2.7%)  
\# peasant s quest guide (349 searches, 2.5%)  
\# peasant s quest walkthrough (294 searches, 2.1%)  
\# homestar (247 searches, 1.8%)  
\# homestarrunner wiki (241 searches, 1.7%)

Funny thing is, bandwidth isn’t the issue anymore. Recently, we’ve run into an entirely different brick wall: system resources. Due to scalability issues with “’Tavi”:http://tavi.sourceforge.net, the engine our wiki runs off of, we’ve finally made the decision to switch to “MediaWiki”:http://wikipedia.sourceforge.net. MediaWiki is the software used by the ever-popular “Wikipedia”:http://www.wikipedia.org. It should be much more suited to a high-traffic site, and will give us several features we’ve been wanting for a while, including better user management and category functions. In retrospect, I should’ve started out with a more trusted wiki engine, but I threw this all together quite haphazardly one slow October day last year, and I didn’t exactly have a broad vision for the future.

In the next few days we’ll probably open a pledge drive, too. Since mySQL is primarily what’s overworking the CPU (“some details”:http://www.cool-stu.com/archives/000015.html), we need to move our database to a dedicated server. Once we’ve taken care of the migration to MediaWiki and the new mySQL server, I think we’ll be in business for quite some time.

In the meantime, things are going to get a little bumpy…