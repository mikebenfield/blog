---
title: "Exploring Star Trek: The Next Generation with some word clouds"
date: 2016-11-21
draft: false
markup: "mmark"
---

## Introduction

I conducted a simple and fun exploration of the television show Star Trek: The
Next Generation (TNG). I used transcripts of the show and made word clouds for
each season and character. (I got the transcripts from the
excellent [Chrissie's Transcripts Site](http://www.chakoteya.net).)

As it turns out, the usual word clouds ranked by
frequency don't clearly distinguish between seasons or between characters
(*everybody* says "sir" all the time), so I created a type of relative word
cloud that rewards words that appear in a given season (or are said by a given
character) more than other seasons (or more than other characters).

In parsing transcripts, for the most part I considered a word to be a string of
two or more alphabetical characters. There were three exceptions: "jean-luc,"
"o'brien," and "la forge" are all words, since these are all names of prominent
characters on the show. I eliminated stop words (words that are extremely
frequent in the English language, like "the").

## Absolute word clouds by season

Here are word clouds displaying the most common words in each season of TNG.

### Absolute word clouds by season - the clouds

<div style="overflow: hidden;">

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_0.png">
<img src="cloud_0.png" alt="Season 1 word cloud" width="200"
height="200">
</a>
<figcaption>Season 1</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_1.png">
<img src="cloud_1.png" alt="Season 2 word cloud" width="200"
height="200">
</a>
<figcaption>Season 2</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_2.png">
<img src="cloud_2.png" alt="Season 3 word cloud" width="200"
height="200">
</a>
<figcaption>Season 3</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_3.png">
<img src="cloud_3.png" alt="Season 4 word cloud" width="200"
height="200">
</a>
<figcaption>Season 4</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_4.png">
<img src="cloud_4.png" alt="Season 5 word cloud" width="200"
height="200">
</a>
<figcaption>Season 5</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_5.png">
<img src="cloud_5.png" alt="Season 6 word cloud" width="200"
height="200">
</a>
<figcaption>Season 6</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_6.png">
<img src="cloud_6.png" alt="Season 7 word cloud" width="200"
height="200">
</a>
<figcaption>Season 7</figcaption>
</figure>
</div>

So far, nothing really stands out. They all look pretty similar. There sure is a
lot of "sir" and "captain" on Star Trek. Also, "data", "know", and "just." Maybe
it's mildly interesting that in seasons 3 and 6 "sir" doesn't completely
dominate the cloud.

## Relative word clouds by season

In order to more clearly characterize the differences between the seasons, I
generated a new set of what I'll call *relative word clouds*. These are not
ranked by simple word frequency. The ranking here is by a statistic I made up
which I'll call *modified frequency relative to total frequency*, and denote by
MFRTF. That is, for each season and each word $$w$$ among the 1000 most common
words (other than stop words) on the show, we have

$$\textrm{MFRTF}_w = \frac{N_w^{1.1}}{T_w} , $$

where $$N_w$$ is the number of times $$w$$ appears in this season, and $$T_w$$
is the number of times $$w$$ appears in the series as a whole.

This way words are highly ranked for a given season if they appear more often in
that season *compared to other seasons*. Moreover, due to the power 1.1, words
are ranked more highly if they appear more often (otherwise, if two words appear
only in Season 2, one twice and the other 20 times, they would both be ranked
equally).

I limit the search to the 1000 most common words (after eliminating stop words)
to avoid very rare words being highly ranked just because they only appeared in
one season.

I give no theoretical justification for this choice of statistic. I simply
experimented with a few different statistics and chose this one because it is
easy to understand and produces good results for these word clouds. Many other
statistics, including the commonly
used
[term frequency-inverse document frequency](https://en.wikipedia.org/wiki/Tf–idf) produce
results which still do not clearly distinguish between the seasons. (Note that
tf-idf also has no theoretical justification. It's just a statistic people have
found to be useful.)

Here we have the new word clouds.

### Relative word clouds by season - the clouds

<div style="overflow: hidden;">

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_0_relative.png">
<img src="cloud_0_relative.png" alt="Season 1 word cloud" width="200"
height="200">
</a>
<figcaption>Season 1</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_1_relative.png">
<img src="cloud_1_relative.png" alt="Season 2 word cloud" width="200"
height="200">
</a>
<figcaption>Season 2</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_2_relative.png">
<img src="cloud_2_relative.png" alt="Season 3 word cloud" width="200"
height="200">
</a>
<figcaption>Season 3</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_3_relative.png">
<img src="cloud_3_relative.png" alt="Season 4 word cloud" width="200"
height="200">
</a>
<figcaption>Season 4</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_4_relative.png">
<img src="cloud_4_relative.png" alt="Season 5 word cloud" width="200"
height="200">
</a>
<figcaption>Season 5</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_5_relative.png">
<img src="cloud_5_relative.png" alt="Season 6 word cloud" width="200"
height="200">
</a>
<figcaption>Season 6</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_6_relative.png">
<img src="cloud_6_relative.png" alt="Season 7 word cloud" width="200"
height="200">
</a>
<figcaption>Season 7</figcaption>
</figure>

</div>

As you can see, these word clouds much more clearly distinguish between the
seasons. I'll comment on a few of the prominent words (which will probably be
easily recognizable to most TNG fans). Tasha Yar is a character who appears only
in Season 1. Pulaski is a character who appears only in Season 2. The Season 2
episode "Elementary, Dear Data" features the character Data role playing as
Sherlock Holmes. Lal is a character who appears only in Season 3. Daimon is a
rank among the Ferengi. Reginald Barclay is a supporting character who appears
in some seasons but not others. Ditto Ro Laren. Spock from the original Star
Trek appears in one Season 5 episode. Two professors appear in Season 6:
Moriarty and Galen. Kahless is the Klingon Jesus. Spot is Data's cat.

## Absolute word clouds by character

Now I present absolute word clouds as spoken by each character. I've included
all the main characters as well as five supporting characters.

### Absolute word clouds by character - the clouds

<div style="overflow: hidden;">

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_PICARD.png">
<img src="cloud_PICARD.png" alt="Jean-Luc Picard word cloud"
width="200" height="200">
</a>
<figcaption>Jean-Luc Picard</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_RIKER.png">
<img src="cloud_RIKER.png" alt="William Riker word cloud"
width="200" height="200">
</a>
<figcaption>William Riker</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_DATA.png">
<img src="cloud_DATA.png" alt="Data word cloud"
width="200" height="200">
</a>
<figcaption>Data</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_LAFORGE.png">
<img src="cloud_LAFORGE.png" alt="Geordi La Forge word cloud"
width="200" height="200">
</a>
<figcaption>Geordi La Forge</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_TROI.png">
<img src="cloud_TROI.png" alt="Deanna Troi word cloud"
width="200" height="200">
</a>
<figcaption>Deanna Troi</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_CRUSHER.png">
<img src="cloud_CRUSHER.png" alt="Beverly Crusher word cloud"
width="200" height="200">
</a>
<figcaption>Beverly Crusher</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_WORF.png">
<img src="cloud_WORF.png" alt="Worf word cloud"
width="200" height="200">
</a>
<figcaption>Worf</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_WESLEY.png">
<img src="cloud_WESLEY.png" alt="Wesley Crusher word cloud"
width="200" height="200">
</a>
<figcaption>Wesley Crusher</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_TASHA.png">
<img src="cloud_TASHA.png" alt="Tasha Yar word cloud"
width="200" height="200">
</a>
<figcaption>Tasha Yar</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_PULASKI.png">
<img src="cloud_PULASKI.png" alt="Katherine Pulaski word cloud"
width="200" height="200">
</a>
<figcaption>Katherine Pulaski</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_GUINAN.png">
<img src="cloud_GUINAN.png" alt="Guinan word cloud"
width="200" height="200">
</a>
<figcaption>Guinan</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_BARCLAY.png">
<img src="cloud_BARCLAY.png" alt="Reginald Barclay word cloud"
width="200" height="200">
</a>
<figcaption>Reginald Barclay</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_RO.png">
<img src="cloud_RO.png" alt="Ro Laren word cloud"
width="200" height="200">
</a>
<figcaption>Ro Laren</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_Q.png">
<img src="cloud_Q.png" alt="Q word cloud"
width="200" height="200">
</a>
<figcaption>Q</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_O'BRIEN.png">
<img src="cloud_O'BRIEN.png" alt="Miles O'Brien word cloud"
width="200" height="200">
</a>
<figcaption>Miles O'Brien</figcaption>
</figure>

</div>

As with the absolute word clouds for seasons, there's nothing earth-shattering
here. All the Starfleet officers except Picard and Crusher say "sir" and/or
"captain" all the time. Geordi La Forge and Data are friends, so it makes sense
that Geordi says "data" a lot. But Data doesn't say "Geordi" nearly as often.

## Relative word clouds by character

Now I'll give the relative per-character word clouds. These are ranked using the
same statistic as the relative per-season clouds: MFRTF.

### Relative word clouds by character - the clouds

<div style="overflow: hidden;">

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_PICARD_relative.png">
<img src="cloud_PICARD_relative.png" alt="Jean-Luc Picard word cloud"
width="200" height="200">
</a>
<figcaption>Jean-Luc Picard</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_RIKER_relative.png">
<img src="cloud_RIKER_relative.png" alt="William Riker word cloud"
width="200" height="200">
</a>
<figcaption>William Riker</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_DATA_relative.png">
<img src="cloud_DATA_relative.png" alt="Data word cloud"
width="200" height="200">
</a>
<figcaption>Data</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_LAFORGE_relative.png">
<img src="cloud_LAFORGE_relative.png" alt="Geordi La Forge word cloud"
width="200" height="200">
</a>
<figcaption>Geordi La Forge</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_TROI_relative.png">
<img src="cloud_TROI_relative.png" alt="Deanna Troi word cloud"
width="200" height="200">
</a>
<figcaption>Deanna Troi</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_CRUSHER_relative.png">
<img src="cloud_CRUSHER_relative.png" alt="Beverly Crusher word cloud"
width="200" height="200">
</a>
<figcaption>Beverly Crusher</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_WORF_relative.png">
<img src="cloud_WORF_relative.png" alt="Worf word cloud"
width="200" height="200">
</a>
<figcaption>Worf</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_WESLEY_relative.png">
<img src="cloud_WESLEY_relative.png" alt="Wesley Crusher word cloud"
width="200" height="200">
</a>
<figcaption>Wesley Crusher</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_TASHA_relative.png">
<img src="cloud_TASHA_relative.png" alt="Tasha Yar word cloud"
width="200" height="200">
</a>
<figcaption>Tasha Yar</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_PULASKI_relative.png">
<img src="cloud_PULASKI_relative.png" alt="Katherine Pulaski word cloud"
width="200" height="200">
</a>
<figcaption>Katherine Pulaski</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_GUINAN_relative.png">
<img src="cloud_GUINAN_relative.png" alt="Guinan word cloud"
width="200" height="200">
</a>
<figcaption>Guinan</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_BARCLAY_relative.png">
<img src="cloud_BARCLAY_relative.png" alt="Reginald Barclay word cloud"
width="200" height="200">
</a>
<figcaption>Reginald Barclay</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_RO_relative.png">
<img src="cloud_RO_relative.png" alt="Ro Laren word cloud"
width="200" height="200">
</a>
<figcaption>Ro Laren</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_Q_relative.png">
<img src="cloud_Q_relative.png" alt="Q word cloud"
width="200" height="200">
</a>
<figcaption>Q</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_O'BRIEN_relative.png">
<img src="cloud_O'BRIEN_relative.png" alt="Miles O'Brien word cloud"
width="200" height="200">
</a>
<figcaption>Miles O'Brien</figcaption>
</figure>

</div>

These seem much more interesting and distinct. There's a lot here that I find
pretty funny. Riker's own name William dominates his cloud. Troi's cloud
prominently features "mother," "emotions," "felt," "angry," "sense," and "pain"
(she's the therapist on the ship). Wesley's biggest words are "mom" and
"thanks," which seems very appropriate. Prominent words for Geordi La Forge
include "yeah," "okay," and "hey." The greatest thing is that the most prominent
word in Barclay's cloud is "er" (he's always nervous and unsure of
himself). Although if you look closely, there's a little "er" in Picard's cloud
too.

(By the way, "number" appears prominently in Picard's cloud because he calls his
First Officer "Number One.")

Regardless of the funny bits, it really feels like each cloud is a peek into the
mind of the character. Beverly Crusher's got all kinds of medical and biological
terminology floating around (and "wes" is in there too); Worf's thinking about
Kahless and various weapons and his son Alexander; Q is thinking about the
universe, the galaxy, the continuum, and, of course, Jean-Luc.

## TNG vs. the world

Finally, I wanted to get a sense of which words are TNG words and which are
not. To that end, I did relative word clouds for TNG vs. the Brown corpus, a
collection of English language documents compiled in the 1960s intended to be a
representative sample of American English.

<div style="overflow: hidden;">

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_tng_relative.png">
<img src="cloud_tng_relative.png" alt="TNG word cloud"
width="200" height="200">
</a>
<figcaption>TNG</figcaption>
</figure>

<figure style="float: left; margin-right: 5px; margin-bottom:5px;">
<a href="cloud_brown_relative.png">
<img src="cloud_brown_relative.png" alt="Brown word cloud"
width="200" height="200">
</a>
<figcaption>Brown</figcaption>
</figure>

</div>

There's that "sir" again. Apparently the least Star Trek words include "state",
"american," "president," and "church." That makes perfect sense as Trek takes
place in the far future, where national divisions (and human religion) are a
thing of the past.

## Conclusion and future projects

I think the relative word clouds really distinguish the various seasons and
characters. Someone could object though that they don't necessarily
*characterize* the seasons and characters.

For instance, Lal appears in *one episode* of Season 3, and yet her name
dominates the relative word cloud for Season 3. Of course this is because her
name never appears in any other season. Maybe a metric other than MFRTF could
rank words higher if they appear in many episodes of a season.

If we want to think of the character relative word clouds as "a peek into their
minds," as I mentioned above, we can see a few imperfections. For instance, the
name "deanna" appears prominently in Riker's relative word cloud (Deanna Troi is
Will Riker's close friend and former lover), but the name "will" does not appear
in Troi's cloud.  This is probably because several other characters call Riker
Will, but most people call Troi by her last name -- including her friend Beverly
Crusher. Thus the MFRTF metric rewards Riker's Deanna because nobody else says
that, but doesn't reward Deanna's Will. It's not immediately clear how to
address that problem.

An obvious related project, which I'll probably tackle at some point, is to
repeat this project with another Star Trek series (Deep Space Nine maybe?). Or
hey, why not go crazy and do a series other than Star Trek?

I've also played with the idea of implementing a machine learning predictor that
guesses which season of TNG a given scene came from. This sounds fun but it's
not clear whether it could work well enough to be worthwhile. And to the extent
it did work, maybe the best algorithm wouldn't amount to much more than looking
for one of a handful of key words in a scene: "Pulaski" means Season 2, "Lal"
means Season 3, and so on.

<a href="https://twitter.com/share" class="twitter-share-button" data-show-count="false">Tweet</a><script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
