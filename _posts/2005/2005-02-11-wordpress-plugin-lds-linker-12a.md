---
id: 498
title: 'WordPress Plugin: LDS Linker 1.2'
date: '2005-02-11T17:28:42+00:00'
author: Joey
layout: post
guid: 'http://www.joeyday.com/2005/02/11/wordpress-plugin-lds-linker-12a'
dsq_thread_id:
    - '1744279676'
categories:
    - essay
tags:
    - lds
    - lds-linker
    - plugin
    - scriptures
    - wordpress
---

*Notice: [A newer version of LDS Linker has been released](http://joeyday.com/to/lds-linker).*

**LDS Linker** is a WordPress plugin that changes any LDS scripture reference into a hyperlink pointing to the Internet Edition of the LDS Scriptures.

- Download the plugin: [lds-linker.1.2.1.zip](http://downloads.wordpress.org/plugin/lds-linker.1.2.1.zip)

It recognizes references whether the book name is written out or shortened using the [standard abbreviations](http://scriptures.lds.org/helps/abbrvtns). Here are some examples:

> Moro. 10:3-5 is a scripture mastery verse. Other scripture mastery verses include Mosiah 4:30, D&amp;C 130:22-23, and JS-H 1:15-20. I have Articles of Faith 1:1-13 memorized—how ’bout you?

This should be the last update for a while. I was able to reproduce the problem with D&amp;C references on a fresh WordPress install, and found that `&#038;` is another valid way to write `&#38;`. My code wasn’t catching that. I’ve also tested the plugin using several different fancy markup plugins. Things seem to be running smoothly in every configuration I have tested.

A big thanks to those who’ve helped me improve the code. Are *you* using **LDS Linker**? Please [let me know](/contact) what you think. ![End mark](http://joeyday.com/wp-content/uploads/2009/08/endmark.png "End mark")

*Edit Feb. 13 @ 9:59 pm: See my comment below for information on version 1.2.1.*