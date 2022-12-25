---
id: 631
title: 'See you later, spam!'
date: '2007-03-22T09:34:09+00:00'
author: joeyday
layout: post
guid: 'http://www.joeyday.com/2007/03/22/see-you-later-spam'
permalink: /index.php/2007/03/22/see-you-later-spam/
dsq_thread_id:
    - '1744278230'
categories:
    - essay
tags:
    - blacklist
    - catch-all
    - Email
    - forward
    - mail
    - personal
    - spam
    - whitelist
---

[![SPAM!](http://joeyday.com/wp-content/uploads/2007/03/spam.png)](http://www.spam.com)

When I first started hosting my own domain five or so years ago, I was happy to discover this really neat thing called a catch-all email account. Basically, I can set up as many static email addresses as I want or need, but any unrouted mail, no matter who it’s addressed to, is redirected into the main catch-all account.

This comes in handy for tracking who I’ve given my email address to (among other obvious reasons). For instance, if I were dealing with a fictional company called Wally’s Widgets, Inc., I might give them the address, *wallyswidgets@joeyday.com*. That way, if I start getting a lot of junk mail pointed to that address, I know it’s either coming from Wally’s Widgets, or Wally’s Widgets has sold my email address to the evil spammers. Over the years that’s happened with a few of the addresses I’ve given out, and when it does I simply add that address to a server side filter that bounces those emails.

Unfortunately, the spammers have developed new tactics in recent months. Perhaps as early as a year ago, I started getting a low volume of mail addressed to random names at my domain, like *joshua@joeyday.com* or *antony@joeyday.com*. I also started seeing strange addresses like *tjoey@joeyday.com* and *oey@joeyday.com* ((This is actually somewhat clever. It appears that when they get an address they know is legitimate, they are assuming either one of two scenarios: either (1) the address is a last name, and adding random letters of the alphabet to the front of it might allow them to stumble across other legitimate addresses, or (2) the address is a first letter and last name, and dropping the first letter or changing it to a different letter may help them stumble across more legitimate addresses. I’m confident this is what they’re doing, because I’ve had mail come to almost every address from *ajoey@joeyday.com* down to *zjoey@joeyday.com*.)). A few months later, really weird ones started coming in, like *ijjojkl@joeyday.com* and *zz3z22z3z1@joeyday.com*. The stranger they got, the more I realized my blacklist system wasn’t good enough anymore. As of last month, I was getting around a thousand junk emails a day to random addresses like these.

All this madness stopped as of last night, when I switched from using a blacklist system to using a forwarding whitelist. I compiled a hopefully comprehensive list of the 200 or so addresses I’ve given out over the years, created forwarding rules so each of them is redirected to my main account, and nuked the catch-all. As of this morning, I’ve got 72 junk emails in my account, which is a very happy improvement from the thousand I’ve been getting each day.

The main reason I’m blogging about this is to let friends and family know they can no longer make up random addresses to send me email. I’ve very much enjoyed getting mail to *awesomeguy@joeyday.com* over the years (that never actually happened, but a few similar ones did), but unfortunately that also must stop as of last night. I’d actually prefer to switch as much of my personal correspondence over to my Gmail account as possible. If you don’t know my Gmail address, feel free to shoot me an email using my [contact form](/contact) and (assuming I know who you are) I’ll be happy to give you my contact info.

Oh, and by the way, as I was searching for a good Spam image for this post, I came across [Spam’s official website](http://www.spam.com). It’s hilarious! [![](http://joeyday.com/wp-content/uploads/2009/08/endmark.png "End mark")](http://joeyday.com/wp-content/uploads/2009/08/endmark.png)