The emotional stuff
===================

a.k.a the really effective stuff.

General idea
------------

We are social animals, and we react, whether we want it or not, when other people care. We've also limited time and plenty of distractions. The more straightforward it is for us to understand how to use a tool, the more likely we are to give it a go. After that, [cognitive dissonance](https://en.wikipedia.org/wiki/Cognitive_dissonance#Free_choice) kicks-in and we'd rather improve the tool than looking for a new one — sometimes for the better! (Don't get me wrong!)

There are plenty of little things that make our experience outstanding when discovering some projects, sometimes they are actually convenient, but often they are only big enough to demonstrate that someone took a moment to think about them, for us. Those are way more significant for us that we often think. This is a list of little hacks, and small ideas to make life nicer, and easier to your users and contributors.

> If you care, make it obvious. 🌸 — proverb

README stuff
------------

The `README` file is a great place to start. Ideally, you want all your projects to have a read-me. You may even want to write the read-me [_before_ you write any code at all](http://tom.preston-werner.com/2010/08/23/readme-driven-development.html)!

Keep in mind that most people will _only_ see your read-me when browsing Github (or Bitbucket, or wherever you publish your projects).

Here come some easy, quick things... that belong to different categories. I'll try to explain why I like each one.

### Learn Markdown!

Seriously, I promise it won't take you hours. Markdown is quick to learn, quick to write, renders as nice HTML, is readable in plain text. You'll use it in issues, pull requests, read-mes, documentation... just do it, and hate me for pushing you if you regret.

Learn to write hierarchical headers, inline code, to make code blocks and [enable syntactic coloration](https://help.github.com/en/articles/creating-and-highlighting-code-blocks) on them (that takes exactly 6 letters: `python`). Learn to make lists, write links and images (both useful for read-me [**badges**](#badges)!). Emphasise or embolden text and quote it. (Quotes are particularly powerful, because they are literally the person who writes talking to _you_.)

You know when you receive that email or SMS full of typos that tells you won a prize? Using a little more than the most basic Markdown will 🚀 rocket you out of that category.

- https://daringfireball.net/projects/markdown/
- https://help.github.com/en/articles/basic-writing-and-formatting-syntax

💡 Open the read-mes you like as "raw" text in Github and see how they're written!

### A title and a one-line description

Bare minimum. If you can't describe what you want your project to achieve, it's unlikely anyone will be able to guess. You might think that the title is enough, I'd say that the difference between the people who took the time to write the one-liner and those who don't is quickly made. (Hint: the latter _feel_ more like people.)

💡 Fill that same one-liner as description at the top of your Github repository.

### Installation, Usage, Development sections

Time to put yourself in... your own shoes when you started learning that language. How do you even get started with this project? How do you install it, how do you use it?

If you expect contributions, tell people how to run the test suite — it is likely the first thing most contributors will try to do. You next contributor will be smart, but she won't spend 20min trying to figure out how to run your code, she'll go elsewhere.

### Contributing section

If you'd like contributions, mention it. This is the perfect place to talk about your project's [code of conduct](#code_of_conduct) or [issue and pull request templates](https://github.blog/2016-02-17-issue-and-pull-request-templates/).

### Credits and License sections

If I'll contribute to your project I want to know you acknowledge contributions and you respect authorship terms. The legal stuff is complex, but the basics are simple: nothing is free to use unless explicitly said so.

The license you choose makes little difference in the end, but even if you release your code in the public domain, say so! Be intentional, for that is a mark of accountability.

Don't forget to place the [`LICENSE`](#license) text in your repo.

### Badges!

No matter the language you use, badges give it the Pro™ touch. They're silly, but they're also useful.

Knowing that your code is continuously tested makes a difference, so does finding out that your library is available in PyPi, NPM or Rubygems, so does knowing that its code is idiomatic, documented and that it's documentation was mindfully put together.

[![Build Status](https://travis-ci.org/gonzalo-bulnes/kata-python-web-app.svg?branch=master)](https://travis-ci.org/gonzalo-bulnes/kata-python-web-app)
[![Gem Version](https://badge.fury.io/rb/dredd-rack.svg)](http://badge.fury.io/rb/dredd-rack)
[![Go Report Card](https://goreportcard.com/badge/github.com/gonzalo-bulnes/pair)](https://goreportcard.com/report/github.com/gonzalo-bulnes/pair)
[![GoDoc](https://godoc.org/github.com/gonzalo-bulnes/pair?status.svg)](https://godoc.org/github.com/gonzalo-bulnes/pair)
[![Inline docs](http://inch-ci.org/github/gonzalo-bulnes/dredd-rack.svg?branch=master)](http://inch-ci.org/github/gonzalo-bulnes/dredd-rack)

The best of it is that most of those badges require very little or no setup when your code is public.

And you can even [create your own badges](https://shields.io/)! How about these?

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-e7359e.svg?style=popout)](http://makeapullrequest.com)
![Code Review Welcome](https://img.shields.io/badge/code%20review-welcome-e7359e.svg?style=popout)
[![Learn Rust](https://img.shields.io/badge/Learn-rust-d98c5e.svg?style=popout)](https://doc.rust-lang.org/book/index.html)
[![Docker image](https://img.shields.io/badge/docker-gonzalobulnes%2Fcartoonist-blue.svg)](https://hub.docker.com/r/gonzalobulnes/cartoonist)

Having badges in your read-me is one more thing that's quick to do and shows you care. Be it about code quality, community, inclusiveness or not taking things too seriously.

### Emojis?

Emojis are cool... I think they are anyway! I copy-paste them from [Emojipedia](https://emojipedia.org/bear-face/). 🐻

The other files
---------------

### CHANGELOG

Please [keep a change log](https://keepachangelog.com/en/1.0.0/). (Good you learnt Markdown isn't it? 😉)

### CODE_OF_CONDUCT

There are sadly so many reasons to include a code of conduct in your projects. On the other side, many of us will be happy when we see it! — Coraline Ada Ehmke's [Contributor Covenant](https://www.contributor-covenant.org/version/1/4/code-of-conduct) is a good place to start.

### CONTRIBUTING

All relevant information about how you like receiving contributions, with the details that don't quite fit in your read-me.

### LICENSE

Don't forget to include a plain text version of the license. As with the other files, it is conventional to call it `LICENSE` with full caps (if you work on Windows and prefer `LICENSE.txt` go for it!) This file makes it easier for robots to find relevant code.

A few thoughts on all this
--------------------------

I started writing my `README`s as the first thing in my projects when I realised how hard it was for me to "finish" anything. I wanted to use that first half an hour of energy and enthusiasm to get that idea public. And I found out that not only I feel the satisfaction of having done something after spending 25 minutes explaining an idea on Github, but it makes it so much easier for me to come back to it when I —inevitably— leave the project untouched for months.

Also, over time, I have had super nice conversations around read-mes with no code. Some motivated me to actually write the [code](https://github.com/gonzalo-bulnes/pair).

These days, with less time to dedicate to programming outside of work, I really like to make sure I'm in position to accept someone's help or pairing offer as soon as I start a new project.

What works for me might not work for you, but it works very well for me and the rewards feel huge. With [love, internet style](https://www.youtube.com/watch?v=Xe1TZaElTAs). ❤️

<br/>
<p align="right">— Next: <a href="./release_early_release_often.md">Release early, release often</a></p>
