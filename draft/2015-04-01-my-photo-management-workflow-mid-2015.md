---
title: "My photo management workflow, mid-2015"
date: '2015-04-01T22:21:49+00:00'
wp_id: 2736
wp_status: draft
wp_type: post
---

When I take photos on my iPhone, they are immediately background-uploaded to three cloud services:
<ul>
	<li>iCloud Photo Library</li>
	<li>Picturelife</li>
	<li>Amazon Cloud Drive</li>
</ul>

Whenever I think about it (once or twice a month) I open the Photos app on my Mac and drag and drop the latest bunch of photos into ~/Pictures/Staging. Then I run a Bash script that rsyncs those files over to our household network attached storage (NAS) drive.

Hazel to sort them.

Bash script to rsync the whole kit and caboodle back to my Mac.

SyncBack to automatically sync the whole kit and caboodle to my wife's PC.

Several automatic cloud backup and/or photo management services are also running on my Mac:
<ul>
	<li>Backblaze</li>
	<li>Picturelife</li>
	<li>Amazon Cloud Drive</li>
</ul>

At the end of this, with very little interaction from me, my precious family photos are in seven+ places:
<ul>
	<li>Our network attached storage (I consider this the canonical place)</li>
	<li>My Mac</li>
	<li>My wife's PC</li>
	<li>Backblaze</li>
	<li>iCloud Photo Library</li>
	<li>Picturelife</li>
	<li>Amazon Cloud Drive</li>
</ul>

Todo: Videos. Right now my videos only live in iCloud and our NAS, and my wife's videos only live in the NAS.
