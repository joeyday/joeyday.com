---
title: "Generating optimal Bible reading plans"
date: '2020-12-09T22:31:14+00:00'
wp_id: 2986
wp_status: draft
wp_type: post
---

I'm working on an app to encourage myself to read the Bible more. I hesitate to call it a "daily" reading app because that's not exactly what it is (it's a lot less structured). I'm calling it "Ribbons" and I'll let you know when it's ready for prime time. Today's post is about how I solved the problem of dividing the Bible text into equal-length individual readings.

Let's say you want to read the book of Leviticus seven minutes at a time (twice a day, once a day, couple times a week, doesn't matter, just imagine you you want to read for about seven minutes each time you read). Average reading speed is 200 to 250 words per minute, so that's between 1,400 and 1,750 words in seven minutes. Leviticus, in the English Standard Version, has 23,438 words. If we divide it into fifteen readings they'll have an average of 1,563 words each, which is right in our desired range (a slower reader might read this in eight minutes, a faster reader in about six).

But how should we divide the text into fifteen readings? One really basic way to do it (and the way many Bible reading plans are actually done) is to count up how many chapters there are and divide that by fifteen. Leviticus has 27 chapters, which divides to 1.8 chapters per reading. If we prefer to start and stop reading at chapter breaks, this means following this basic plan we need to read two chapters some days and only one chapter other days. In fact, we need to read two chapters in twelve of the fifteen readings and one chapter in the other three readings. If we keep things very basic and read two chapters for the first twelve readings, the length of our readings looks like figure 1 below. Readings range from a short 893 words (about five minutes of reading) to one that is a whopping 3,394 words (about fifteen minutes), and the mean absolute deviation is 395 words.

[caption id="leviticus-divided-by-chapter-front-loaded" align="aligncenter" width="640"]<img src="/images/leviticus-divided-by-chapter-front-loaded.png" alt="Figure 1: Basic division by chapter, front-loaded" /> Figure 1[/caption]

Instead of loading all the shorter readings at the end, what if we even them out throughout the book? This seems at first to make sense, but actually we're just arbitrarily shifting the problem around. What if the last three chapters in Leviticus are actually the longest ones? Then picking those as our single-chapter readings will (accidentally) have the effect of evening out our readings. What if the last three chapters are the shortest? That will really throw things off! What if we happen to get lucky and every fifth chapter is the longest? Then dispersing them evenly throughout the text would slightly improve our readings. Turns out, evenly dispersing the single-chapter readings throughout our fifteen readings in Leviticus does eliminate the one terrible outlier in the previous set, giving us a range from 621 to 2,638, but we get a slightly worse mean absolute deviation of 445 words (see Figure 2). We get a couple readings that will only take us three minutes and a few that will take us more than ten.

[caption id="leviticus-divided-by-chapter-distributed" align="aligncenter" width="640"]<img src="/images/leviticus-divided-by-chapter-distributed.png" alt="Figure 2: Basic division by chapter, distributed" /> Figure 2[/caption]

To do better than this, it's clear we can't just keep picking which chapters to group together arbitrarily. We need to know something about the lengths of the individual chapters. I hit the ESV Bible API to analyze the text and compile my own data set on word counts for every chapter. Armed with this data, the most obvious change we can make is picking the three longest chapters to use as our single-chapter readings. (Footnote: We can't always do this, since it relies on things lining up just perfect. In Leviticus, the three longest chapters happen to fall in just the right places that we can pair off all the remaining chapters neatly.)

<!-- get stats and build chart for this one -->

But is it possible there are cases where counterintuitively grouping three or even four shorter chapters together might make them the same length as some of the longest single chapters? What is the best way to answer this question besides brute forcing it?

<!-- explain how I researched bin-packing before asking on Stack Overflow and someone suggested word wrap algorithms -->

One approach is a simple "greedy" algorithm. First, determine the maximum number of words you'd like to have in each reading. For the first reading, pull in the first chapter and make note of how many words it has. Then, if there's room left in the reading (if we haven't yet reached the maximum number of words we decided on per reading), pull the next chapter in. Keep pulling in more chapters as long as there's room, but when we run out of room, end that reading and start the next one. Continue this way until we've placed every chapter into a reading. Note that this algorithm isnâ€™t guaranteed to produce a specific count of readings, but we can keep choosing different maximum sizes per reading to coax it into dividing the text into our desired number of readings. The readings I generated this way are given in Figure 3. The range is considerably better at at 893 to 2,018 and so is the mean absolute deviation of 244 words.

[caption id="leviticus-greedy-by-chapter" align="aligncenter" width="640"]<img src="/images/leviticus-greedy-by-chapter.svg" alt="Figure 3: Leviticus divided along chapter breaks based on word count using a "greedy" algorithm" /> Figure 3: Leviticus divided along chapter breaks based on word count using a "greedy" algorithm[/caption]

You can see the greedy word wrap algorithm is indeed grouping three chapters together to form single readings in more than a few places. Notice how chapters 10, 11, and 12 are nearly the same length put together as chapter 13 is by itself. Now we're getting somewhere!

But can we do even better than this? It turns out thereâ€™s a better word wrap algorithm than the "greedy" one, but Iâ€™ll save that for the end because thereâ€™s one more way to optimize that Iâ€™d like to introduce first: splitting on section headings instead of chapter breaks.
