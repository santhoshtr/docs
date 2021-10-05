# XeTeX

[XeTeX](http://scripts.sil.org/xetex) is an extension of TeX with built-in support for Unicode and OpenType. In this tutorial, we are going to learn how to typeset Malayalam using XeTeX. With some learning effort, we can produce high quality typesetting using XeTeX. 

[XeTeX](http://scripts.sil.org/xetex) is a Unicode TeX engine which can load system fonts directly using the HarfBuzz library, which is built in. To do this, the `\font` primitive is extended. In order to support these major concepts, a range of TeX primitives are extended. For most LaTeX end users, these subtleties are transparent, with the LaTeX kernel and [`fontspec`](https://ctan.org/pkg/fontspec) package providing interfaces.

Like Knuth’s TeX, it does not directly produce PDF output but rather works _via_ an intermediate format, XDV \(eXtended DVI\). Unlike the classical [DVI](https://www.texfaq.org/FAQ-dvi) format produced by TeX, XDV files cannot be viewed directly, and are normally converted directly to PDF as part of the `xetex` run. \(The conversion itself is carried out by `xdvpdfmx`.\([reference](https://www.texfaq.org/FAQ-xetex-luatex)\)

### Installing XeTeX <a id="installing-xetex"></a>

XeTeX is packaged for all famous GNU/Linux distros. The installation method depends your distro. For ease of installation and configuration, we suggest to use a TeXLive version 2012 or above – either standalone TeXLive distribution or install from your distribution’s package manager. Windows and OSX versions are also available.

Following packages are required to install to get a working xetex environment in your computer. Note that these packages are relatively large in size and will take time and bandwidth.

* texlive-xetex
* texlive-latex-extra
* texlive-lang-other or 
  * texlive-lang-indic \(in older distros\)

You also need reasonably good unicode compatible Malayalam fonts. These fonts also comes with GNU/Linux distros. Search for malayalam fonts in your package manager and install if not already installed. Eg fonts: Meera, Rachana etc.

### Creating documents using XeTeX <a id="creating-documents-using-xetex"></a>

A simple document to learn usage of xetex is given below.

Using a text editor like gedit or kate, create a new file with .tex as file extension. Eg: example.tex. Copy the following content as the content for that file and save.

{% code title="example.tex" %}
```text
\documentclass[11pt]{article}
\usepackage{fontspec}
\usepackage{polyglossia}
\setdefaultlanguage{malayalam}
\setmainfont[Script=Malayalam, HyphenChar="00AD]{Rachana}
\lefthyphenmin=3
\righthyphenmin=4
\linespread{1.2}
\widowpenalty=10000
\clubpenalty=10000
\raggedbottom
\sloppy
\title{\textbf{സ്വർണം}}
\author{മലയാളം വിക്കിപീഡിയ}
\date{}
\begin{document}

\maketitle

\section{സ്വർണം}

മൃദുവും തിളക്കമുള്ളതുമായ മഞ്ഞലോഹമാണ് സ്വർണം. വിലയേറിയ ലോഹമായ സ്വർണം, നാണയമായും, ആഭരണങ്ങളുടെ രൂപത്തിലും നൂറ്റാണ്ടുകളായി മനുഷ്യൻ ഉപയോഗിച്ചു പോരുന്നു. 
ചെറിയ കഷണങ്ങളും തരികളുമായി സ്വതന്ത്രാവസ്ഥയിൽത്തന്നെ പ്രകൃതിയിൽ ഈ ലോഹം കണ്ടുവരുന്നു. ലോഹങ്ങളിൽ വച്ച് ഏറ്റവും നന്നായി രൂപഭേദം വരുത്താവുന്ന ലോഹമാണിത്.
\footnote{http://www.webelements.com/webelements/elements/text/Au/key.html "Key properties of gold" (in ഇംഗ്ലീഷ്). ശേഖരിച്ചത് 2007-06-18.}

\section{ഗുണങ്ങൾ}
സ്വർണത്തിന്റെ അണുസംഖ്യ 79-ഉം പ്രതീകം Au എന്നുമാണ്. ഔറം എന്ന ലത്തീൻ വാക്കിൽ നിന്നാണ് Au എന്ന പ്രതീകം ഉണ്ടായത്.
ഏറ്റവും നന്നായി രൂപഭേദം വരുത്താൻ സാധിക്കുന്ന ലോഹമാണ് സ്വർണ്ണം. ഒരു ഗ്രാം സ്വർണ്ണം അടിച്ചു പരത്തി ഒരു ചതുരശ്രമീറ്റർ വിസ്തീർണ്ണമുള്ള ഒരു തകിടാക്കി മാറ്റാൻ സാധിക്കും. 
അതായത് 0.000013 സെന്റീമീറ്റർ വരെ ഇതിന്റെ കനം കുറക്കാൻ കഴിയും. അതു പോലെ വെറും 29 ഗ്രാം സ്വർണ്ണം ഉപയോഗിച്ച് 100 കിലോ മീറ്റർ നീളമുള്ള കമ്പിയുണ്ടാക്കാനും സാധിക്കും. 

\section{ചരിത്രം}
ചരിത്രാതീത കാലം മുതൽക്കേ അറിയപ്പെട്ടിരുന്ന അമൂല്യലോഹമാണ്‌ സ്വർണ്ണം. ഒരുപക്ഷേ മനുഷ്യൻ ആദ്യമായി ഉപയോഗിച്ച ലോഹവും ഇതുതന്നെയായിരിക്കണം.
ബി.സി.ഇ. 2600 ലെ ഈജിപ്ഷ്യൻ ഹീറോഗ്ലിഫിക്സ് ലിഖിതങ്ങളിൽ ഈജിപ്തിൽ സ്വർണ്ണം സുലഭമായിരുന്നെന്ന് പരാമർശിക്കുന്നുണ്ട്.
ചരിത്രം പരിശോധിച്ചാൽ ഈജിപ്തും നുബിയയുമാണ്‌ ലോകത്തിൽ ഏറ്റവുമധികം സ്വർണ്ണം ഉല്പ്പാദിപ്പിച്ചിരുന്ന മേഖലകൾ. ബൈബിളിലെ പഴയ നിയമത്തിൽ സ്വർണ്ണത്തെപ്പറ്റി പലവട്ടം പരാമർശിക്കുന്നുണ്ട്.

\end{document}
```
{% endcode %}

Now you need to compile this document to generate PDF.

```text
xelatex example.tex
```

Output of the above content should look like this:

![](../../.gitbook/assets/image%20%284%29.png)

The above tutorial is a very basic tutorial on using XeTeX with Malayalam. For detailed tutorial, please refer any tutorial available freely in internet. Example: [https://en.wikibooks.org/wiki/LaTeX](https://en.wikibooks.org/wiki/LaTeX)

## Faux slanted text

To generate faux\(artificial, fake\) slanted text from a font that does not have it, following trick can be used:

```text
% Tikz package for faking slanted text
\usepackage{tikz}
\renewcommand{\textsl}[1]{\tikz[baseline=(X.base)] \node[xslant=0.2231153] (X) {#1};}
```

Then in a chapter content use 

```text
\textsl{ഈജിപ്ഷ്യൻ ഹീറോഗ്ലിഫിക്സ്}  
```

