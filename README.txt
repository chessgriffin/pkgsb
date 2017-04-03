pkgsb
====

a simple slackbuild script package builder

pkgsb is designed to be a "light" variant to third-party tools like
"sbopkg" for Slackware Linux.  I originally developed sbopkg and I think it
has been helpful to Slackware users who want a way to easily manage the
process of building and installing third-party software from
SlackBuilds.org and other similar repositories of SlackBuild scripts.

However, I also wanted to try creating something simpler to use and
maintain.  This was the basis for working on pkgsb.  It is not a
replacement for sbopkg per se and it does not have all the features of
sbopkg.  But, it works for me and if it works for you, then that's cool.

pkgsb is just a single Bash script of a few hundred lines (and a good chunk
of that is the license, the user configuration section, and the usage and
help functions).  The actual working part of the script is far smaller
than sbopkg.

Hopefully, it should be fairly self-explanatory.  The only required changes
are to edit the $REPOPATH and $SOURCEDIR variables at the top of the
script.  The $pkgsbDIR variable is optional but might be useful.  The
$SPKGDIR directory is where you can save edited copies of the SlackBuild
script or the .info file or save build options that can be passed to a
SlackBuild script in a *.options file (e.g. openbox.options).  Think of
this as an "override" directory where you can save edited files without
touching the actual repo.  Anything here will be sourced after sourcing the
actual SlackBuild script or the .info file in the repository.

pkgsb does not handle the actual syncing of the repo.  I figured that the
user can do this outside of pkgsb, either with rsync, or git, or ftp or
whatever the user needs.  The user can probably write a wrapper script
around pkgsb in fact to handle the syncing.  Again, pkgsb is supposed to be
'simple'.  :-)

pkgsb supports sbopkg-style queuefile with the exception that it does not
read build options passed in the queuefile after the pipe ('|') character.
Save those build options in a *.options file in the $pkgsbDIR directory
instead.

DISCLAIMER: pkgsb is still alpha code under development.  It might destroy
your machine, eat all your cookies, or leave your refrigerator door open.
Use at your own risk!

Here is the command line output:

Usage: pkgsb [OPTION] <packagename(s)> or <queuefile>:

    -b            Browse the subdirectories/categories in $REPOPATH.
    -d            Download the source(s) for a package in $REPOPATH.
    -h            Additional help. Please read this.
    -i            Download and install a package in $REPOPATH.
    -l            List installed packages in $REPOPATH.
    -p            Print the .info and README for a package in $REPOPATH.
    -q            Download and install packages in a /path/to/queuefile.
    -r            Print the list of REQUIRES for a package in $REPOPATH.
    -R            Reverse REQUIRES - where package is listed in REQUIRES.
    -s            Non case sensitive search for a package in $REPOPATH.
    -u            Upgrade installed packages in $REPOPATH.
    -w            Write a queuefile for installed $REPOPATH packages.

Package names are case-sensitive but -s will search non case sensitive.

Enjoy!
