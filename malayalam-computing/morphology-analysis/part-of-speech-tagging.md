# Part of speech tagging

Identifying the part of speech, or the grammatical category of the word is one of the fundamental requirement for higher level analysis of text. In a sentence “She lives at Palakkad”, identifying ‘she’ as a pronoun, ‘lives’ as verb with a specific tense, Palakkad as a Proper noun, specifically as a place name is crucial to understand the semantics of the text. There are rule based and statistical approaches for identifying these categories. We will not discuss those methods in this article, but once that identification is done, the result is the text with each word annotated with a tag. For example, here is a POS tagged sentence in English:

`There/EX are/VBP 70/CD children/NNS there/RB`

Here, EX, VBP, CD, NNS, RB are POS tags. Specifically, these are tags defined in [PENN treebank POS tags](https://www.ling.upenn.edu/courses/Fall\_2003/ling001/penn\_treebank\_pos.html). It has 45-tags, used to label many corpora in English.&#x20;

![](<../../.gitbook/assets/image (26).png>)

**Penn treebank POS tagset**

There are alternate tagsets such as Brown tagset, which defines 87 tags for English. The members of the tagset is defined based on language characteristics and how detailed analysis is required. For example, In Penn tagset IN is used for both subordinating conjunction like `if, when, unless, after` and prepositions like `in, on, after`. A different tagset may define separate tags for them, so that it would be possible to differentiate them.

### POS tagging for morphologically rich languages <a href="#pos-tagging-for-morphologically-rich-languages" id="pos-tagging-for-morphologically-rich-languages"></a>

Languages with rich morphology require a more complex tagging scheme and methods. Malayalam is one such language, so is many of the dravidian languages, Turkish, Hungarian, Finnish, Czech and many others. A rich morphology language has more information in a word compared to languages like English. If the word is agglutinated and inflected, it has multiple words and inflection information. Since POS tagging is the basis for higher level information processing, extracting as much information as possible from the word is important.

To understand the productive word formation in a morphologically rich language, compared to English, a corpora analysis can be used. A 250,000 word token corpus of Hungarian has more than twice as many word types as a similarly sized corpus of English (Oravecz and Dienes, 2002). A 10 million word corpus of Turkish has 4 times unique words compared to similarly sized English corpus(Hakkani-T ̈ur et al., 2002). A 10 million word corpus of Malayalam has 14 times unique words compared to similarly sized English corpus, as calcualted from [SMC Corpus](https://gitlab.com/smc/corpus).

| Language  | Corpus size | Unique words |
| --------- | ----------- | ------------ |
| English   | 10 million  | 97,734       |
| Turkish   | 10 million  | 4,17,775     |
| Malayalam | 10 million  | 14,27,392    |

In English, lot of information about the syntactic function of a word is represented by word order or neighborimg function words. For example in the phrase `at Palakkad` the word `at` and its word order in the sentence gives the place name `Palakkad` its locative inflection. If we consider the same word in Malayalam, `പാലക്കാട്ടിൽ`, the word `പാലക്കാട്` is inflected(locative) and contains the whole information. Identifying പാലക്കാട്ടിൽ just as Proper noun is not sufficient. The nominal inflection, that is is locative here, should also be identified.

For this reason, the tagging system for agglutinative, inflective languages uses a sophisticated tagging system and has bigger tag set larger than the 50-100 tags we have seen for English. The general practice is to use a sequence of tags rather than a single primitive tag. An example from (Hakkani-T ̈ur et al., 2002):

* Sentence: Yerdeki **izin** temizlenmesi gerek.
* English: The **trace** on the floor should be cleaned
* POS tagging for **izin**: z +Noun+A3sg+Pnon+Gen

A morphology analyser is used for this tagging. The tag set for these languages are huge. In such a morphologically analysed and tagged MULTEXT-East corpora in English, Czech, Estonian, Hungarian, Romanian, and Slovene(Dimitrova et al, 1998; Erjavec 2004, Hajic, 2000) gives the following tagset size

| Language  | tagset size |
| --------- | ----------- |
| English   | 139         |
| Czech     | 970         |
| Estonian  | 476         |
| Hungarian | 401         |
| Romanian  | 486         |
| Slovene   | 1033        |

[The Universal Dependencies](http://universaldependencies.org/) project which defines 16 POS tags and an extensive feature tags to tag any language is worth mentioning here. Mlmorph uses the tagset from Universal Dependencies.

### mlmorph tagset <a href="#mlmorph-tagset" id="mlmorph-tagset"></a>

Mlmorph uses the sequence based tag set. Currently there are 87 tags - you can refer it here: [https://gitlab.com/smc/mlmorph/blob/master/tags.json](https://gitlab.com/smc/mlmorph/blob/master/tags.json) A word `പാലക്കാട്ടിൽ` will be analysed as `പാലക്കാട്<np><locative>`. Similarly `തിരുവനന്തപുരവുമാണ്` will be tagged as `തിരുവനന്തപുരം<np>ഉം<cnj>ആണ്<aff>`. As you can see we are extracting maximum information out of the words for higher level processing. The number of unique pos tag sequences is not finite.

### BIS POS tagset <a href="#bis-pos-tagset" id="bis-pos-tagset"></a>

[The BIS pos tagset](http://tdil-dc.in/tdildcMain/articles/134692Draft%20POS%20Tag%20standard.pdf) attempts to define a common tagset for all Indian languages. I will focus on Malayalam language here, but the tagset is mostly same for other languages too. The tags are defined in 11 categories.

1. **Noun**: 3 tags are defined for Common noun, Proper Noun and Locative inflection - NN, NNP, NST. There is no tag to differentiate a singular noun or plural noun. No tags for gender too. I am not sure why locative is defined while accusative, dative, genitive, instrumental, sociative, and vocative nominal inflections are omitted. The document does not give much example for NST too.
2. **Pronoun**: 5 tags are defined for Personal pronoun(PRP), Reflexive Pronoun(PRF), Relative(PRL), Reciprocal(PRC) and Pronoun question word(PRQ)
3. **Demonstrative**: 3 tags are defined: Deictive(DMD), Relative(DMR), Demonstrative question(DMQ). It should be noted that Malayalam has demonstrative prefixing for “**ചുട്ടെഴുത്തുകൾ**”. For example, `അക്കാര്യം`, `ഇക്കാര്യം`, `അക്കാണുമ്മാമലയൊന്നും` shows that demonstrative prefixing. The document does not discuss them.
4. **Verb**: Verbs are divided to Main, Verbal(VN) and Auxilary(VAUX) categories. Main verb can be Finite(VF), Non Finite(VNF), Infinitive(VINF). Total 6 tags. Obviously the tense information is not captured. Verbs in Malayalam get inflected based on tense, mood, voice and aspect. Verbs are inflected for present, past and future tenses. Perfect, habitual and iterative aspects are very common. Iterative aspect has tense and emphatic variations. Verbs get inflected with causative and passive voices as well. A variety of mood forms such as abilitative, imperative, compulsive, promissive, optative, purposive, permissive, precative, irrealis,monitory, conditional, satisfactive exist. All o fthese forms are supported by Mlmorph. It is a serious omission in BIS POS set. If you are not able to extract at least tense information, I don’t know how useful a POS tagging is.
5. **Adjective**: JJ tag is used here. Here also the agglutinative nature of Malayalam adjectives is not addressed. Consider `നീലത്താമര` -here നീല is adjective to താമര- a perfect case you need sequence of POS tags as we discussed earlier. A related characterestics of Malayalam - coordinatives(ദ്വന്ദസമാസം) is missed here. For example, in the word `അച്ചനമ്മമാർ` - here it is tricky to avoid interpreting അച്ഛൻ as adjective of അമ്മ.
6. **Adverb**: RB tag is used here, which seems directly copied from PENN POS set
7. **Postposition**: PSP tag is defined here.
8. **Conjunction**: Coordinator(CCD), Subordinator(CCS) and Quotative(UT) are defined here. Examples are confusing.
9. **Particles**: Default(RPD), Classifier(C), Interjection(INJ), Negation(NEG) are defined here. Curiously Affirmative is missing when NEG is present.
10. **Quantifiers**: General(QTF), Cardinals(QTC), Ordinals(QTO) are defined. I have written extensively on why Malayalam need a large tagset about numbers in my article about [number spellout](https://thottingal.in/blog/2017/12/10/number-spellout-and-generation-in-malayalam-using-morphology-analyser/). Malayalam numbers are spelled using agglutinated words and it is important to recognize the digits and place value from it.
11. **Residuals**: Foriegn words(RDF), Symbol(SYM), Punctuation(PUNC), Unknown words(UNK) and Echowords(ECH) are defined in this section. There is no explanation or example on what is meant by Echowords. The symbols and punctuations are more or less same from examples given. Since there is no example or explanation for Foreign word, I am not sure if it is English words written in English for example or words originated from other languages such as Sanskrit. Mlmorph has sanskrit tag when the morpheme of the word is from Sanskrit. Knowing this is important since such words have completely different agglutination rules. For example ആശാതീരം vs കടൽത്തീരം-the ആശ->ആശാ adjective form is from sanskrit origins.

#### General comments <a href="#general-comments" id="general-comments"></a>

1. A total of 36 tags defined for Malayalam while a morphologically poor language has at least 45, does not take any language characterstics into consideration.
2. A lot of word information can not be captured because of missing tags. Even Penn POS has tense information.
3. Poor documentation and examples.
4. Does not discuss the morphology of the languages or does not provide any detail on how rich morphology of Malayalam is addressed in this tagging system.
5. Sequential tagging is not discussed at all.
6. One of the worst Malayalam font is used with lot of rendering mistakes, adding to the confusing examples.

In general BIS tag set is incomplete for Malayalam. It is more obvious from the example tagging given in the same document.&#x20;

![](<../../.gitbook/assets/image (27).png>)

**Malayalam tagging examples from BIS POS tag document**

1. Let us list the words that are tagged as N\_NN-(Common noun): പട്ടണങ്ങൾ, പുണ്യനഗരികൾ, പുണ്യസ്ഥലങ്ങൾക്ക്, പുണ്യസ്ഥലങ്ങളുടെ, സ്ഥലങ്ങൾക്കും,ധർമ്മസ്ഥലങ്ങളും, തീർത്ഥാടനസ്ഥലങ്ങളും, മോക്ഷം, ഹിന്ദു, മഹത്വം, ശ്രേഷ്ഠതയും, ആദരവും, ഗ്രന്ഥങ്ങളിൽ. It is obvious that tagging all of these as N\_NN is a very generic tagging. We lost plural, inflections, adjectives, Conjunction and many more information.
2. ആണ് is tagged as auxilary verb V\_AUX, while its use here is Affirmative.
3. മോക്ഷപ്രദായകമാണെന്ന് - this is a good example, you can see agglutination of 4 words - മോക്ഷം, പ്രദായകം, ആണ്, എന്ന് - tagging all of them together as Commoun Noun has no use.

Now I will attempt to prove my observation by actually using a corpus that is tagged using the above tag system and provided by TDIL.

### Malayalam Monolingual Text Corpus ILCI-II <a href="#malayalam-monolingual-text-corpus-ilci-ii" id="malayalam-monolingual-text-corpus-ilci-ii"></a>

Under the Indian Languages Corpora Initiative phase –II (ILCI Phase-II) project, initiated by the MeitY, Govt. of India, Jawaharlal Nehru University, New Delhi had collected [monolingual corpus in Malayalam](https://tdil-dc.in/index.php?option=com\_download\&task=showresourceDetails\&toolid=1886\&lang=en). This is the final outcome of the project and there are approx. 31,000 sentences of general domain. It uses the BIS tag system. This corpus is available in TDIL website to download, but it is not straight forward. To download the complete corpus, you need to register in the site and fill a form, sign and send the physical copy by post to TDIL to get download link. The corpus has very restrictive terms of use. You can only use it for research. The same site also provide a sample version of corpus which has about 30% of original corpus. For my analysis, I used that smaller version.

Let us take a tagged sentence for analysis:

```
YACD54	കരീമിന്റെ\N_NNP `\RD_PUNC പറയാന്‍\N_NNP ബാക്കിവെച്ചത്\N_NNP
`\RD_PUNC ,\RD_PUNC അനില്‍\N_NNP തോമസിന്റെ\N_NNP
`\RD_PUNC മരം\N_NNP പെയ്യുമ്പോള്‍\N_NNP `\RD_PUNC എന്നിവ\N_NN
പ്രദര്‍ശനത്തിന്\N_NN തയ്യാറായി\RB നില്‍ക്കുന്നു\V_VM_VF .\RD_PUNC
```

The above sentence is from _mal\_art and culture\_set1.txt_ in the corpus. YACD54 is sentence Id.

1. Words that are tagged as Proper Noun(N\_NNP): കരീമിന്റെ, പറയാന്‍, ബാക്കിവെച്ചത്, അനില്‍, മരം, പെയ്യുമ്പോള്‍. Here പറയാന്‍, ബാക്കിവെച്ചത്, പെയ്യുമ്പോള്‍ are verb or verb derived words. It should never tagged as nouns
2. Words that are tagged as Common noun(N\_NN): പ്രദര്‍ശനത്തിന്, എന്നിവ,. None of them are nouns.
3. Words that are tagged as Adverb: തയ്യാറായി.
4. Words thare are tagged as Finite verbs: നില്‍ക്കുന്നു

If I understood correctly this is a mannually tagged corpus. And as we see, excluding punctuations, I would say 3 out of 11 words are tagged almost correctly- അനിൽ, തയ്യാറായി, നില്‍ക്കുന്നു.

I will list a few more samples for your analysis.

```
MYGD42	വാല്മീകി\N_NNP രാമായണത്തിലും\N_NNP ഭാസന്റെ\N_NNP കൃതികളിലും\N_NN
എല്ലാം\QT_QTF ഇവിടുത്തെ\N_NST പർവ്വതങ്ങളെ\N_NN പരാമർശിച്ചിരിക്കുന്നതു\V_VM_VNF
കാണാം\V_VM_VNF .\RD_PUNC
```

```
MYLTD52 പായ\N_NN കെട്ടിയ\JJ വലിയ\JJ വഞ്ചികളും\N_NN മീന്‍\N_NN പിടിക്കുന്ന\V_VM_VNF
കൊച്ചുതോണികളും\N_NN പോകാന്‍\V_VM_VNF തുടങ്ങും\V_VM_VNF .\RD_PUNC
```

### Conclusion

Malayalam is a morphologically rich language and require sequence based POS tagging system with wide set of POS tags and Feature tags. A smaller POS tagging system like BIS POS tagging system does not address the language characteristics. The POS tag set itself is incomplete and not prepared with details. Using such a tag system will miss most of the important POS information required for higher level processing. The tagging examples given in the POS tag document and the corpus provided by TDIL are full mistakes and make me wonder whether it went through any review at all. I would not advice to use that corpus for any statistical training purpose or any reference purpose.

Even though I used Malayalam language as example, the BIS tag set has same tags for other languages as well. I would argue that those languages also face more or less same issues I explained in this article.

Thanks for reading!

## References

1. Oravecz, C. and Dienes, P. (2002). Efficient stochastic part-of-speech tagging for Hungarian. InLREC-02, Las Palmas,Canary Islands, Spain, pp. 710–717
2. Hakkani-T ̈ur, D., Oflazer, K., and T ̈ur, G. (2002). Statistical morphological disambiguation for agglutinative languages.Journal of Computers and Humanities,36(4), 381–410.
3. Daniel Jurafsky, James H Martin. Speech and Language Porcessing. Second edition. Chapter 5.
4. [Universal Dependencies (UD)](https://universaldependencies.org/) is a framework for consistent annotation of grammar (parts of speech, morphological features, and syntactic dependencies) across different human languages. UD is an open community effort with over 300 contributors producing more than 150 treebanks in 90 languages.
