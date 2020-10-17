# Scribus

[Scribus](https://www.scribus.net/) is a page layout program available for many popular operating systems. It is a free and opensource software. Starting from scribus 1.5.4 version, Malayalam support is available. Their later versions improved the Malayalam unicode support.

Scibus is [used for Janayugam news paper](https://forums.scribus.net/index.php?topic=3566.0) since 2019 December. A few other news paper also started using it recently.

## Hyphenation

Scribus [has support for hyphenating in a dozen or more Indian languages](https://thottingal.in/blog/2019/03/02/scribus-gets-hyphenation-support-for-11-indian-languages/). It can use the hyphenation rules I wrote.

Scribus has a new way to download and use these hyphenation dictionaries. You can now use this feature right away in your installed scribus. The languages with hyphenation support are the following:

* Malayalam
* Tamil
* Telugu
* Kannada
* Marathi
* Hindi
* Bengali
* Gujarati
* Assamese
* Panjabi
* Odia

#### How to Add Hyphenation Dictionary? <a id="how-to-add-hyphenation-dictionary"></a>

Navigate to `Windows -> Resources` in the menu bar. You will see a window as given below. You may want to press “Update Available List”. Then you can see all the languages with hyphenation dictionaries available. Select the download checkbox and press “Download” button. The dictionary will get installed to your system.

Scribus Resource Manager

![Scribus resource manager](../.gitbook/assets/image%20%2811%29.png)

### How to use? <a id="how-to-use"></a>

* Start a new document. Add text frames and content. You may need narrow columns to have wordbreaking contexts.
* Select the text and set appropriate font\(Unicode\) for your language. Make sure the language is selected as your preferred language.
* In Hyphenation properties, set hyphenation character as blank, otherwise visible hyphens will appear.
* Set the text justified.
* From menu Extras-&gt;Hyphenate text. Done.

![](../.gitbook/assets/image%20%2813%29.png)



![Hyphenated two column content](../.gitbook/assets/image%20%287%29.png)

### How does it work? <a id="how-does-it-work"></a>

The resource manager based hyphenation libraries are easier way to add new hyphenation dictionaries. Earlier, these files need to add to Scribus source code. Now these files are defined in scribus server – [http://services.scribus.net/scribus\_hyph\_dicts.xml. ](http://services.scribus.net/scribus_hyph_dicts.xml)It maps the languages to files to download. So if I update the dictionaries in the github repo, a new installation will take that updated file.

### Reporting issues <a id="reporting-issues"></a>

If you find any issues in the hyphenation rules, you can file at [https://github.com/smc/hyphenation/](https://github.com/smc/hyphenation/)

