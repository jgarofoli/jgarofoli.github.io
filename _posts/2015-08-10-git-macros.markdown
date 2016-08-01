---
layout: post
title: A git workflow
tags: ['git', ]
originaldate: 2015-08-10
reviseddate: 2015-08-15
changelog: |
    2015-08-15
    - update title
    - added link about revision selection

    2015-08-11
    - spelling corrections

    2015-08-10
    - original upload
---
It is intended that this post will also be a living document.  As such the 
contents will be edited and updated.  A change log will be at the bottom 
when the first changes occurs.

## Editing on a thread (a.k.a. rewriting history)

This is one way to do keep changes small and discrete, and non-spaghetti.
I'm not saying it's the best way, it's just one way.

1. create a small change (a) and commit it.
1. create another small change (b) and commit it.
1. create yet another small change (c).

Now you find that the commit (a) is incomplete and requires editing for (c) to 
be satisfactory.

Here is what to do.
First, issue this command:

    git rebase -i HEAD^^^

There are many ways to say "rebase from 3 commits ago".
Here is the [doc on that](https://git-scm.com/book/en/v2/Git-Tools-Revision-Selection).
This command will give you this screen:

    pick 2abb20e Add a manuscript latex style note.
    pick ca28c79 Small style change.
    pick 3e8963c ssh tunneling note draft

    # Rebase e6466fd..3e8963c onto e6466fd (       3 TODO item(s))

    # Commands:
    # p, pick = use commit
    # r, reword = use commit, but edit the commit message
    # e, edit = use commit, but stop for amending
    # s, squash = use commit, but meld into previous commit
    # f, fixup = like "squash", but discard this commit's log message
    # x, exec = run command (the rest of the line) using shell

    # These lines can be re-ordered; they are executed from top to bottom.
    ... (more stuff) ...

The important thing to know is that the first three lines are the last three commits, 
and they will be performed again in the order that they appear in when you write 
and exit this file.

What to do is this.  Change the first line, the line for commit (a) to be `edit` instead 
of `pick`.

    edit 2abb20e Add a manuscript latex style note.
    pick ca28c79 Small style change.
    pick 3e8963c ssh tunneling note draft

Then write and exit the file.  The status of the repository is now in the (a) edit.
At this point you can modify the files that were edited in that commit.  You
can add new files to the commit if necessary.  Do what you need and then
add the files to the commit, and then amend the commit.

    git add path/to/file
    ...
    git commit --amend

If needed, push this to the origin.
Then continue with the rebase.

    git rebase --continue

Now the repository is at the point (c) where we were at the beginning.
