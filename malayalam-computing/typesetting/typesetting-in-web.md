# Typesetting in web

* **Can you typeset a book with CSS?** [**https://www.w3.org/Talks/2013/0604-CSS-Tokyo/**](https://www.w3.org/Talks/2013/0604-CSS-Tokyo/)\*\*\*\*

## **Hyphenation**

{% page-ref page="../hyphenation/web.md" %}



## Web typography best practices

16px or 12pt for body text is must  - [https://www.smashingmagazine.com/2011/10/16-pixels-body-copy-anything-less-costly-mistake/](https://www.smashingmagazine.com/2011/10/16-pixels-body-copy-anything-less-costly-mistake/) 

Material Language support - [https://material.io/design/typography/language-support.html](https://material.io/design/typography/language-support.html)

[https://accessibility.digital.gov/visual-design/typography/](https://accessibility.digital.gov/visual-design/typography/) **Use a large enough font size for body text so that people can comfortably read.** Use at least an effective size of 16px, but this can vary depending on the design of the font.

font-size: 100%; // In most browsers, this defaults to 16 pixels

Enable tabular opentype feature for tables



[https://betterwebtype.com/articles/2019/06/16/5-keys-to-accessible-web-typography/](https://betterwebtype.com/articles/2019/06/16/5-keys-to-accessible-web-typography/) Do not set your base font size in pixels. Doing so will overwrite the browser’s default font size. But what exactly is the browser’s default font size? In the code examples above we set our base font size to 100% and I wrote a comment next to it: In most browsers, this defaults to 16 pixels. That’s what I mean when I say browser’s default font size. But here’s the tricky part. Yes, most browsers agreed on the default size of 16 pixels, but the user can change that. Let’s say someone has an impaired vision and sets their browser’s default font size to something larger. Setting the base font size in our CSS to pixels will overwrite their browser default font size setting. Instead of seeing most of the text at a larger font size, we now force them to read it at 16 pixels size. That’s because pixels are an absolute unit, not a relative one. To correct the instructions for setting the base font size by Adam Wood from above, let’s rewrite them like this:

The best practice is to set the font-size on the html using % \(or any other relative unit\), and then set all the other elements to either em or rem which will be relative to the body size.



**Don’t use justified alignment**

I shouldn’t even have to write about this any longer but warning against these can’t hurt. Justifying text on the web results in “rivers of white space between words” which has a hugely negative impact on readability. Avoid justifying text altogether, or at least enable hyphenation or make it work with JavaScript.

[https://www.w3.org/TR/typography/\#hyphenation](https://www.w3.org/TR/typography/#hyphenation)





