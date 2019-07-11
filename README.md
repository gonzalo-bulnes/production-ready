An approach to make code "production-ready"
===========================================

There is no "one true way" to write code or make it production-ready. What _production-ready_ means will highly depend on what the code does and the context in which you will use it. However, it is generally useful to try and prioritise among all the things that you could do to increase the level of confidence that you have in your code, and approach that task in a systematic way.

The general rule of thumb is: **don't do more than needed**. The sooner your code is in production, the sooner it actually starts being useful. You are only judge of what is _needed_, and it is a difficult question to answer. Different people around you will have different thoughts about what that means. Try to stay open-minded about it, accept that you might not be fully comfortable with the code you ship to production, but be reasonable, think through the consequences and don't put yourself in a position where you'd be tempted to deny responsibility for what you ship — because you _are_ ultimately responsible for what the code you write does.

I'll do my best to help. Now take a breath, it takes practice, but you can do it! ;)

Two different kinds of steps
----------------------------

While most steps in the list below aim at increasing your understanding of your code and helping you gain confidence that either you or your teammates will be able to evolve it as needed, the first step is a little different. It doesn't directly involve your code, or the effects of your code.

The first step of the list —[Store the configuration in the environment][config]— is security related. Certain infomation is not relevant for other people that work with your code, and some information should be kept confidential.  Leaving credentials behind is frowned-upon, and with good reason! Just don't do it, it's not difficult to fix. It is easy to set up and quite important, and that is why it's the first step in my list.

This first step as it is described will also put you in a good position to deploy your code and will make you friends in your development operations team (and if that team is you, you'll love yourself for that!) It's a good investment.

Let's get started!
------------------

  [config]: ./store_config_in_the_environment.md
  [side-effects]: ./identify_and_start_isolating_side_effects.md
  [data]: ./identify_data_structures.md
  [emotions]: ./the_emotional_stuff.md
  [release]: ./release_early_release_often.md

1. [Store the configuration in the environment][config]
1. [Identify side-effects and start isolating them][side-effects]
1. [Identify data structures and namespaces][data]
1. [The emotional stuff][emotions]
1. [Release early, release often][release]


<br/>
<p align="right">— First: <a href="./store_config_in_the_environment.md">Store the configuration in the environment</a></p>


<br><br><br><br>

----

<br><br>

Contributing
------------

Feedback and contributions are welcome. Please feel welcome to get in touch, [opening an issue](https://github.com/gonzalo-bulnes/production-ready/issues) or otherwise, to share what worked well for you and what could be improved.

The content describes my approach, today, which makes it of course quite personal. Nonetheless, I am particularly interested in knowing if the way ideas are presented and the tone seem appropriate to you, or how they could be improved.

Please note that by participating in this project, you agree to abide by its [code of conduct]. Hopefully, by the time you've read this and consider contributing, you won't be too surprised to hear that 😉

  [code of conduct]: ./CODE_OF_CONDUCT.md

License
-------

### Documentation

    Copyright (C) 2019 Gonzalo Bulnes Guilpain

    Permission is granted to copy, distribute and/or modify this document under the terms
    of the GNU Free Documentation License, Version 1.3 or any later version published by
    the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and
    no Back-Cover Texts. A copy of the license can be found at
    <http://www.gnu.org/copyleft/fdl.html>.

### Code

These notes were originally written next to a small amount of Python code, which is in the public domain and remains available in its [original repository](https://github.com/gonzalo-bulnes/kata-python-web-app).
