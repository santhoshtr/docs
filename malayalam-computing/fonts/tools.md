# Tools

## fontreport

Google i18n team developed a tool to create detailed report of fonts. The tool named [fontreport](https://github.com/googlei18n/fontreport), produces a multi page PDF with Unicode coverage of the font, what glyphs are in it, what Open Type features it supports, available ligatures, and glyph substitutions. Optionally the tool can also create plain text reports. The PDF is generated using TeX. This tools is used in Gayathri, Manjari fonts.

## fontconfig

[Fontconfig documentation](https://www.freedesktop.org/software/fontconfig/fontconfig-user.html)

```text
$ fc-list MyFont : family : style : lang
MyFont:style=Bold:lang=aa|ay|bi|br|ch|en|es|eu|fj|fur|gd|gl|gv|ho|ia|id|ie|io|it|mg|ml|nl|nr|nso|oc|om|pt|rm|so|sq|ss|st|sw|tl|tn|ts|uz|vo|xh|yap|zu|an|fil|ht|jv|kj|kwm|li|ms|ng|pap-an|pap-aw|rn|r
w|sc|sg|sn|su|za
MyFont:style=Regular:lang=aa|ay|bi|br|ch|da|de|es|et|eu|fi|fj|fo|fur|fy|gl|ho|ia|id|ie|io|is|it|ki|lb|mg|ml|nb|nds|nl|nn|no|nr|nso|ny|om|rm|sma|smj|so|ss|st|sv|sw|tl|tn|ts|uz|vo|vot|xh|yap|zu|an|f
il|ht|jv|kj|kwm|li|ms|na|ng|pap-an|pap-aw|rn|rw|sc|sg|sn|su|za
```

```text
$ fc-match MyFont
MyFont.otf: "MyFont" "Regular"
```

```text
$ fc-validate --lang=en MyFont.otf
MyFont.otf:0 Missing 1 glyph(s) to satisfy the coverage for en language
```

