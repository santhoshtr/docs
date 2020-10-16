# Hyphenation

**What is Hiphenation?**

Hyphenation is the process inserting hyphens in between the syllables of a word so that when the text is [justified](http://en.wikipedia.org/wiki/Justification_%28typesetting%29), maximum space is utilized.

Hiphenation is an important feature that DTP softwares provide. For Indian languages there is no good DTP softwares available. XeTex is the only choice to work with unicode and professional quality page layout. But xetex and DTP are not exactly same. Inkscape can be used as temporary solution. But only for small scale works. There is a project going on to add Harfbuzz backend to Scribus, the freedomware DTP package.

Hiphenation is also requred in many other places. Actually it is required where ever we ‘justify’ a block of text in openoffice or any wordprocessors. Same is the case of webpages. If we justify a block of text in ml\_IN, let is see what is happening now

![](http://pics.livejournal.com/santhoshtr/pic/0000wd6p)

Note the long gaps between words. This is a screenshot taken from firefox. The default hiphenation just breaking the lines in space characters. And no doubt that it makes the pages ugly. The problem becomes worse if the length of the word is more and column width is less.

**Algorithm For Hiphenation**

The basic for all hyphenation algorithms is the hyphenation algorithm, designed by Frank Liang in 1983, which is adopted in TeX. [Wikipedia artcle of TeX](http://en.wikipedia.org/wiki/TeX#Hyphenation_and_justification) explain this with very simple example

> If TeX must find the acceptable hyphenation positions in the word encyclopedia, for example, it will consider all the subwords of the extended word .encyclopedia., where . is a special marker to indicate the beginning or end of the word. The list of subwords include all the subwords of length 1 \(., e, n, c, y, etc\), of length 2 \(.e, en, nc, etc\), etc, up to the subword of length 14, which is the word itself, including the markers. TeX will then look into its list of hyphenation patterns, and find subwords for which it has calculated the desirability of hyphenation at each position. In the case of our word, 11 such patterns can be matched, namely 1c4l4, 1cy, 1d4i3a, 4edi, e3dia, 2i1a, ope5d, 2p2ed, 3pedi, pedia4, y1c. For each position in the word, TeX will calculate the maximum value obtained among all matching pattern, yielding en1cy1c4l4o3p4e5d4i3a4. Finally, the acceptable positions are those indicated by an odd number, yielding the acceptable hyphenations en-cy-clo-pe-di-a. This system based on subwords allows the definition of very general patterns \(such as 2i1a\), with low indicative numbers \(either odd or even\), which can then be superseded by more specific patterns \(such as 1d4i3a\) if necessary. These patterns find about 90% of the hyphens in the original dictionary; more importantly, they do not insert any spurious hyphen. In addition, a list of exceptions \(words for which the patterns do not predict the correct hyphenation\) are included with the Plain TeX format; additional ones can be specified by the user.

For more details about the algorithm used in Openoffice [read](http://markmail.org/download.xqy?id=rwne7kf67ttyk62l&number=2) this paper by Nemeth Laszlo

