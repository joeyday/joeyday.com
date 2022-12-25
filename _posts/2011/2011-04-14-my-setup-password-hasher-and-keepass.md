---
id: 1599
title: 'My setup: Password Hasher and KeePass'
date: '2011-04-14T21:25:40+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/?p=1599'
permalink: /index.php/2011/04/14/my-setup-password-hasher-and-keepass/
dsq_thread_id:
    - '1744280750'
categories:
    - essay
tags:
    - keepass
    - my-setup
    - 'password hasher'
    - passwords
    - security
---

![Padlock](http://joeyday.com/wp-content/uploads/2011/04/padlock-150x150.jpg "Padlock") My friend Aaron recently blogged about an innovative way to generate and remember many passwords using convenient [password cards](http://pthree.org/2010/09/21/password-cards/). His post has inspired me to share my own method for randomizing my passwords across many sites. Let me say at the outset, though, I really like Aaron’s approach, and don’t mean to imply by this post that I think my approach is superior to his (in fact, for portability and forward compatibility, his solution is perhaps superior to mine). The point is to find a method that works and then discipline yourself to stick to it.

Let me start with a short story. You may remember that I used to be the proprietor of the [Homestar Runner Wiki](http://www.hrwiki.org) and its accompanying [discussion forum](http://forum.hrwiki.org). Well, there was some drama there one year (as there was every year and as there is with all online fora) and one of our members decided to start his own forum and tried to persuade other members to leave us and join him since we were so dumb and he was so cool. I almost signed up on his forum just to see what all the fuss was about, but before I got around to it, one of our forum’s moderators signed up on his site. Shortly after she signed up, he was able to retrieve her password from his own forum’s database, and, since she had used the same password for his site as she had used on our site, he was able to log into our site using her password.

Total chaos ensued. Using her moderator abilities, he was able to delete a significant chunk of our forum’s posts, though it was slow going because he had to delete the posts one at a time, and the activity was eventually noticed and blocked by one of our admins. I was mortified as I imagined what would have happened had I signed up there as I had been considering. He would’ve had much greater permissions to delete whole sections of the board much faster, and could have done a lot more damage. The take home lesson from this little story is obvious: no matter how secure you think any two sites are, don’t ever use the same password twice, or you risk a disgruntled administrator using your password from one place to log in somewhere else.

How ’bout you? Do you currently use the same password in many different places across the web? Imagine what someone could do if they were to obtain that password. Could they log into your e-mail and steal all your contacts? Your blog and delete all your posts? Your bank and transfer all your money to their secure off-shore account?

#### Password Hasher

[![Pasword Hasher](http://joeyday.com/wp-content/uploads/2011/04/passhash.png "Password Hasher")](http://wijjo.com/passhash/) Of course, managing unique passwords across hundreds of sites is no easy task. Enter [Password Hasher](http://wijjo.com/passhash/), an algorithm for generating secure passwords from a site tag and a master password. Since the passwords are regenerated using the same algorithm every time you need them, there’s no need to actually store the password anywhere. As long as you remember your master password and the tag you used for each site (the easiest way to do this is simply to use the domain name itself as the tag), you can regenerate the password whenever you need it.

A [Password Hasher Firefox extension](https://addons.mozilla.org/en-us/firefox/addon/password-hasher/) makes it easy to generate these passwords whenever you need them on your own computer (be it a Mac, PC, or Linux box), and a [JavaScript version](http://wijjo.com/passhash/passhash.html) of the same algorithm makes the system portable (say when you’re using a library computer or a friend’s computer, and don’t have your Firefox extension handy).

Not only does Password Hasher let you generate unique passwords for each of the sites you use, but it also makes it dead simple to use much more secure passwords than you normally would. I’ve set my default password length to significantly more than eight characters, and I make sure to use special characters on any sites that allow them. I rest easy knowing it is that much more difficult for any of my passwords to be cracked.

#### KeePass

[![KeePass](http://joeyday.com/wp-content/uploads/2011/04/keepass.gif "KeePass")](http://www.keepass.info) Now, once in a while I have need of passwords outside of my browser, where opening up my browser and firing up my Password Hasher extension is a bit impractical. For instance, user passwords for web servers, FTP passwords, instant messengers, &amp;c. For these kinds of outside-the-browser passwords, I supplement my security scheme with an open source multi-platform tool called [KeePass](http://keepass.info/).

KeePass has a nice password generator built in, but instead of generating your passwords on the fly each time you use them, your passwords get stored in a strongly encrypted master-password-protected database. I store this database on my [Dropbox](http://www.dropbox.com) and use [Portable Dropbox](http://forums.dropbox.com/topic.php?id=33387) and [Portable KeePass](http://portableapps.com/apps/utilities/keepass_portable) on my thumb drive for when I’m on the go, and this has worked very well for those passwords where Password Hasher just isn’t a good fit.

#### Drawbacks

I’ve been using Password Hasher and KeePass for a couple years now, and they continue to serve me well, but there are a few niggles. For one, I find myself using Google Chrome more and more on my Mac and PC, and of course there is no Firefox at all on my iPad and iPhone, so consequently I’m using the JavaScript version of Password Hasher more and leaving the more convenient Firefox extension behind.

Furthermore, on iPad and iPhone, there is simply no way to access my KeePass database, so I find myself either reading my passwords from my Mac or PC and typing them into my iPad or iPhone, or copying and pasting my password into [Simplenote](http://simplenoteapp.com/) on my Mac or PC and subsequently copying and pasting it out of Simplenote into the app or website on my iPhone or iPad. This is not exactly ideal—and of course this only works if I’m near my Mac or PC, and I rarely prefer to use my iPhone or iPad when I am—but until I find something better, it suffices. In light of this, though, I’m seriously considering replacing KeePass with [1Password](http://agilewebsolutions.com/onepassword), even despite my deep consternation about replacing an open tool with a proprietary one.

#### Conclusion

These days the only password I have memorized is my computer login password (I wish there was an easy way to copy and paste a password on an initial computer login screen, but oh well), but even that password is generated with Password Hasher, is not the same password I use anywhere else, and is changed on a regular basis. All my other passwords are either stored in KeePass or generated on the fly with Password Hasher.

I hope I’ve encouraged you to come up with a system to keep your passwords more secure and armed you with some tools to make this easy (though, if you think my system is too complicated, by all means, check out [Aaron’s](http://pthree.org/2010/09/21/password-cards/)). You never know what can happen on the world wide interweb series of tubes, and it’s always better to be safe than sorry. ![](http://joeyday.com/wp-content/uploads/2009/08/endmark.png "End mark")

#### See also

- [My setup: YubNub](/2007/08/20/my-setup-yubnub)