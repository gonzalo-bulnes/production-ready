Release early, release often
============================

General idea
------------

The best use of our time is to develop products _incrementally_ —don't do more than needed (release early)— and _iteratively_ —re-assess often what would be the best use of your time (release often).

The shorter each iteration is, the quicker new knowledge can be used to evaluate what is the most valuable next step, and the quicker new realities can be taken into account in those decisions for maximum impact.

Incremental delivery requires understanding of how the programs we write will be used, and to which purpose. That in itself is the object of an entire field: product development. But the acquisition of that understanding is greatly facilitated by the feedback gathered after each iteration. That's why, if we'll focus on one thing at a time, the question becomes: how can we iterate quickly?

A continuous conversation on the product will allow to determine what could be the best next increment (trade-off size _vs_ delivered value), but adequate thinking about tooling will greatly increase your or your team's readiness for quick iteration.

Where to start?
---------------

### Release

No doubts here: if you want to release often, you need to release once. Figure out what it takes to deploy your code to production, write it down in your `README` and do it, now, when the program says "hello, world".

It might sound silly to write the steps down at this point, it's probably not very complicated. But if you want to do something often, you'd rather make it as error-proof as possible. Time will come to automate this, but as a first step, following a checklist adds a lot of reliability for little effort. Also, anyone can deploy now!

**Note**: I'm not making a distinction between releasing and deploying for now, honestly, I think it doesn't matter at this point. Not until multiple deployments are active at the same time. But you might see the distinction being made in the literature.

### Automate the test suite

Since [identifying side-effects and isolating them][side-effects], you have a little collection of automated tests (for the code without side-effects). That is great, and efficient, but useless if you forget to run it. Don't be too hard on yourself, and instead make your life easy. — _People don't fail, processes do_.

  [side-effects]: ./identify_and_start_isolating_side_effects.md]

If your code is public in Github, setting up a continuous integration server is fairly quick as soon as you can run your test suite locally (on your own machine). I personally use [Travis CI](https://travis-ci.org/gonzalo-bulnes/kata-python-web-app), which can be setup adding a [single file](https://github.com/gonzalo-bulnes/kata-python-web-app/commit/fc131e9ac074e27fb1d4c1b04533f3747887db34) to your project ([tutorial](https://docs.travis-ci.com/user/tutorial/)). The commands will be the same you run locally. The Travis CI team supports the open-source community by providing the service for free on public repositories, and I appreciate their commitment to diversity in the industry. (In return, don't heat the planet and spend their money running your test suite for _all existing_ versions of Python if that's not useful! Think about costs and benefits globally.)

Once set up, the test suite will be run automatically every time you push to Github and the results will feed back into your repository. If you keep the discipline of only merging branches which test suite succeeds ("is green"), you'll be in position to release the content of the `master` branch anytime.

**Note**: The continuous integration server can be used for more than running the test suite (building deployable artifacts when using compiled languages for example), that's why the word "build" is used everywhere. Running the test suite is understood as one step in a build process — which might also be entirely composed of that single step, in Python for example because we deploy the code as-is.

What's next?
------------

### Tag your releases

Use Git (or whatever version control system you use) to tag your releases. As soon as your program does something useful in production, don't  tergiversate, go with `v1.0.0`!

```bash
git tag -a "v1.0.0" -m "Initial release"

# then go with semantic versioning (https://semver.org)
git tag -a "v1.1.0" -m "Add optional Twitter support"
```

Tagging your releases will greatly improve your users experience, whether they use a library your maintain or a service. We all want to know what's new when things change! And it's good for you to feel progress to keep the motivation going.

----

Once you're here, you're in a pretty good position already. What comes next will depend on your context and users.

Does your build process contain multiple steps? Is running your test suite matter of more than a single command? You _could_ use a [`Makefile`](https://github.com/gonzalo-bulnes/dice/blob/master/Makefile) to semi-automate those steps and make maintenance or development operations less error-prone and more contributor-friendly... if you like make files!

At that point, you can probably identify the painful points in your process and address them as you go. Your best guide is probably keeping in mind that any repetitive process is inherently error-prone, and that there is no point in doing boring stuff more than thrice when it can be automated.

What about incremental thinking?
--------------------------------

Training to think incrementally is likely to be your next best investment. It is also a never-ending practice. How to make decisions will always depend on the context, and it is something for which you never stop training for.

If you work with product managers, getting to understand how they think and how to communicate with them effectively is the best way to learn. They tend to use a whole different vocabulary —same words, different meanings which is sometimes tricky if you're not fully aware of it— and come with an often different perspective, which can also be confusing. But they want the same as you: maximum impact. (Outcome, not features. Changing the world, not only adding lines of code to it — with the advantage that they're usually unimpressed by code and have less distractions to keep their focus on the outcome.) Learning to communicate with them effectively will dramatically increase your and your team's potential for impact through collaboration.

<br />

> Different people around you will have different thoughts about what [is needed]. Try to stay open-minded about it, accept that you might not be fully comfortable with the code you ship to production, but be reasonable, think through the consequences, [identify trade-offs, and you'll be fulfilling your role at best in a collaborative team].
>
> — (looping back from the series [Intro](./README.md).)


<br /><br />
<h2 align="center">Opening thoughts</h2>
<br /><br />

The conversation doesn't end here. Your code is production-ready, and contribution-ready; that's when collaboration really starts. Release, deploy, talk to the people around you —or on the other side of the world— learn and iterate on your project together! And maybe [get comfortable pair programming](https://olivierlacan.com/posts/the-fear-of-pairing) next, or learn more about [refactoring techniques](https://refactoring.guru/refactoring/techniques/composing-methods) or automatically testing code with side-effects. Exposing yourself to different ways of thinking is a great way to grow! 🍐🎉
