---
id: 57
title: 'Mozilla Firefox 0.9'
date: '2004-06-16T10:28:37+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2004/06/16/mozilla-firefox-09'
dsq_thread_id:
    - '1744275142'
categories:
    - essay
tags:
    - critique
    - mozilla
---

I hesitate to write this review. I’m quite afraid that someone reading what I’m about to say might not want to try Firefox. Please don’t get the wrong impression. I absolutely love Firefox, and I whole-heartedly recommend it to \_everyone\_. The story below is simply what happened to me during an upgrade, and is not intended to reflect negatively on Firefox or the Mozilla Foundation in any way.

“Mozilla Firefox 0.9”:http://www.mozilla.org/products/firefox was released to the general public yesterday morning. I was so excited I could’ve wet my pants and not noticed. As soon as I knew it was available, I immediately went and downloaded it, taking care to check the release notes so I could avoid having a bad experience upgrading. Little did I know what was in store for me.

The “release notes”:http://www.mozilla.org/products/firefox/releases/0.9.html specify the following:

bq. \*NOTE\* – Do not install Firefox over the top of another Firefox installation. If you want to install Firefox 0.9 into the same folder that you had Firefox 0.8 in, uninstall Firefox 0.8 first. Upgrading will be fixed in a future release.

The release notes also specify that profile settings are now stored in the @Application Data/Mozilla/Firefox@ directory, rather than the @Application Data/Phoenix@ directory. In addition:

bq. If you were using Firefox 0.8 as your default browser prior to upgrading to Firefox 0.9, data from your profile will be copied into the new location. You can remove the old “Phoenix” folder at your leisure.

I followed all the noted precautions, but something must’ve gone wrong for me, because my profile settings certainly were not moved. I started using Firefox around version 0.6, so I’ve been through a couple of upgrades without any problems. My profile settings have always come through before. I figured it should be an easy matter to move (in retrospect, I should’ve copied) my profile settings from the old folder to the new and edit my @profiles.ini@ file, afterall, the release notes mentioned doing that (though now I realize that note was meant for people with a different, more specific problem).

All that seemed to accomplish was to break the display of certain key components of the browser, prompting me to believe that a few things have changed in the @chrome@ directory.

So, on the off chance that something had gone wrong during the install, I decided to move my profile settings back to the @Phoenix@ folder and reinstall Firefox 0.8. It took me a while to find the 0.8 install file, but upon installing it, my profile settings didn’t come back! It seems something in 0.9 had corrupted (upgraded) the settings so that 0.8 couldn’t read them.

Needless to say, I was quite ticked about the whole thing, since I have a number of bookmarks I need in order to perform my job functions.

I finally decided to start over with Firefox 0.9 (I had a co-worker send me many of the bookmarks I needed). I deleted all the leftover profile files, installed, and created a new profile from scratch.

The next step was to import the “Qute theme”:http://quadrone.org/projects/mozilla/browser/, since the new one is ugly as sin. The import simply didn’t work. “Qute” would flash up in the “Themes” window for a few seconds and then dissappear.

So I moved on to downloading my favorite extensions. I was able to download most of them, but upon downloading “Tabbrowser Extensions”:http://white.sakura.ne.jp/~piro/xul/\_tabextensions.html.en and restarting my browser, I started getting XML parsing errors. Turns out there isn’t a version of Tabbrowser Extensions for Firefox 0.9, yet.

At that point, I was steaming, but I uninstalled and reinstalled, then downloaded the rest of the extensions I use (being careful to check if they were compatible with 0.9 first). Everything seems to be working fine.

Things have improved markedly since yesterday. This morning I was able to successfully install the Qute theme, and they’ve made changes to the extension download website. Now it only shows extensions that are compatible with the version you are currently using, which should prevent people from downloading incompatible extensions and getting the same errors I experienced.

Though it would’ve been nice for these things to have been in place before releasing 0.9, it is wonderful to see how fast the Mozilla team has fixed them. It’s great to use a free (open source) browser that is updated often. If you are still using Internet Explorer, get your head out of the sand! Do you realize your browser is three years old and only getting older? Firefox is the way of the future.

For a list of updates in version 0.9, check out The Burning Edge’s “Bigger Picture”:http://www.squarefree.com/burningedge/bigger-picture.html. I’m especially tickled about the new extension and theme managers, update notifications, CSS3 opacity, the smaller download size (4.7 MB), and the 3% speed increase.