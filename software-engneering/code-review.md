---
description: My approach for code review
---

# Code Review

## General approach

Code review is to help impove the code and there by improving the product. It is not an evaluation or judgement on the person who wrote the code. What is being reviewed is the code, not the person who write the code. Code review is not an exam that every commit need to be passed. Sometimes the reviewer and submitter will agree to address a few suggestion in future iteration than holding the commit in review forever.\
\
Don't do architecture review in PRs. If you're going to make architectural changes, do so in a lightweight design document and get approval there first.

### Ignore minor issues <a href="4-ignore-minor-issues" id="4-ignore-minor-issues"></a>

As long as it is not causing a bug, leave minor issues aside. Interfere only if it will cause a bug. You are not trying to write Linux Kernel. It is OK to have some bad parts of your repo. I am pretty sure even Linux Kernel will have some bad code, even after Linus's strict code review.

### Focus on things that matter <a href="2-focus-on-things-that-matter" id="2-focus-on-things-that-matter"></a>

Instead of going line by line, check the overall logic, check flows in the logic, structure, maintainability and re-usability. Having a perfect code may give you a short term ego boost. But in the long term, the time you spend on that is just a waste. Instead of focusing on that, try to build something new or fix a couple of bugs. The idea of perfect code or perfect algorithm is a delusion.

### Don't insist on coding style <a href="1-don-t-insist-on-coding-style" id="1-don-t-insist-on-coding-style"></a>

Don't get me wrong, your project should have a coding standard and style. Instead of manually making sure it is followed, automate it. Make use of git pre-push / pre-commit hooks. Test it via CI/CD tools to make sure that each PR is tested independently of the developer's environment.\
\
Use a linter and code beautifier of your team's choice. If  your project is JS, use eslint, prettier, etc, if it is python use pep8 or pycodestyle. If you want a custom rule which you can't find in any of these linters, write your own shell script.

It is OK if the variable name is long, or you can come up with a better variable name. As long as the code is readable and code is making sense, it is fine, let it go.

It is quite possible that the code is written by a person who is non-native English speaker. Don't force your understanding of that language on that person. If you think something can be better written, propose alternative and be gentle about it.

### Multiple ways of doing things <a href="3-multiple-ways-of-doing-things" id="3-multiple-ways-of-doing-things"></a>

As programmers, we always see different methods of doing the same things. If a choice is subjective, prefer developers choice and not impose your  preference. It is common to have multiple ways to do same thing. Avoid  asking "why not this way" unless there is a demonstrable advantage. Given the choices have equal advantage, prefer developer's version.

### Clarity on your comments <a href="6-clarity-on-your-comments" id="6-clarity-on-your-comments"></a>

For every comment that you make, make sure there is a clear action to be taken. It should be clear what you expect to happen. Just stating your opinion is not enough. If possible give code snippets. If there are web resources that explain a concept better, please provide that. Then it becomes a team effort than a judging exercise. Every back and forth communication for clarification is time waste. If the code is related to a UI, try maximum to use screenshots and video snippets to illustrate the problem and explain what you expect.

### Be nice <a href="7-last-but-not-the-least-be-nice" id="7-last-but-not-the-least-be-nice"></a>

Be nice to the person who spent time to write the code you are reviewing. The code you are reviewing is written by another human being who has their own opinions, be considerate, don't push your ideology down his or her throat. Agree to disagree. If you think there is a better way to this, think about iterations and improving in multiple steps, rather than outright rejection of a work. 

## References

* [How to do a code review](https://google.github.io/eng-practices/review/reviewer/) - Google Engineering practices
* [How to and How not to, do Code Review](https://blog.j15h.nu/how-to-review-code/) - Jishnu Mohan
* Non violent code review [https://www.mediawiki.org/wiki/Nonviolent_Code_Review](https://www.mediawiki.org/wiki/Nonviolent_Code_Review)
* [Compassionate Coding](https://medium.com/@anikadamg/compassionate-coding-the-secret-of-high-perfomance-teams-34a158fd1390) by Aniket Kadam.
* [Code Health: Respectful Reviews == Useful Reviews](https://testing.googleblog.com/2019/11/code-health-respectful-reviews-useful.html) from Google's Coe Health series
* [Unlearning toxic behaviors in a code review culture](https://medium.com/@sandya.sankarram/unlearning-toxic-behaviors-in-a-code-review-culture-b7c295452a3c) by Sandya Sankarram
* [The Ten Commandments of Egoless Programming](https://blog.codinghorror.com/the-ten-commandments-of-egoless-programming/) on Coding Horror
* [Conventional Comments](https://conventionalcomments.org)
