spkg
====

a simple slackbuild script package builder

spkg is designed to be a "light" variant to third-party tools like "sbopkg"
for Slackware Linux.  I originally developed sbopkg and I think it has been
helpful to Slackware users who want a way to easily manage the process of
building and installing third-party software from SlackBuilds.org and other
similar repositories of SlackBuild scripts.

However, I also wanted try creating something simpler to use and maintain.
This was the basis for working on spkg.  It is not a replacement for sbopkg
per se and it does not have all the features of sbopkg.  But, it works for me
and if it works for you, then that's cool.

spkg is just a single Bash script of less than 700 lines (and a good chunk of
that is the license, the user configuration section, and the usage and help
functions).  The actual working part of the script is probably about 575
lines so it is far smaller than sbopkg.

Hopefully, it should be fairly self-explanatory.  The only required changes
are to edit the $REPOPATH and $SOURCEDIR variables at the top of the script.
The $SPKGDIR variable is optional but might be useful.  The $SPKGDIR directory
is where you can save edited copies of the SlackBuild script or the .info file
or save build options that can be passed to a SlackBuild script in a *.options
file (e.g. openbox.options).  Think of this as an "override" directory where
you can save edited files without touching the actual repo.  Anything here
will be sourced after sourcing the actual SlackBuild script or the .info file
in the repository.

spkg does not handle the actual syncing of the repo.  I figured that the user
can do this outside of spkg, either with rsync, or git, or ftp or whatever the
user needs.  The user can probably write a wrapper script around spkg in fact
to handle the syncing.  Again, spkg is supposed to be 'simple'.  :-)

spkg supports sbopkg-style queuefile with the exception that it does not read
build options passed in the queuefile after the pipe ('|') character.  Save
those build options in a *.options file in the $SPKGDIR directory instead.

Here is the command line output:

Usage: spkg [OPTION] <packagename(s)> or <queuefile>:

    -d            Download the source(s) for a package in $REPOPATH.
    -h            Additional help. Please read this.
    -i            Download and install a package in $REPOPATH.
    -l            List installed packages in $REPOPATH.
    -p            Print the .info and README for a package in $REPOPATH.
    -q            Download and install packages in a /path/to/queuefile.
    -r            Print the list of REQUIRES for a package in $REPOPATH.
    -s            Search for a package in $REPOPATH.
    -u            Upgrade installed packages in $REPOPATH.
    -w            Write a queuefile based on installed $REPOPATH packages.

Enjoy!
