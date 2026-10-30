---
title: "LDS Linker regression tests"
date: '2009-12-21T10:37:48+00:00'
wp_id: 1042
wp_status: private
wp_type: post
---

<span style="color: #c00;">To ensure that things are working, click every link and make sure they don't give you an error. Plus, don't forget to test this with Passage Search mode, too!</span>

<h4>These lines test en-dash support verse ranges</h4>
Moroni 10:3-5, 6 â€” a hyphen
Moroni 10:3--5, 6 â€” two hyphens (WP Texturize turns these into an en-dash)
Moroni 10:3â€“5, 8 â€” a UTF-8 encoded en-dash
Moroni 10:3–5, 7 â€” a character entity reference (ndash)
Moroni 10:3–5, 10 â€” a character entity reference (#150)
Moroni 10:3–5, 10 â€” a character entity reference (#8211)
Moroni 10:3–5, 11 â€” a character entity reference (#x2013)

<h4>We shouldn't link book names by themselves</h4>
James E. Faust
John Piper
Captain Moroni

<h4>We shouldn't link references with exclamation points at the beginning</h4>
!Moroni 10:3-5
!Joseph Smith-History 1:1
!Joseph Smith-Matthew 1:1 â€” This one will still get a link if Holy Scripturizer is turned on; when in doubt, turn that plugin off and see what happens
!D&C 18:10, 15-16
I gave !Jacob 3 toys.



<h4>Various ways of linking to the Doctrine and Covenants</h4>
Doctrine and Covenants 1:37-38 â€” and
Doctrine & Covenants 8:2-3 â€” actual ampersand with spaces
Doctrine & Covenants 19:16-19 â€” character entity (amp) with spaces
Doctrine & Covenants 19:16-19 â€” character entity (#38) with spaces
Doctrine & Covenants 19:16-19 â€” character entity (#x26) with spaces
Doctrine&Covenants 8:2-3 â€” actual ampersand without spaces
Doctrine&Covenants 19:16-19 â€” character entity (amp) without spaces
Doctrine&Covenants 19:16-19 â€” character entity (#38) without spaces
Doctrine&Covenants 19:16-19 â€” character entity (#x26) without spaces
D & C 14:7 â€” actual ampersand with spaces
D & C 58:26-27 â€” character entity (amp) with spaces
D & C 58:26-27 â€” character entity (#38) with spaces
D & C 58:26-27 â€” character entity (#x26) with spaces
D&C 18:10, 15-16 â€” actual ampersand without spaces
D&C 58:42-43 â€” character entity (amp) without spaces
D&C 58:42-43 â€” character entity (#38) without spaces
D&C 58:42-43 â€” character entity (#x26) without spaces

<h4>Joseph Smithâ€”History</h4>
Joseph Smith-History 1:1 â€” actual hyphen without spaces
Joseph Smith--History 1:1 â€” two hyphens without spaces
Joseph Smith---History 1:1 â€” three hyphens without spaces
Joseph Smithâ€”History 1:1 â€” actual em-dash without spaces
Joseph Smith—History 1:1 â€” character entity (mdash) without spaces
Joseph Smith—History 1:1 â€” character entity (#151) without spaces
Joseph Smith—History 1:1 â€” character entity (#8212) without spaces
Joseph Smith—History 1:1 â€” character entity (#x2014) without spaces
Joseph Smith History 1:1 â€” space
JS-H 1:1 â€” actual hyphen without spaces
JSâ€”H 1:1 â€” actual em-dash without spaces
JS—H 1:1 â€” character entity (mdash) without spaces
JS—H 1:1 â€” character entity (#151) without spaces
JS—H 1:1 â€” character entity (#8212) without spaces
JS—H 1:1 â€” character entity (#x2014) without spaces
JSH 1:3 â€” no space

<h4>Joseph Smithâ€”History with spaces (can't decide whether I think these should work or not; probably not)</h4>
Joseph Smith - History 1:1 â€” actual hyphen with spaces
Joseph Smith â€” History 1:1 â€” actual em-dash with spaces
Joseph Smith — History 1:1 â€” character entity (mdash) with spaces
Joseph Smith — History 1:1 â€” character entity (#151) with spaces
Joseph Smith — History 1:1 â€” character entity (#0151) with spaces
Joseph Smith — History 1:1 â€” character entity (#8212) with spaces
JS - H 1:1 â€” actual hyphen with spaces
JS â€” H 1:1 â€” actual em-dash with spaces
JS — H 1:1 â€” character entity (mdash) with spaces
JS — H 1:1 â€” character entity (#151) with spaces
JS — H 1:1 â€” character entity (#0151) with spaces
JS — H 1:1 â€” character entity (#8212) with spaces

<h4>Joseph Smithâ€”Matthew</h4>
Joseph Smith-Matthew 1:1 â€” actual hyphen without spaces
Joseph Smith--Matthew 1:1 â€” two hyphens without spaces
Joseph Smith---Matthew 1:1 â€” three hyphens without spaces
Joseph Smithâ€”Matthew 1:1 â€” actual em-dash without spaces
Joseph Smith—Matthew 1:1 â€” character entity (mdash) without spaces
Joseph Smith—Matthew 1:1 â€” character entity (#151) without spaces
Joseph Smith—Matthew 1:1 â€” character entity (#0151) without spaces
Joseph Smith—Matthew 1:1 â€” character entity (#8212) without spaces
Joseph Smith Matthew 1:1 â€” space
JS-M 1:1 â€” actual hyphen without spaces
JSâ€”M 1:1 â€” actual em-dash without spaces
JS—M 1:1 â€” character entity (mdash) without spaces
JS—M 1:1 â€” character entity (#151) without spaces
JS—M 1:1 â€” character entity (#0151) without spaces
JS—M 1:1 â€” character entity (#8212) without spaces
JSM 1:3 â€” no space

<h4>Joseph Smithâ€”Matthew with spaces (can't decide whether I think these should work or not; probably not)</h4>
Joseph Smith - Matthew 1:1 â€” actual hyphen with spaces
Joseph Smith â€” Matthew 1:1 â€” actual em-dash with spaces
Joseph Smith — Matthew 1:1 â€” character entity (mdash) with spaces
Joseph Smith — Matthew 1:1 â€” character entity (#151) with spaces
Joseph Smith — Matthew 1:1 â€” character entity (#0151) with spaces
Joseph Smith — Matthew 1:1 â€” character entity (#8212) with spaces
JS - M 1:1 â€” actual hyphen with spaces
JS â€” M 1:1 â€” actual em-dash with spaces
JS — M 1:1 â€” character entity (mdash) with spaces
JS — M 1:1 â€” character entity (#151) with spaces
JS — M 1:1 â€” character entity (#0151) with spaces
JS — M 1:1 â€” character entity (#8212) with spaces

<h4>Miscellaneous test cases</h4>
4 Nephi 1:1
Official Declaration 1
OD 2
Article of Faith 3
Articles of Faith 4
A of F 4
A. of F. 8
Articles of Faith 1:4
Article of Faith 1:8
A. of F. 1:13
Moro 10: 3-5 â€” space after chapter
1Ne 3:7 â€” no space after volume number
1 Ne 3:7 â€” space after volume number

<h4>Complex verse ranges</h4>
1 Ne 3:7; 4:8
1 Ne 3:7, 4:8
1 Ne 3:7, 9
1 Ne 3:7-8, 10-12
1 Ne 3:7-8, 4:6-9
1 Ne 3-4
1 Nephi 3:1, 3, 5, 7, 9
1 Nephi 3:1-2, 4-5, 7-8, 10
1 Nephi 3:15-17, 3-4

(the verses below are for comparison of the above with Holy Scripturizer plugin)
Matt 3:7; 4:8
Matt 3:7, 4:8
Matt 3:7, 9
Matt 3:7-8, 10-12
Matt 3:7-8, 4:6-9
Matt 3-4
