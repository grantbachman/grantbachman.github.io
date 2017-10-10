---
layout: post
title: "Managing Multiple Versions of Python in OSX"
author: "Grant David Bachman"
---

If you find yourself working on multiple projects using multiple versions
of Python as I do, then it's important to be able to switch between
these projects relatively effortlessly. What follows is the simple process
I use to set up my dev machine to work with multiple version of Python
in a way that keeps me sane.

1. Install virtualenv and virtualenvwrapper.
```bash
# installing virtualenvwrapper automatically installs the virtualenv dependency
pip install virtualenvwrapper
```

2. Install PyEnv. If you don't have Homebrew, [install it](https://brew.sh/).
```bash
brew install pyenv
```

3. Install your project-specific version of python
```bash
# Replace '3.6.0' with whichever version you need (3.6.0a3, 3.5.2, etc.)
pyenv install 3.6.0
```

4. Add the PyEnv shim to your .bash_profile and
re-start your shell to enable changes. Adding this to your .bash_profile
isn't strictly necessary, but without it, you lose the ability to run commands
like `pyenv shell`.
```bash
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
exec $SHELL
```

5. Change your shell's version of python. Doing so will change all references
of python within your shell to your newly installed version.
```bash
pyenv shell 3.6.0
```

6. Make a virtual environment for your project. Because of Step 5,
virtualenvwrapper
will automatically create an environment based around your new python version.
```bash
mkvirtualenv my-project
```
