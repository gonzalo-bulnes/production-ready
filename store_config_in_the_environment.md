Store the configuration in the environment
==========================================

General idea
------------

Configuration values should not be committed in the code. If you code is public, then configuration should not be embedded with it because it becomes public too (and some configuration values should be kept secret, see below).

Beyond that, the values of the configuration are not really relevant to the code itself. Once you know that an application relies on a given `API_KEY` to access a third party service, knowing that the API_KEY is `sd4wu8sfd` or `sd345fluae5w345` does not help understanding the code better. Suffice to read the constant name `API_KEY` in a portion of code to understand that some kind of authentication is happening.

What qualifies as configuration?
--------------------------------

- any secret: API keys, passwords
- any user information: usernames, account IDs
- any constant in the program that is likely to change independently from it: third party API URLs for example
- any constant that you may want to change between different deployments of the code: a custom brand name for example if you provide the same application to multiple customers

What does "environment" mean in this context?
---------------------------------------------

The environment is the context in which the application is executed. It is not part of the application, but the application can access information about it (typically using [`os.getenv`](https://docs.python.org/3.5/library/os.html#os.getenv) in Python).

For example, given:

```python
# app.py

import os

key = os.getenv('API_KEY')
message = "Your API_KEY is %s" % key
print(message)
```

```bash
# the first part sets an environment variable, the second runs app.py
API_KEY=sd345fluae5w345 python app.py

# would output:
# Your API_KEY is sd345fluae5w345
```

Changing the `API_KEY` does not require to modify the program, and more importantly, if I want to share this program with you, I can give you `app.py` without disclosing my personal API key to you.

Why in the environment?
-----------------------

> Another approach to config is the use of config files which are not checked into revision control [...]. This is a huge improvement over using constants which are checked into the code repo, but still has weaknesses: it’s easy to mistakenly check in a config file to the repo; there is a tendency for config files to be scattered about in different places and different formats, making it hard to see and manage all the config in one place. Further, these formats tend to be language- or framework-specific.
 _(source: [The Twelve-Factor App](https://12factor.net/config))_

 A note on testing
 -----------------

The environment is not part of the application. That's why it serves our purposes, but that also means that writing tests for the parts of the code that rely on it is slightly more complex than writing usual unit tests.

In the example below, a special tool [`EnvironmentVarGuard`](https://docs.python.org/3/library/test.html#test.support.EnvironmentVarGuard) (part of Python's standard library) is used to simulate changes in the environment from within the test cases.

Demo
----

In this [proof of concept][app], I decided to make the `COLOR` configurable ([test][test], [code][code], [docs][docs]).

  [app]: https://github.com/gonzalo-bulnes/kata-python-web-app
  [test]: https://github.com/gonzalo-bulnes/kata-python-web-app/blob/v1.0.0/test_numbersandcolors.py#L23
  [code]: https://github.com/gonzalo-bulnes/kata-python-web-app/blob/v1.0.0/numbersandcolors.py#L11
  [docs]: https://github.com/gonzalo-bulnes/kata-python-web-app/blame/v1.0.0/README.md#L37-L41

I deployed the application to https://numbersandcolors.herokuapp.com using `turquoise` as my chosen color, but you could deploy your own version using your own preferred provider and choosing whatever `COLOR` value makes you happy — without needing to change any code.

Further reading
---------------

- https://12factor.net/config

<br/>
<p align="right">— Next: <a href="./identify_and_start_isolating_side_effects.md">Identify side-effects and start isolating them</a></p>
