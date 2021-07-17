# Web Typography

## **Font size**

16px or 12pt is the recommended size for body text. But do not set this value in pixels or points. Set it as 100%. `font-size: 100%;` In most browsers, this defaults to 16 pixels. Inheriting the base font size from browsers allow users to use browser preference to set their comfortable font size.

![Firefox settings for default font size.](../../.gitbook/assets/image%20%2898%29.png)

Then we can use other relative units \(`em` or `rem`\) to set font sizes for other elements. This is crucial because it means that changing the base font size will also change all other font sizes.

The body text of the page should respect the browser setting.\(Note: [Wikipedia does not do that](https://phabricator.wikimedia.org/T254055), even though [it is recommended in style guide](https://design.wikimedia.org/style-guide/visual-style_typography.html#use-of-styles)\)

As per [https://accessibility.digital.gov/visual-design/typography/](https://accessibility.digital.gov/visual-design/typography/):  **Use a large enough font size for body text so that people can comfortably read.** Use at least an effective size of 16px, but this can vary depending on the design of the font.

### **Accessibility**

* At age 40, only half the light gets through to the retina as it did at age 20. For 60-year-olds, it’s just 20%. People in their 60s need three times more light for comfortable reading than those in their 20s\([Reference](https://newsinhealth.nih.gov/special-issues/seniors/your-aging-eyes)\)
* [Nearly 9%](http://www.who.int/blindness/table/en/index.html) of Americans are visually impaired, meaning their vision cannot be completely corrected with lenses.
* Most people, when sitting comfortably, are [about 20 to 23 inches](http://www.eyefatigue.com/cvs-computer-glasses.asp) from their computer screens. In fact, 28 inches is the recommended distance, because this is where [vergence](http://en.wikipedia.org/wiki/Vergence) is sufficiently low to avoid eye strain. This is much further than the distance at which we read printed text — most people do not hold magazines at arm’s length!\([source](https://www.smashingmagazine.com/2011/10/16-pixels-body-copy-anything-less-costly-mistake/)\)
* 16-pixel text on a screen is [about the same size](http://www.informationarchitects.jp/en/100e2r/) as text printed in a book or magazine; this is accounting for reading distance. Because we read books pretty close — often only a few inches away — they are typically set at about 10 points. If you were to read them at arm’s length, you’d want at least 12 points, which is about the same size as 16 pixels on most screens:\([source](https://www.smashingmagazine.com/2011/10/16-pixels-body-copy-anything-less-costly-mistake/)\)
* People don't zoom. The people who most need to increase font size are people 65+, which is the group least-likely to be skilled enough to have adjusted settings.\([source](https://www.nngroup.com/articles/guesses-vs-data/)\)

### **Links**

* [https://type-scale.com/](https://type-scale.com/) A tool to try and choose a scale rhythm\(ratio of typeface sizes used for headings, body content
* Tim Brown’s [modular typeface scales concept](https://alistapart.com/article/more-meaningful-typography/)
  * [Modular Scale](https://www.modularscale.com/)
  * A set of js, css, sass libraries to implement this - [https://github.com/modularscale](https://github.com/modularscale)
  * Typesetting body text - Talk by Tim brown [https://vimeo.com/156203722](https://vimeo.com/156203722)
* using musical scales for better scale harmony - Owen Gregory [Composing the New Canon: Music, Harmony, Proportion](https://24ways.org/2011/composing-the-new-canon) 

## **Script characteristics**

Depending one the script characteristics, specifically the nature of glyphs in the scrpt, latin defaults for font metrics will need adjustments. Following are two script classification based on glyphs.

### **Tall scripts** 

 Language that require extra line height to accommodate larger glyphs, including South and Southeast Asian and Middle Eastern languages ****listed below\(incomplete\).

* ar - Arabic
* bn- Bengali
* ml- Malayalam - This script has vertical stacking and the line height-font size ratio should be chosen to avoid parts of it not chopped off.
* fa- Persian
* gu- Gujarati
* hi - Hindi
* mr - Marathi
* as - Assamese
* kh - Khmer
* kn- Kannada
* my-Myanmar
* ne - Nepali
* pa-Panjabi
* si -Sinhala
* ta-Tamil
* te-Telugu
* th-Thai
* ur-Urdu
* ko-Korean - The height is mostly same as Latin but the density of glyphs are higher. Slightly higher linespacing expected
* vi -Vietnamese - Even though the script used is latin, it has many diacritic marks that are specific to vietnamese.
* bo-Tibetan - This script has multi level vertical stacking and no word spacing. [bo.wikipedia.org](https://bo.wikipedia.org) increased the default font size to 125%\(20px\) using [custom styling](https://bo.wikipedia.org/w/load.php?debug=1&lang=bo&modules=site.styles&only=styles&skin=vector)

### Dense scripts

Scripts with glyphs having more complex strokes in comparison with latin need larger font size for legibility. Chinese, Indic scripts are some examples. Most of these scripts are legible in 12pt or 16px. Anything below makes them hard to read

* bn- Bengali - Glyphs are very dense with strokes joining in accute angles. Need minimum 12pt/16px font size. [Script example](https://bn.wikipedia.org/wiki/%E0%A6%B6%E0%A7%87%E0%A6%96_%E0%A6%AE%E0%A7%81%E0%A6%9C%E0%A6%BF%E0%A6%AC%E0%A7%81%E0%A6%B0_%E0%A6%B0%E0%A6%B9%E0%A6%AE%E0%A6%BE%E0%A6%A8)
* ml- Malayalam
* gu- Gujarati
* hi - Hindi
* mr - Marathi
* as - Assamese
* kh - Khmer
* kn- Kannada
* my - Myanmar
* ne - Nepali
* pa - Panjabi
* si - Sinhala
* ta - Tamil
* te - Telugu
* th - Thai
* lo - Lao
* ur - Urdu
* vi - Vietnamese
* bo - Tibetan
* zh - Chinese - High script density and require larger fontsize. The Chinese wikipedia sets larger font size using [custom styling](https://zh.wikipedia.org/w/load.php?debug=1&lang=ml&modules=ext.gadget.large-font&only=styles&skin=vector).
* ja - Japanese- High script density and require larger fontsize. The Japanse wikipedia sets larger font size using [custom styling](https://ja.wikipedia.org/w/load.php?debug=1&lang=en&modules=site.styles&only=styles&skin=vector).

A script can be tall and dense at the same time. That means, they need larger font size and larger  line spacing.

Google material guidelines does a similar [grouping](https://material.io/design/typography/language-support.html#language-categories-reference) of scripts.

## **Font selection**

**To be added.**

## **Hyphenation**

If text is justified, it is important to hyphenate to avoid big whitespaces between words.

Latest version of Chromium based browsers has built in hyphenation for many languages. The HTML elements should annotate the language using `lang` attribute. Then use the following css:

```css
text-align: justify;
hyphens: auto;
```

#### Recommendations

* It is better to **not justify** if hyphenation support is not available. For other browsers or old versions https://github.com/mnater/Hyphenopoly can be used. This library uses hyphenation patterns I authored for Indic languages
* The hyphenation character defaults to Soft Hyphen\(`0x00AD`\) but that is not always optimal. Several scripts prefere non-visible hyphenation character at the place of word break. This can be controlled by `hyphenate-character` CSS property. But not widely implemented.  `-webkit-hyphenate-character: '';` works for webkit browsers
* Refer [https://www.w3.org/TR/typography/\#hyphenation](https://www.w3.org/TR/typography/#hyphenation) \( which I contributed with content and examples\)

**Android**: Android comes with hyphenation support. For Indic languages it [uses](https://android.googlesource.com/platform/external/hyphenation-patterns/+/4f23db401df34c634b1aa7248a76e43ff4ce4d8a) the hyphenation patterns I authored 

{% page-ref page="../hyphenation/web.md" %}

## Counters

To be added. Ref [https://www.w3.org/TR/typography/\#lists](https://www.w3.org/TR/typography/#lists)

## Opentype features

### Tabular numbers

Fixed-width numbers are useful for tabular data, where comparing columns across rows is desired. In CSS this can be done by adding style `font-feature-settings: "tnum";`. Enabling this for tables is recommended. A good quality typeface will have this implemented and it helps a lot for fast scanning and analysing data.

![From https://rsms.me/inter/\#features/tnum](../../.gitbook/assets/image%20%28100%29.png)

### Fractions

This feature is contextually sensitive and will convert "words" of numbers separated by forward slash into proper fractions. Good quality fonts will have these opentype rules. In CSS this can be done by adding style `font-feature-settings: "frac";`

![Source https://rsms.me/inter/\#features/frac](../../.gitbook/assets/image%20%2897%29.png)



## Smart quotes

{% embed url="https://smartquotesforsmartpeople.com/" %}

## CSS properties that should not be used

* `font-smoothing` - badly speced and unxpected results depending background and foreground color. Pick a good font instead.
* `font-stretch` - Don't override the designer of the font. The results won't be pretty, especially for complex scripts
* `font-size-adjust` - Don't override the designer of the font. The results won't be pretty, especially for complex scripts
* `:dir()` The :dir\(\) CSS pseudo-class matches elements based on the directionality of the text contained in them. Be aware that the behavior of the `:dir()` pseudo-class is not equivalent to the `[dir=…]` attribute selectors. The latter match the HTML dir attribute, and ignore elements that lack it — even if they inherit a direction from their parent. \(Similarly, `[dir=rtl]` and `[dir=ltr]` won't match the auto value.\) In contrast, `:dir()` will match the value calculated by the user agent, even if inherited. **it  doesn’t have great support, is considered** [**experimental**](https://developer.mozilla.org/en-US/docs/Web/CSS/:dir)\*\*\*\*
* `direction` The direction CSS property sets the direction of text, table columns, and horizontal overflow. Use `rtl` for languages written from right to left \(like Hebrew or Arabic\), and `ltr` for those written from left to right \(like English and most other languages\). Note that text direction is usually defined within a document \(e.g., with [HTML's `dir` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/dir)\) rather than through direct use of the `direction` property.
* `letter-spacing` Don't change this to support complex scripts. Just use defaults
*  `font-kerning` By default kerning is enabled by browsers. Don't play with it.

## Text decoration

### Italic

Italic or even the slanted text decorations are not universal. Due to latin influence some non-latin scripts started using it, but they are mostly artificial. Typefaces for non-latin script not always comes with italic variants. The issue is browsers and editors will create a synthetic italic in those cases - that is a forced 20 degree skewing to the glyphs and it is not nice  to that script. Also known as **faux italic**.

### Underline

For emphasis, avoid using underlines. If at all this is required please be aware that glyph heights vary depending on the script and it may look like script is striked off. [ഇതുപോലെ](https://example.com) is a Malayalam example, the script has bottom tails that already looks like underlines. An additional underline would cut through the glyphs. Because of this, browser now detect these boundaries and avoid overwriting glyphs in link underlines. The css property `text-decoration-skip: ink`; can be used to skip glyphs that cross that underline. [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration-skip)

![](../../.gitbook/assets/image%20%2899%29.png)



## Vertical Rhythm

{% embed url="https://betterwebtype.com/articles/2018/10/15/rhythm-in-web-typography/" %}

### Resources & tools for vertical rhythm <a id="resources--tools-for-vertical-rhythm"></a>

Here’s a list of really cool and useful tools and resource when it comes to rhythm in web typography.

* [Syncope](http://nowodzinski.pl/syncope/) Syncope is a WYSIWYG tool for establishing vertical rhythm on websites.
* [Archetype](https://archetypeapp.com/) Create beautiful web typography designs, in the browser.
* [Grid Lover](https://www.gridlover.net/) Establish a typographic system with modular scale & vertical rhythm.
* [Gutenberg](http://matejlatin.github.io/Gutenberg/) A meaningful web typography starter kit.

## Typesetting in web

#### Links

* Can you typeset a book with CSS? ****[**https://www.w3.org/Talks/2013/0604-CSS-Tokyo/**](https://www.w3.org/Talks/2013/0604-CSS-Tokyo/)\*\*\*\*

