===============
git meld README
===============

SYNOPSIS
========
    git meld [options] <commit>{0,2} [--] [<path>...]

DESCRIPTION
===========
    git meld is a git command that allows you to compare and edit treeishs
    between revisions using meld. git meld is a frontend to git diff and accepts
    the same options and arguments.

    It is essentially an extended git-difftool for tools that support comparing
    directories rather than having git call the external tool for every file
    that has changed

EXAMPLE
=======

    Show the differences between HEAD and your working directory:
        $ git meld
    
    Show the differences between the tips of branch master and branch topic
        $ git meld master..topic
    
    Show all the changes made to branch topic since it branched off branch
    master
        $ git meld master...topic

INSTALLATION
============
    Add a git alias to your gitconfig with:
        $ git config --global alias.meld \!/path/to/git-meld/git-meld.pl

    Alternatively add:

        [alias]
        	meld = !/path/to/git-meld/git-meld.pl
    
    To your ~/.gitconfig

CAVEATS
=======
    git meld can display the differences between two commits or between HEAD and
    the working directory, but not between an arbitrary commit and the working
    directory.
    
    There is currently no way of comparing anything to what is in the staging
    area

HOW IT WORKS
============
    git meld uses "git diff --name-only" to extract the files that have changed
    between the two commits and then makes a copy of these files into a
    temporary directory before invoking meld on these copies.
