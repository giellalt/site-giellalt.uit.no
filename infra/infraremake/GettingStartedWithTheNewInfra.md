# Installation and setup

The required steps for setting up the computer and installing the
auxiliary programs needed are described in our
[Getting Started guide](../GettingStarted.html).

# Check out the source code for language modelling

1. First, decide what language(s) you are interested in working on, from
  [the following list](https://giellalt.uit.no/lang/index.html)
1. The alphabetic list on the page gives the ISO code of all the languages
1. Then go to the page of the source code: [github.com/giellalt](https://github.com/giellalt).
  Let us say you are interested in Eastern Mari. The ISO code is '*mhr*',
  and the address is [github.com/giellalt/lang-mhr](https://github.com/giellalt/lang-mhr).
  Exchange *mhr* with the code of the language you want.
1. The GitHub page will show an INSTALLATION file with instructions. You may also
  see [this page](https://giellalt.uit.no/infra/MigratingToGit.html) for more
  specific instructions (start at point 2).

# Getting started with your language

When you have installed and checked out qw explained above, do the following:

```
cd $HOME/giella/fin
./autogen.sh -l
./configure
```

(replace **fin**, the code for Finnish, with the language(s) you checked out). Now
you are ready to start working. More info about where to find the different
pieces of source code can be found on [this page](NewinfraCatalogues.html).

**NOTE** that the command `./configure` assume that you checked out the
**Xerox compilers** (see the Getting s

To build the transducers and other tools for linguistic analysis, do:

```make```

To run the preinstalled tests, do:

```make check```

**WARNING**

You may encounter troubles with your CLASSPATH. We are working on it,
here is a fix if the compiler complains it is not set:
In the langs directory, write `export CLASSPATH=`.

Happy linguistic coding!
