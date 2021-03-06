

The purpose of this file is to function as a memo aid for the ones of us who will assist our collegues in the transition aftermath.

Read the [documentation](docu-svn-user.html).

## Procedure

Check whether you have a new enough svn:

* svn --version

The version should preferably be at least 1.4 (but earlier versions ought to work, and 1.3 does work)

The checkout command is:

svn co https://gtsvn.uit.no/repos/trunk gtsvn

Copy existing non-cvs-files (in the cvs dev catalogues to the corresponding svn)

## Placement of the svn catalogue

We here assume it is `$HOME/gtsvn/`.

Some of us have other systems. Thus, in all our scripts, we operate with an alias `GTHOME`. We urge all to put the line

export GTHOME=~/gtsvn

in their `.bashrc` file (or any other address than gtsvn if you would prefer that). In that way we have a flexible system.

##  .bashrc-file

1. The paths of the type $HOME/gt etc. should be changed to $HOME/gtsvn/gt etc
1. The lo, osmj, etc. aliases must be corrected, e.g. so that ~/gt must be ~/gtsvn/gt
1. The up alias must be corrected, e.g.
    1. alias up="cd $HOME/gtsvn/ && svn up"
1. Some paths in .emacs must be corrected:
    1. (load "~/gtsvn/gt/script/emacs/namelex")
    1. (load "~/gtsvn/gt/script/emacs/correct")
1. The makefiles in st must get updated script cat reference
1. The dict/../src catalogues must have their *.sh executable
1. All files in the gt/script must be executables.

## Password

All users have received a password. It will be used once, and changing it is thus not that crucial. If someone wants a password to remember, they may have it changed by a superuser:

```
htpasswd -m /etc/subversion/svn-auth-file sally
New password: *******
Re-type new password: *******
Adding password for user sally
```

## Commands

Most commands are familiar from cvs:

* svn up (note that this only updates, it does not tell anything abot local M status)
* svn ci -m "Log message" filename
* svn log filename

Then there are new commands. The most important is:

* svn status = command to check for status (local and central modifications, will list all and only modified files)
    - svn status has two modes:
        - one fast, without network access - it will check only whether you have modified files locally: `svn status`
        - one slower, **with** network access - it will also check against the repository: `svn status -u` (-u as in Update, to check whether an Update is needed)

And remember the svn book!
