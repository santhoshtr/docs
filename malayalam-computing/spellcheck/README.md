# Spellcheck

### What is a spellchecker? <a id="what-is-a-spellchecker"></a>

The spellchecker is an application that tells whether the given word  is spelled correctly as per the language or not. If the word is not  spelled correctly, the spellchecker often gives possible alternatives as  suggestion to correct the misspelled word. The word can be spellchecked  independently or in the context of a sentence. For example, in the  sentence “അസ്തമയസൂര്യൻ കടലയിൽ മുങ്ങിത്താഴ്ന്നു”, the word “കടലയിൽ” is  spelled correctly if considered independently. But in the context of the  sentence, it is supposed to be “കടലിൽ”.

The correctness of the word is tested by checking if that word is in  the language model. The language model can be simply a list of all known  words in the language. Or it can be a system which knows how a word in a  language will look like and tell whether the given word is such a word.  In the case of Malayalam, we saw that the finite dictionary is not  possible. So we will need a system which is ‘aware’ of all words in the  language. We will see how a morphology analyser can be such a system.

If the word is misspelled, the system need to give correction. To  generate the correctly spelled words from a misspelled word form, an  error model is needed. The most common error model is [Levenshtein edit distance](https://en.wikipedia.org/wiki/Levenshtein_distance).  In the edit distance algorithm, the misspelling is assumed to be a  finite number of operations applied to characters of a string: _deletion, insertion, change, or transposition_. The number of operations is known as ‘_edit distance_‘.  Any word from the known list of words in the language, with a minimal  distance is a candidate for suggestion. Peter Norvig explains such a  functional spellchecker in his article :

{% embed url="https://norvig.com/spell-correct.html" %}

There are multiple problems with the edit distance based correction mechanism

* For a query word, to generate all candidates after applying the four operations, we can calculate the number of words we need to generate and test its correctness. For a word of length n, an alphabet size a, an edit distance d=1, there will be n deletions, n-1 transpositions, _a\*n_ alterations, and _a\*\(n+1\)_ insertions, for a total of _2n+2an+a-1_ terms at search time. In the case of Malayalam, a is 117 if we consider all encoded characters in Unicode version 11. If we remove all archaic characters, we still need about 75 characters. So, for edit distance d=1, a=75, for a word with 10 characters, 2\*10+2\*75\*10+75-1 = 1594 and much larger for larger d. So, you will need to do 1594 lookups\(spellchecks\) in the language model to get possible suggestions.
* The concept that the 4 edit operations are the cause for all spelling mistakes is not accurate for Malayalam. There are many common spelling mistakes in Malayalam that are 3 or 4 edit distance from the original word. Usually the edit distance based corrections won’t go beyond d=2 since the number of candidates increases.

### The Standard Malayalam or lack thereof <a id="the-standard-malayalam-or-lack-thereof"></a>

How do you determine which is the “correct” or “standard” way of  writing a word? Malayalam has lot of orthographic variants for words  which were introduced to language as genuine mistakes that later became  common words\(രാപ്പകൽ/രാപകൽ, ചിലവ്/ചെലവ്\), phonetic  simplification\(അദ്ധ്യാപകൻ/അധ്യാപകൻ, സ്വർണ്ണം/സ്വർണം\), or old  spelling\(കർത്താവ്/കൎത്താവു്\) and so on. A debate about the correctness  of these words will hardly reach conclusion. For our case, this is more  of an issue of selecting words in the lexicon. Which one to include,  which one to exclude? It is easy to consider these debates as blocker  for the progress of the project and give up: “well, these things are not  decided by academics so far, so we cannot do anything about it till  they make up their mind”.

I did not want to end up in that deadlock. I decided to be liberal  about the lexicon. If people are using some words commonly, they are  valid words the project need to recognize as much as possible. That is  the very liberal definition I have. I leave the standardization  discussion to linguists who care about it.

![The news report from Mathrubhumi daily in 2007 about my old spelling checker](../../.gitbook/assets/image%20%2815%29.png)

Back in 2007, when I developed the old Malayalam spellchecker, these  debates came up.  Dr. P Somanathan, who helps me a lot now a days with  this project, wrote about the issue of Malayalam spelling  inconsistencies: “[ചരിത്രത്തെ വീണ്ടെടുക്കുക:](http://www.chintha.com/node/3003)” and “[വേണം നമുക്ക് ഏകീകൃതമായ ഒരെഴുത്തുരീതി](http://chintha.com/node/2967)“.

### Context sensitive spellchecking <a id="context-sensitive-spellchecking"></a>

Usually the spellchecking and suggestion are done at one word at a time. But if we know the context of the word, the spellchecking will be further useful. The context is usually the words before and after the word. An example from English is “I am in Engineer”. Here the word “in” is a correct word, but with in the context, it is wrong. To mark the word “in” wrong, and provide ‘an’ as suggestion, one approach is ngram model of part of speech for the language. In simple words, what kind of word can appear in between a known kind of words. If we build this model for a language, that will surely tell that the a locative POS “in” before Engineer is rare or not seen before.

{% hint style="info" %}
_Improving Finite-State Spell-Checker Suggestions with Part of Speech N-Grams_ Tommi A Pirinen and Miikka Silfverberg and Krister Lindén \[[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.302.9371&rep=rep1&type=pdf)\] – This paper discuss the context sensitive spellchecker approach.
{% endhint %}

