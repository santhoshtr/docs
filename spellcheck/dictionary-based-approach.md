# Dictionary based approach

My first attempt to develop a [spellchecker for Malayalam was in 2007](https://wiki.smc.org.in/Spellchecker). I was using [hunspell](https://hunspell.github.io/) and a word list based approach. It was not successful because of rich morphology of Malayalam. Even though I prepared a  manually curated 150K words list, it was nowhere near to cover practically infinite words of Malayalam. For languages with productive morphological processes in compounding and derivation that are capable of generating dictionaries of infinite length, a morphology analysis and generation system is required.  

![](../.gitbook/assets/image%20%288%29.png)

#### The problems with hunspell based spellchecker and Malayalam <a id="the-problems-with-hunspell-based-spellchecker-and-malayalam"></a>

Hunspell has a limited compounding support, but limited to two  levels. Malayalam can have more than 2 level compounding and sometimes  the agglutinated words is also inflected. Hunspell system has [an affix dictionary and suffix mapping system.](https://sourceforge.net/p/hunspell/bugs/94/) But it is very limited to support complex morphology like Malayalam.  With the help of Németh László, Hunspell developer, I had explored this  path. But abandoned due to many limitation of Hunspell and lack of  programmatic control of the morphological rules.

{% hint style="info" %}
_A Data-Driven Approach to Checking and Correcting Spelling Errors in Sinhala_. Asanka Wasala, Ruvan Weerasinghe, Randil Pushpananda, Chamila Liyanage and Eranga Jayalatharachchi \[[pdf](https://www.researchgate.net/profile/Ruvan_Weerasinghe/publication/235931937_A_Data-Driven_Approach_to_Checking_and_Correcting_Spelling_Errors_in_Sinhala/links/5893524daca27231daf61993/A-Data-Driven-Approach-to-Checking-and-Correcting-Spelling-Errors-in-Sinhala.pdf)\] This paper discuss the phonetic similarity based strategies to create a wordlist, instead of edit distance approach.
{% endhint %}

