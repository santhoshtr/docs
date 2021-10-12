# What is a good input method?

As more and more people enter to the Malayalam digital world, the issue of not having any formal training for Malayalam computing is more observed. People sometimes just search for input methods in web, ask friends or use whatever coming with the devices they have. Since I myself is an author of two input methods, sometimes people ask me too. This essay is about the characteristics of a good input method to help people make the right choice. This essay does not recommend any particular input method though. I will focus on Malayalam language, but some concepts may be applicable for similar languages.

### What is an input method?

An [input method](https://en.wikipedia.org/wiki/Input_method) or Input Method Editor(IME) is a program that helps to enter characters that are not natively present in the keyboard of computer(computing devices). An IME is necessary when the script has more characters than the number of keys available in the keyboard. Malayalam need an IME to generate Malayalam content because it is not present as native keys in a keyboard or it has more characters than any keyboard.

### Why the selection of input method is important?

Learning an input method and practicing typing Malayalam with that is as important as you learn to write using a pen when you were a kid. You learned that skill once, by taking time, once for your life time. Writing using pen used to be the only way to communicate in written form. Now a days it is typing. You should master this skill to express freely. You should own the pen, you should own the input method. It should not spy you. I will explain these concepts in detail in this essay.

Now a days, people learn Malayalam typing based on social needs. "I want to chat with my friends in Malayalam", "I want to participate in Whatsapp discussions in Malayalam", "I am a Malayalam teacher, it is bad if I don't know typing in Malayalam", "I am a software engineer, it is bad if I don't know typing in my mother tongue" and so on. There will be a tendency to learn this skill quickly and start using it. The immediate need to write your name or write some informal chat message can be met by any kind of input method, but soon you will realize that you need to write serious things also. You will realize I need to prepare a formal document, I need to typeset a report or a notice and so on. You should not require relearning a new input method at that point. So don't take the learning Malayalam typing lightly.

### Choices

If you just do a web search for Malayalam keyboard in Google or its playstore, you get dozens of options. That is good and bad. For an uninformed user, it is difficult to chose the right one and that is why I write this essay.

There are three main types of input methods available now a days:

#### Keyboard based input methods

Keyboards remains the most accurate and robust ways to input. Once practiced, they are the fastest too. There are one to one mapping keyboard based input methods like Inscript, where each physical key in keyboard is mapped to a single unicode codepoint.

**Inscript**

There is a misconception that one should use a government prescribed official keyboard for typing in Malayalam. First of all, there is no such official prescription.

{% content-ref url="inscript.md" %}
[inscript.md](inscript.md)
{% endcontent-ref %}

**Phonetic keyboards**

While the inscript layout claims to be logically designed, some people find it difficult to learn, and prefer phonetic keyboards. In phonetic keybaords, the English keys in physical keyboard are mapped to phonetically similar letters in a language. So p will be mapped to പ(pa), instead of ജ(ja).

Both phonetic or inscript, or in general one to one keymap based keyboards are the most flexible keyboards. The user need to decide the character sequences.

**Transliteration based keyboards**

These are the most popular keyboards for Indian languages. There is a wide spread habit of writing Indian scripts using latin alphabet(transliteration). The same latin alphabet sequences are used to input a language. They are not one to one mapping, they are sequence based. Typing `ki` produces കി. For Malayalam, [Swanalekha](https://swanalekha.smc.org.in), Mozhi are some of the popular transliteration based input methods.

![Swanalekha transliteration key mapping](https://swanalekha.smc.org.in/img/swanalekha.png)

In general, these keyboards also provide flexibility to type anything as long as the user use the correct key sequences.

The popularity of transliteration is not limited to Indian languages. For example, a widely used input method in Chinese, [Pinyin](https://en.wikipedia.org/wiki/Pinyin) is a transliteration based input method.

![Typing in Chinese using pinyin](<../../.gitbook/assets/image (7).png>)

#### Probabilistic keyboards

These type of keyboards are "intelligent" keyboards and expect no learning from users at all. They are mainly transliteration based, but does not expect user to learn any transliteration schemes. Based on different algorithms, the keyboards will predict what you meant to type and provide auto completion.

I called it probabilistic because they give you suggestions about what to type as a probability of what you typed in English. Since there is no fixed keymaps, every output is guess and often there are multiple guesses.

[Varnam Input method](https://www.varnamproject.com), Google input tool are some examples.

![ Varnam Input method](<../../.gitbook/assets/image (9).png>)

![ Google Input tool](<../../.gitbook/assets/image (8).png>)

Since predicting what the user meant require longer sequences, these input methods are word translitrations. That means, user types approximate transliteration of a word, and then the input method offers suggestions. The aspect of "no learning" comes with the cost that, the input method "dictates" what you can type. If you want to literally input something that the system does not know, you are at loss. Similarly, the usual editing practices like deleting few characters using backspace and continuing there is painful because, what you continue is considered as a new word.

As it is very easy to start with, many users try these "intelligent" keyboards. But they are not general purpose input methods and often hinders your speed and flexibility.

#### Speech recognition based input methods

Speech recognition based input methods like Google voice input is very popular in chat applications. They are getting better at recognizing speech and demand very low effort from the user. Recognition is often at group of words level. In a mobile context, this hands free input method is very efficient for quick communication.

But it is important to differentiate this from a keyboard based input method. Speech recognition based input method is not a replacement for keyboard based input method. There is no concept of "editing" the text using speech recognition. It is not easy to move back and forth through the content and make changes. It is designed for a small amount of content in a simple context like chat application. Speech recognition also has limitations of requiring relatively noise-free surroundings.

#### Handwriting recognition based input methods

This is another input method with relatively nil learning. Users write using a finger or stylus in a virtual pad in the screen. Google handwriting tool is an example. The efficiency and accuracy is getting better everyday. Similar to speech recognition based input method, this is also designed for quick communications in non-sophisticated contexts with very little editing involved. Again, this is also not a replacement for keyboard based input method. Ambiguity in handwriting is often introduced as spelling mistakes. For example, symbols like \[0, o, ഠ, ം], \[l, 1, |, \\, /, I, i], \[:, ഃ] are all often misinterpreted. In formal communication or writing context, it is not uncommon for a user to have to switch to keyboard based input method for corrections.

### Integration

A recent small study by my colleagues at Wikimedia found that many non-latin users think that they cannot input non-lating content directly to any application. Instead they use random websites that provide online typing tool and copy paste that content to other applications. This is a big gap in awareness. Now a days you can input content to any application directly just like how you would type English. A good input method is well integrated to operating system and won't require copy paste.

Many applications respond to keypresses in various ways(autocomplete, contextual help). You will lose all those features, if content is not entered directly, but used copy paste. Almost all applications provide undo-redo support for editing. If the input method is not well integrated to operating system, you will lose that features as well.

For example, a "smart" keyboard that shows latin and when you press space, converting what you typed to your preferred language is intercepting with the undo redo operations(in general edit transactions. The application see you first typing English and then suddenly changes to Malayalam for example.

A good input method won't reveal your input keys to application, It will internally process it and present the output to application. For example, if you are using a transliteration based input method "Swanalekha", even if you are typing in english key sequences, the screen does not show those characters, the application to which you are typing does not see those English characters. It only gets Malayalam. The keys are processed in a special layer called "composition or pre-edit".

### Features of good input methods

#### Control

You should master this skill to express freely. Just like the pen does not interfere with what you write, the input methods should just do what you wanted to write. It should not control what you can type, where you can type. Probabilistic or "intelligent" keyboards control what you type and what you can type. They also decide the spelling or style of words too based on popularity(or sometimes popular mistakes).

#### Privacy

Can an input method keep what you type private? No one knows that unless the source code of the input method is available to inspect. Free and open source software is a prerequisite for data privacy. Think twice before choosing proprietary input methods from suspicious sources, requiring internet access for use.

#### Availability and ownership

An input method should be available always in your device. It should not stop working if device is offline. The input method should be available in all devices and operating systems you use. You don't want to learn a new input method for your phone, another for your office computer. A good input method will be available in maximum platforms.

An input method is primary way to use your language. [Just like you own your pen, you should own the input method](https://thottingal.in/blog/2017/08/16/your-language-your-pen/). Input methods that require licensing fee and become unavailable based on the conditions of its vendor is not owned by you. You should make sure that input methods are expected to continue even after the original author is not maintaining it. A couple of years back, [Google withdrew its input methods for desktops](https://support.google.com/chrome/thread/32057437?hl=en). There were lot of users for that input method and they were all stuck with the last release. I even see some of those users, save the installation programs in their computers and share with their friends while Google just abandoned them.

Make sure that your input method is not an experiment of some developer who just want to play with a technology. Make sure it is well maintained and expected to be available for long time.

#### Correctness

The ultimate goal of an input method is to generate data in unicode. You may be using voice, handwriting, transliteration, autocompletion or such methods. But the end result should be correct according to the language. If an input method produce 0(zero) for ം(anuswaram) or o(English o) for Malayalam TTA(ഠ), you may not notice it immediately because they are visually same. But they are completely different. The content generated become unsuitable for any language processing. Malayalam unicode has interesting characteristics and complexities. The language written in digital form, sometimes may use invisible characters like Zero Width Joiner and Zero width non-joiners. If [an input method adds these invisible characters in unwanted places](https://thottingal.in/blog/2007/10/11/%E0%B4%B5%E0%B4%B0%E0%B4%AE%E0%B5%8A%E0%B4%B4%E0%B4%BF%E0%B4%AF%E0%B4%BF%E0%B4%B2%E0%B5%81%E0%B4%82-%E0%B4%AE%E0%B5%8A%E0%B4%B4%E0%B4%BF-%E0%B4%95%E0%B5%80%E0%B4%AE%E0%B4%BE%E0%B4%A8%E0%B4%BF%E0%B4%B2/), then also it is buggy.

Since input method is a software, like any software, bugs are often present. But the difference is whether you can report bugs and get it fixed. For that the software should be well maintained.

#### Well maintained software

A well maintained input method will have a bug tracker where people can report issues. The maintainers will respond to the issues and release new versions with bug fixes. There will be a forum or similar places where people can go and ask questions. The input method will require updates as the operating systems get new versions. There should be a community or maintainer who release new versions regularly. You should not use an input method that is not maintained by anybody.

#### Documentation

A well maintained input method will also have accompanied up to date documentation. This is helpful for you to refer, learn the input method, solve technical issues.

#### Easy to learn

Yes, the input method should be easy to learn and practice. How much easy? Please expect a minimum effort here. You did not learn to write using pen in 10 minutes. So a lifelong skill require time to learn and master. If you are not willing to spend time to learn an input method, the choices are input methods that predict what you meant in probabilistic way and they often control what you can write.
