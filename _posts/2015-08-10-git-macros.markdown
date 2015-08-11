---
layout: post
title: A git macro # update this 
tags: ['git', ]
original_date: 2015-08-10
#revised_date: 2015-08-11
---
It is intended that this post will also be a living document.  As such the 
contents will be edited and updated.  A change log will be at the bottom 
when the first changes occurs.

By "macro" I mean a routine that I find myself doing often.

## Editing on a thread (a.k.a. rewriting history)

This is one way to do keep changes small and discrete, and non-spaghetti.

1. create a small change (a) and commit it.
1. create another small change (b) and commit it.
1. create yet another small change (c).

Now you find that the commit (a) is incomplete and requires editing for (c) to 
be satisfactory.

Here is what to do.
First, issue this command:

```bash
git rebase -i HEAD^^^
```

There are many ways to say "rebase from 3 commits ago".
This command will give you this screen:

```
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
```

The important thing to know is that the first three lines are the last three commits, 
and they will be performed again in the order that they appear in when you write 
and exit this file.

What to do is this.  Change the first line, the line for commit (a) to be `edit` instead 
of `pick`.

```
edit 2abb20e Add a manuscript latex style note.
pick ca28c79 Small style change.
pick 3e8963c ssh tunneling note draft
```

Then write and exit the file.  The status of the repository is now in the (a) edit.
At this point you can modify the files that were edited in that commit.  You
can add new files to the commit if necessary.  Do what you need and then
add the files to the commit, and then amend the commit.

```
git add path/to/file
...
git commit --amend
```

If needed, push this to the origin.
Then continue with the rebase.

```
git rebase --continue
```

Now the repository is at the point (c) where we were at the beginning.
