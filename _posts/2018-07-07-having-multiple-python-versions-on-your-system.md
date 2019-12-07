---
layout: post
title: Managing multiple python versions on your system
categories: python
---
Ubuntu by default comes with python 2.7. But I mostly use python 3 for my projects and algorithm practise.
I know one solution is creating an alias. All you have to do is `alias python="python3"`.

But what if I wanted to use Python 2.7 again. Change the alias back? I could do that.

But I used virtual environments instead. They are actually used to keep dependencies for different projects separate.

When you create a virtual environment using particular version of python that's the version of python thats invoked when it is active.

So first create a virtual environment using the version of python you want.

For python 2 you need to install virtualenv package using pip. More details [here](https://virtualenv.pypa.io/en/stable/installation/)

For python 3 the way to create a virtual environment is `python3 -m venv tutorial-env`. I think this will be the process for future versions too.

This way you can activate the virtual environment you want and work with that version of python.
