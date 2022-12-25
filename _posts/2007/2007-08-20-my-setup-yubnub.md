---
id: 721
title: 'My setup: YubNub'
date: '2007-08-20T13:20:11+00:00'
author: joeyday
layout: post
guid: 'http://www.joeyday.com/2007/08/20/my-setup-yubnub'
permalink: /index.php/2007/08/20/my-setup-yubnub/
dsq_thread_id:
    - '1744278022'
categories:
    - essay
tags:
    - address-bar
    - command-line
    - efficiency
    - firefox
    - howto
    - internet
    - keyword
    - my-setup
    - productivity
    - rubnub
    - search
    - yubnub
---

[![YubNub logo](/wp-content/uploads/2007/08/yubnub.png)](http://www.yubnub.org "YubNub logo")

I’ve blogged before ([here](/2003/11/20/firebirds-smart-address-bar#more-31) and [there](/2003/12/10/ditch-your-google-toolbar)) about keyword searches in Firefox. Keyword searches are great because they allow you to perform searches right from your address bar. Simply type your keyword (e.g. I use `g` for Google, `a` for Answers.com, `wp` for Wikipedia, &amp;c.) followed by search terms and you’ll be magically whisked off to your search results. You can set up your own keyword for any site by right-clicking in any search bar and choosing “Add a keyword for this search” from the context menu. By setting up my own keyword searches, I’ve completely eliminated the need for the little search box to the right of my address bar, and, in fact, have removed it from my browser altogether.

Recently I discovered a service that takes this feature to the next level. [YubNub](http://www.yubnub.org), as the service is called, bills itself as a “(social) command line for the web,” and boy does it deliver. You can try the service out right away by going to the YubNub website, but it really becomes useful if you set it up directly in your address bar. I’ve got my Firefox address bar functioning as a YubNub command line, and I’ll mention later a few ways (and what I think is the best way) to do that. But first let me tell you more about the service.

#### What is YubNub?

YubNub is basically a shared repository for keyword searches. The community has already entered appropriate keywords for most of your favorite sites (`g`, `a`, and `wp` are already there, plus most of the others I was already using). So, say you’ve found a cool new site you want to be able to search with a keyword. Look it up in YubNub using the convenient `ls` keyword and chances are you’ll find someone else has already added it. If no one’s added it, you can create your own using the convenient `create` keyword.

The real power comes with being able to chain and pipe the various keywords into one another to create cool mashups and functions. This is where the command line paradigm fits in. Some of the more complex commands I’ve found do things like downloading and then zipping or unzipping files directly from the web (check out [`wobzip`](http://yubnub.org/kernel/man?args=wobzip) and [`kzip`](http://yubnub.org/kernel/man?args=wobzip)). Another potentially useful command, [`save`](http://yubnub.org/kernel/man?args=save), takes a URL and simply hands you back a lone hyperlink. This may not sound useful at first, but I can’t tell you how many times I’ve created a hyperlink in a wiki sandbox just so I can right-click and choose “Save As” to download an elusive mp3 or video file (you can’t just stick the URL in your address bar because that would stream the file in the browser rather than download it).

If all this sounds like it would benefit you—and believe me I’ve only scratched the surface of all the things you can do with it—let me give you a few ideas for integrating this with your browser.

#### What’s the best way to use YubNub?

YubNub works in all the major browsers, and there are some ideas for how to use it in your browser on the YubNub website on the [Installing YubNub](http://yubnub.org/documentation/describe_installation) page. I’ll be dealing with Firefox for the rest of this article, so if you use a different browser you’ll have to go there for ideas.

The most obvious option for Firefox is to put YubNub in the search box to the right of the address bar using the provided [search plugin](http://yubnub.blogspot.com/2005/10/installing-yubnub-in-firefox-detailed.html). Another way is the [YubNub Command Line](http://yubnubcommandline.mozdev.org/) Firefox extension, which places a YubNub bar across the bottom of your screen with various options for styling and auto-hiding it. While these are both useful, I don’t think they begin to approach the usefulness of integrating YubNub into the address bar itself. However, if you’re looking for something non-intrusive and safe, one of these should fit the bill.

One way to integrate YubNub directly into your address bar is using a Firefox extension called [RubNub for YubNub](http://rubnub.org/). This completely replaces your address bar with a YubNub command line. The problem I see with this is that it gives preference to YubNub commands and will only load something with the default behavior if it is obviously not a YubNub command. Maybe what I just said doesn’t make sense or doesn’t sound like it would be a problem, but I’ll give you an example in a moment.

The other way (and in my opinion the better of the two) requires tweaking a single Firefox setting. You simply open up `about:config`, search for a setting called `keyword.URL`, and set it to:

> `http://yubnub.org/parser/parse?command=`

This setting controls where Firefox sends address bar contents that it otherwise has no idea what to do with. In other words, if Firefox rules out the possibility of whatever you’ve typed being a URL or a Firefox keyword, it will pass off the string to this address. Now, did you catch what I just said? If what you’ve typed into the address bar matches a keyword search you’ve set up in Firefox, this will execute that search rather than passing it through to YubNub.

What’s cool about this is it gives you a built-in way to override YubNub commands. For instance, the `flix` command in YubNub executes a [Netflix](http://www.netflix.com) search. I don’t use Netflix, but instead have the `flix` keyword set up in Firefox to search [Flixster](http://www.flixster.com), a movie-themed social networking site. With this solution, my `flix` keyword overrides YubNub’s, whereas with RubNub I wouldn’t have had that ability.

#### Conclusion

So there you have it, a brief introduction to the YubNub service and what I think is the best way to integrate it with Firefox. Let me know if you start using it or if you already use it and have any additional tips or tricks. I’m especially interested in discovering useful commands, so let me know if you have any favorites. Happy YubNubbing! ![End mark](http://joeyday.com/wp-content/uploads/2009/08/endmark.png "End mark")