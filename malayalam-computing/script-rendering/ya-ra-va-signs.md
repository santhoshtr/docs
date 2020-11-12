# Ya Ra Va Signs

In Malayalam, the Ya, Va and Ra signs when appeared together has an interesting problem. The Ra sign is prebase sign, meaning, it goes to left side of the consonant or conjunct to which it applies. The Ya and VA signs are post base, meaning it goes to the right side of consonant or conjunct to which it applies. So, after a consonant or conjunct, if Ra sign and Ya sign is present, Ra sign goes to left and Ya sign remain atto right. This is same, irrespective of the order of ya and ra. 

To understand this issue better, let us take the example of ക + ്‌ര  + ്‌യ and ക + ്‌യ +  ്‌ര. The below image illustrates the steps this combination goes through in rendering. An example word with ക + ്‌ര  + ്‌യ can be transliteration of crew - ക്ര്യൂ. സ്വാതന്ത്ര്യം is another word where this  Ra sign, Va sign combination appears. There is no valid word for ക + ്‌യ +  ്‌ര, but that is not much relevant to a font. It is supposed to render any sequence without errors. If both ക + ്‌ര  + ്‌യ and ക + ്‌യ +  ്‌ര are producing same rendering it is a bug.

![Ya, Ra signs producing same rendering irrespective of order in data.](../../.gitbook/assets/ya-ra-order-wrong.svg)

This bug was present in SMC's Manjari, Chilanka, Gayathri fonts\(all share same opentype tables\).  The issue is also present in Ra sign, Va sign combination as illustrated in the below image.

![Va, Ra signs producing same rendering irrespective of order in data.](../../.gitbook/assets/vara-order-wrong.svg)

I had noticed this issue in 2018 and reported: "[സ്വാതന്ത്ര്യം സ്വാതന്ത്യ്രം rendered same](https://gitlab.com/smc/fonts/manjari/-/issues/20)". I did not give much importance to it since has relatively small impact. But recently Jon Hudson asked me about this behaviour in twitter. That prompted me to solve it.

The fix is not complex. It involves a conditional replacement of Ra sign with Virama + Ra when appeared after Ya sign or Va sign. The replacement can be done using a multiple substitution rule. The Noto Sans Malayalam font from Google also address this issue in exactly same way.

![The splitting of Ra-sign when followed by Ya sign after pstf step](../../.gitbook/assets/ya-ra-order-right.svg)

![The splitting of Ra-sign when followed by Va sign after pstf step](../../.gitbook/assets/right.svg)

This fix is available in latest versions of Manjari, Gayathri and Chilanka. The issue is present in other fonts of SMC too, but not fixed yet.

