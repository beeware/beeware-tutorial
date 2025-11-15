# Tutorial 0 - Let's get set up!

Before we build our first BeeWare app, we have to make sure we've got all the prerequisites for running BeeWare.

## Install Python { id="install-python" }

The first thing we'll need is a working Python interpreter.

/// tab | macOS

If you're on macOS, you can get an official Python installer from [the Python website](https://www.python.org/downloads). You can use any version of Python from 3.10 or newer (although you should avoid alphas, betas and release candidates). We strongly recommend using Python 3.13 or newer.

You can also install Python through [Homebrew](https://docs.brew.sh/Homebrew-and-Python), use [pyenv](https://github.com/pyenv/pyenv#simple-python-version-management-pyenv) to manage multiple Python installs, or use [Anaconda](https://docs.anaconda.com/anaconda/install/) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html). It doesn't matter *how* you've installed Python - it only matters that you can run `python3` from your terminal and get a working, supported Python interpreter.

Xcode and the Command-line Developer Tools provide a version of Python; however that Python is version 3.9. Python 3.9 has reached end-of-life, and is no longer supported by Python or BeeWare. You will *not* be able to use the Xcode-provided version of Python to run this tutorial.

To check the version of Python that you have installed, run the following command:

```console
$ python3 --version
```

If Python is installed, you'll see its version number.

///

/// tab | Linux

If you're on Linux, you'll install Python using the system package manager (`apt` on Debian/Ubuntu/Mint, `dnf` on Fedora, or `pacman` on Arch).

You should ensure that the system Python is Python 3.10 or newer; if it isn't (e.g., Ubuntu 20.04 ships with Python 3.8), you'll need to upgrade your Linux distribution to something more recent.

Support for Raspberry Pi is limited at this time.

**Important:** You *must* use the system Python provided by your operating system. Alternative Python installations (pyenv, Anaconda, manually compiled Python, etc.) will prevent you from successfully packaging your application for distribution in later steps of this tutorial.

///

/// tab | Windows

If you're on Windows, you can get the official installer from [the Python website](https://www.python.org/downloads). You can use any version of Python from 3.10 to 3.13 (although you should avoid alphas, betas and release candidates). We strongly recommend using Python 3.13.

Support for Windows on ARM64 is limited at this time.

You can also install Python from the Windows App Store, or use [Anaconda](https://docs.anaconda.com/anaconda/install/) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html). It doesn't matter *how* you've installed Python - it only matters that you can run `python3` from your command prompt and get a working, supported Python interpreter.

///

## Install dependencies { id="install-dependencies" }

Next, install the additional dependencies needed for your operating system:

/// tab | macOS

Building BeeWare apps on macOS requires:

- **Git**, a version control system. This is included with Xcode or the command line developer tools, which you installed above. You may need to open Xcode for the first time in order for Git to work in your terminal session. If it still doesn't register that Git is installed, you may need to restart your terminal session.

///

/// tab | Linux

To support local development, you'll need to install some system packages. The list of packages required varies depending on your distribution:

### Ubuntu / Debian

```console
$ sudo apt update
$ sudo apt install git build-essential pkg-config python3-dev python3-venv libgirepository1.0-dev libcairo2-dev gir1.2-gtk-3.0 libcanberra-gtk3-module
```

### Fedora

```console
$ sudo dnf install git gcc make pkg-config rpm-build python3-devel gobject-introspection-devel cairo-gobject-devel gtk3 libcanberra-gtk3
```

### Arch / Manjaro

```console
$ sudo pacman -Syu git base-devel pkgconf python3 gobject-introspection cairo gtk3 libcanberra
```

### OpenSUSE Tumbleweed

```console
$ sudo zypper install git patterns-devel-base-devel_basis pkgconf-pkg-config python3-devel gobject-introspection-devel cairo-devel gtk3 'typelib(Gtk)=3.0' libcanberra-gtk3-module
```

///

/// tab | Windows

Building BeeWare apps on Windows requires:

- **Git**, a version control system. You can download Git from from <nospell>[git-scm.com](https://git-scm.com/downloads/)</nospell>.

After installing these tools, you should ensure you restart any terminal sessions. Windows will only expose newly installed tools terminals started *after* the install has completed.

///

## Set up a virtual environment

We're now going to create a virtual environment - a "sandbox" that we can use to isolate our work on this tutorial from our main Python installation. If we install packages into the virtual environment, our main Python installation (and any other Python projects on our computer) won't be affected. If we make a complete mess of our virtual environment, we'll be able to simply delete it and start again, without affecting any other Python project on our computer, and without the need to re-install Python.

/// tab | macOS

```console
$ mkdir beeware-tutorial
$ cd beeware-tutorial
$ python3 -m venv beeware-venv
$ source beeware-venv/bin/activate
```

///

/// tab | Linux

```console
$ mkdir beeware-tutorial
$ cd beeware-tutorial
$ python3 -m venv beeware-venv
$ source beeware-venv/bin/activate
```

///

/// tab | Windows

```doscon
C:\...>md beeware-tutorial
C:\...>cd beeware-tutorial
C:\...>py -3.12 -m venv beeware-venv
C:\...>beeware-venv\Scripts\activate
```

If you're not using Python 3.12, replace the `-3.12` in these instructions with the version number that you are using.

/// admonition | Errors running PowerShell Scripts

If you're using PowerShell, and you receive the error:

```console
File C:\...\beeware-tutorial\beeware-venv\Scripts\activate.ps1 cannot be loaded because running scripts is disabled on this system.
```

Your Windows account doesn't have permission to run scripts. To fix this:

1. Run [Windows PowerShell as Administrator](https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.4).
2. Run `set-executionpolicy RemoteSigned`
3. Select `Y` to change the execution policy.

Once you've done this you can rerun `beeware-venv\Scripts\activate.ps1` in your original PowerShell session (or a new session in the same directory).

///

///

If this worked, your prompt should now be changed - it should have a `(beeware-venv)` prefix. This lets you know that you're currently in your BeeWare virtual environment. Whenever you're working on this tutorial, you should make sure your virtual environment is activated. If it isn't, re-run the last command (the `activate` command) to re-activate your environment.

/// admonition | Alternative virtual environments

If you're using Anaconda or miniconda, you may be more familiar with using conda environments. You might also have heard of `virtualenv`, a predecessor to Python's built in `venv` module. As with Python installs -if you're on macOS or Windows, it doesn't matter *how* you create your virtual environment, as long as you have one. If you're on Linux, you should stick to `venv` and the system Python.

///

## Next steps

We've now set up our environment. We're ready to [create our first BeeWare application](tutorial-1.md).
