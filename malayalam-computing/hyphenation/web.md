---
description: How to hyphenate web pages
---

# Web page

Latest version of Chromium based browsers[ has built in hyphenation](https://github.com/chromium/chromium/tree/main/third\_party/hyphenation-patterns/src/ml) for many languages. The HTML elements should annotate the language using `lang` attribute. Then use the following css:

```css
text-align: justify;
hyphens: auto;
-webkit-hyphenate-character: '';

```

![Example webpage hyphenation](<../../.gitbook/assets/image (95).png>)

Firefox 97+ will have hyphenation support for Indian languages([Bug 1240277](https://bugzilla.mozilla.org/show\_bug.cgi?id=1240277))

For other browsers or old versions [https://github.com/mnater/Hyphenopoly](https://github.com/mnater/Hyphenopoly) can be used

{% embed url="http://clagnut.com/blog/2395/" %}

