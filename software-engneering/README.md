# Software Engneering

## Principles

* ****[**Forcing Functions**](https://coderefinery.wordpress.com/2020/10/21/forcing-functions-in-software-development/) -there are some things you can do to force issues up to the surface.
  * Dig out an old or cheap phone and try to run your app on it. Any major performance bottlenecks will suddenly become obvious
  * Pretend you’re a new developer in the team1. Delete the project from your development machine, clone the source code and set it up from scratch. Gaps in the Readme file and outdated setup scripts will soon become obvious
  * Try to add support for a completely different database. Details of your current database that have leaked into your data layer abstractions will soon become obvious
  * Port a few screens from your front-end app to a different platform. For example, write a command-line interface that reuses the business and data layers untouched. “Platform-agnostic” parts of the architecture might soon be shown up as anything-but
  * Start releasing beta versions of your mobile app every week. The painful parts of your monthly release process will start to [become less painful](https://martinfowler.com/bliki/FrequencyReducesDifficulty.html)
  * Put your software into the hands of a real user without telling them how to use it. Then carefully watch how they actually use it
* ****[**Software Peter principle** ](https://en.wikipedia.org/wiki/Software\_Peter\_principle)**-** The **Software Peter principle** is used in [software engineering](https://en.wikipedia.org/wiki/Software\_engineering) to describe a dying project which has become too complex to be understood even by its own developers.
* [Zawinski's law of software envelopment](https://en.wikipedia.org/wiki/Jamie\_Zawinski#Principles) - (on [feature creap](https://en.wikipedia.org/wiki/Feature\_creep))    Every program attempts to expand until it can read mail. Those programs which cannot so expand are replaced by ones which can.
* Evidence-based Software Engineering - [http://www.knosof.co.uk/ESEUR/](http://www.knosof.co.uk/ESEUR/)
* DRY, or [Don't Repeat Yourself](https://en.wikipedia.org/wiki/Don't\_repeat\_yourself)&#x20;
  * &#x20;[Don't Repeat Yourself](https://en.wikipedia.org/wiki/Don't\_repeat\_yourself) is a tradeoff - [https://orbifold.xyz/dry-trade-off.html](https://orbifold.xyz/dry-trade-off.html) ([HN](https://news.ycombinator.com/item?id=25459506))
  * Pros and cons of DRY code [https://qvault.io/2021/01/25/the-pros-and-cons-of-dry-code/](https://qvault.io/2021/01/25/the-pros-and-cons-of-dry-code/) - "one place to change a fact".  things that tend to change together should be closer together.
  * [https://coderefinery.nz/2019/01/28/beyond-dry-why-redundancy-makes-your-code-more-robust-and-less-fragile/](https://coderefinery.nz/2019/01/28/beyond-dry-why-redundancy-makes-your-code-more-robust-and-less-fragile/)

## Links

* What distinguishes great software engineers? \[[pdf](https://faculty.washington.edu/ajko/papers/Li2019WhatDistinguishesEngineers.pdf)] \[[HN](https://news.ycombinator.com/item?id=25107285)]
*
