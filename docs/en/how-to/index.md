# Contributing to this tutorial { id=contributing }

This tutorial is written using [MkDocs and Markdown](https://www.mkdocs.org/).
This guide will help you contribute fixes or new content to this
tutorial.

Translations of this tutorial are managed using
[Weblate](https://hosted.weblate.org/engage/beeware/). If you'd like to
contribute to the translation effort, join the `#translations` channel
on [Discord](https://beeware.org/bee/chat/) and introduce yourself!

## Set up your development environment

To build the BeeWare tutorial you **must** have a Python 3.12
interpreter installed and available on your path (i.e., `python3` must
start a Python 3.12 interpreter).

/// tab | macOS

```console
$ python3 --version
$ pip3 --version
```

///

/// tab | Linux

```console
$ python3 --version
$ pip3 --version
```

///

/// tab | Windows

```doscon
C:\...>python3 --version
C:\...>pip3 --version
```

///

### Create a virtual environment

The recommended way of setting up your development environment for
BeeWare is to install a virtual environment, install the required
dependencies and start coding. To set up a virtual environment, run:

/// tab | macOS

```console
$ python3 -m venv venv
$ source venv/bin/activate
```

///

/// tab | Linux

```console
$ python3 -m venv venv
$ source venv/bin/activate
```

///

/// tab | Windows

```doscon
C:\...>python3 -m venv venv
C:\...>venv\Scripts\activate
```

///

Your prompt should now have a `(venv)` prefix in front of it.

### Clone the BeeWare Tutorial repository

For updates to BeeWare documentation:

Next, go to [the BeeWare Tutorial page on
GitHub](https://github.com/beeware/beeware-tutorial), fork the repository into
your own account, and then clone a copy of that repository onto your
computer by clicking on "Clone or Download". If you have the GitHub
desktop application installed on your computer, you can select "Open in
Desktop"; otherwise, copy the URL provided, and use it to clone using
the command line:

/// tab | macOS

Fork the BeeWare Tutorial repository, and then:

```console
(venv) $ git clone https://github.com/<your username>/beeware-tutorial.git
```

(substituting your GitHub username)

///

/// tab | Linux

Fork the BeeWare Tutorial repository, and then:

```console
(venv) $ git clone https://github.com/<your username>/beeware-tutorial.git
```

(substituting your GitHub username)

///

/// tab | Windows

Fork the BeeWare Tutorial repository, and then:

```doscon
(venv) C:\...>git clone https://github.com/<your username>/beeware-tutorial.git
```

(substituting your GitHub username)

///

### Install BeeWare tutorial docs dependencies

Now that you have the source code, you can install BeeWare docs
requirements into your development environment. Since we're installing
from source, we can't rely on pip to resolve the dependencies to source
packages, so we have to manually install each package:

/// tab | macOS

```console
(venv) $ cd beeware
(venv) $ python -m pip install -e ".[dev]"
```

///

/// tab | Linux

```console
(venv) $ cd beeware
(venv) $ python -m pip install -e .[dev]
```

///

/// tab | Windows

```doscon
(venv) C:\...>cd beeware
(venv) C:\...>python -m pip install -e .[dev]
```

///

### Install pre-commit

BeeWare uses a tool called [Pre-Commit](https://pre-commit.com) to
identify simple issues and standardize code formatting. It does this by
installing a git hook that automatically runs a series of code linters
prior to finalizing any git commit. To enable pre-commit, run:

/// tab | macOS

```console
(venv) $ pre-commit install
pre-commit installed at .git/hooks/pre-commit
```

///

/// tab | Linux

```console
(venv) $ pre-commit install
pre-commit installed at .git/hooks/pre-commit
```

///

/// tab | Windows

```doscon
(venv) C:\...>pre-commit install
pre-commit installed at .git/hooks/pre-commit
```

///

When you commit any change, pre-commit will run automatically. If there
are any issues found with the commit, this will cause your commit to
fail. Where possible, pre-commit will make the changes needed to correct
the problems it has found:

/// tab | macOS

```console
(venv) $ git add some/interesting_file.py
(venv) $ git commit -m "Minor change"
black....................................................................Failed
- hook id: black
- files were modified by this hook

reformatted some/interesting_file.py

All done! ✨ 🍰 ✨
1 file reformatted.

flake8...................................................................Passed
check toml...........................................(no files to check)Skipped
check yaml...........................................(no files to check)Skipped
check for case conflicts.................................................Passed
check docstring is first.................................................Passed
fix end of files.........................................................Passed
trim trailing whitespace.................................................Passed
isort....................................................................Passed
pyupgrade................................................................Passed
docformatter.............................................................Passed
```

///

/// tab | Linux

```console
(venv) $ git add some/interesting_file.py
(venv) $ git commit -m "Minor change"
black....................................................................Failed
- hook id: black
- files were modified by this hook

reformatted some/interesting_file.py

All done! ✨ 🍰 ✨
1 file reformatted.

flake8...................................................................Passed
check toml...........................................(no files to check)Skipped
check yaml...........................................(no files to check)Skipped
check for case conflicts.................................................Passed
check docstring is first.................................................Passed
fix end of files.........................................................Passed
trim trailing whitespace.................................................Passed
isort....................................................................Passed
pyupgrade................................................................Passed
docformatter.............................................................Passed
```

///

/// tab | Windows

```doscon
(venv) C:\...>git add some/interesting_file.py
(venv) C:\...>git commit -m "Minor change"
black....................................................................Failed
- hook id: black
- files were modified by this hook

reformatted some\interesting_file.py

All done! ✨ 🍰 ✨
1 file reformatted.

flake8...................................................................Passed
check toml...........................................(no files to check)Skipped
check yaml...........................................(no files to check)Skipped
check for case conflicts.................................................Passed
check docstring is first.................................................Passed
fix end of files.........................................................Passed
trim trailing whitespace.................................................Passed
isort....................................................................Passed
pyupgrade................................................................Passed
docformatter.............................................................Passed
```

///

You can then re-add any files that were modified as a result of the
pre-commit checks, and re-commit the change.

/// tab | macOS

```console
(venv) $ git add some/interesting_file.py
(venv) $ git commit -m "Minor change"
black....................................................................Passed
flake8...................................................................Passed
check toml...........................................(no files to check)Skipped
check yaml...........................................(no files to check)Skipped
check for case conflicts.................................................Passed
check docstring is first.................................................Passed
fix end of files.........................................................Passed
trim trailing whitespace.................................................Passed
isort....................................................................Passed
pyupgrade................................................................Passed
docformatter.............................................................Passed
[bugfix e3e0f73] Minor change
1 file changed, 4 insertions(+), 2 deletions(-)
```

///

/// tab | Linux

```console
(venv) $ git add some/interesting_file.py
(venv) $ git commit -m "Minor change"
black....................................................................Passed
flake8...................................................................Passed
check toml...........................................(no files to check)Skipped
check yaml...........................................(no files to check)Skipped
check for case conflicts.................................................Passed
check docstring is first.................................................Passed
fix end of files.........................................................Passed
trim trailing whitespace.................................................Passed
isort....................................................................Passed
pyupgrade................................................................Passed
docformatter.............................................................Passed
[bugfix e3e0f73] Minor change
1 file changed, 4 insertions(+), 2 deletions(-)
```

///

/// tab | Windows

```doscon
(venv) C:\...>git add some\interesting_file.py
(venv) C:\...>git commit -m "Minor change"
black....................................................................Passed
flake8...................................................................Passed
check toml...........................................(no files to check)Skipped
check yaml...........................................(no files to check)Skipped
check for case conflicts.................................................Passed
check docstring is first.................................................Passed
fix end of files.........................................................Passed
trim trailing whitespace.................................................Passed
isort....................................................................Passed
pyupgrade................................................................Passed
docformatter.............................................................Passed
```

///

Now you are ready to start hacking on BeeWare docs!

## Building BeeWare's documentation

### Build documentation locally

Once your development environment is set up, run:

/// tab | macOS

```console
(venv) $ tox -e docs
```

///

/// tab | Linux

```console
(venv) $ tox -e docs
```

///

/// tab | Windows

```doscon
(venv) C:\...>tox -e docs
```

///

The output of the file should be in the `docs/_build/html` folder. If
there are any markup problems, they'll raise an error.

### Live documentation preview

To support rapid editing of documentation, BeeWare also has a "live
preview" mode:

/// tab | macOS

```console
(venv) $ tox -e docs-live
```

///

/// tab | Linux

```console
(venv) $ tox -e docs-live
```

///

/// tab | Windows

```doscon
(venv) C:\...>tox -e docs-live
```

///

This will build the documentation, start a web server to serve the build
documentation, and watch the file system for any changes to the
documentation source. If a change is detected, the documentation will be
rebuilt, and any browser viewing the modified page will be automatically
refreshed.

### Documentation linting

The build process will identify reStructuredText problems, but BeeWare
performs some additional "lint" checks. To run the lint checks:

/// tab | macOS

```console
(venv) $ tox -e docs-lint
```

///

/// tab | Linux

```console
(venv) $ tox -e docs-lint
```

///

/// tab | Windows

```doscon
(venv) C:\...>tox -e docs-lint
```

///

This will validate the documentation does not contain:

- dead hyperlinks
- misspelled words

If a valid spelling of a word is identified as misspelled, then add the
word to the list in `docs/spelling_wordlist`. This will add the word to
the spellchecker's dictionary. When adding to this list, remember:

- We prefer US spelling, with some liberties for programming-specific
  colloquialisms (e.g., "apps") and verbing of nouns (e.g., "scrollable")
- Any reference to a product name should use the product's preferred
  capitalization. (e.g., "macOS", "GTK", "pytest", "Pygame",
  "PyScript").
- If a term is being used "as code", then it should be quoted as inline
  code rather than being added to the dictionary.

### Rebuilding all documentation

To force a rebuild for all the documentation:

/// tab | macOS

```console
(venv) $ tox -e docs-all
```

///

/// tab | Linux

```console
(venv) $ tox -e docs-all
```

///

/// tab | Windows

```doscon
(venv) C:\...>tox -e docs-all
```

///

The documentation should be fully rebuilt in the `docs/_build/html`
folder. If there are any markup problems, they'll raise an error.

## What to work on?

If you're looking for specific areas to improve, there are [tickets tagged
"documentation"](https://github.com/beeware/BeeWare/issues?q=is%3Aopen+is%3Aissue+label%3Adocumentation)
in BeeWare's issue tracker.

However, you don't need to be constrained by these tickets. If you can
identify an error in the tutorial, or an improvement that can be made,
start writing! Anything that improves the experience of the end user is
a welcome change.

## Submitting a pull request

Before you submit a pull request, there's a few bits of housekeeping to
do.

### Submit from a feature branch, not your `main` branch

Before you start working on your change, make sure you've created a
branch. By default, when you clone your repository fork, you'll be
checked out on your `main` branch. This is a direct copy of BeeWare's
`main` branch. To contribute to BeeWare itself, not the docs, please
review the repo README.

While you *can* submit a pull request from your `main` branch, it's
preferable if you *don't* do this. If you submit a pull request that is
*almost* right, the core team member who reviews your pull request may
be able to make the necessary changes, rather than giving feedback
asking for a minor change. However, if you submit your pull request from
your `main` branch, reviewers are prevented from making modifications.

Instead, you should make your changes on a *feature branch*. A feature
branch has a simple name to identify the change that you've made.

To create a feature branch, run:

/// tab | macOS

```console
(venv) $ git checkout -b fix-layout-bug
```

///

/// tab | Linux

```console
(venv) $ git checkout -b fix-layout-bug
```

///

/// tab | Windows

```doscon
(venv) C:\...>git checkout -b fix-layout-bug
```

///

Commit your changes to this branch, then push to GitHub and create a
pull request.
