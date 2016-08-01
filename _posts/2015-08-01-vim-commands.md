---
title: "Some Vim commands to keep handy"
tags: vim
originaldate: 2015-08-01
reviseddate: 2015-09-20
changelog: |
    2015-09-20
    - Added paragraph formatting command

    2015-08-15
    - Added navigating help

    2015-08-01
    - original upload
---
## Format a paragraph

Just issue the command ```gqip```.  Remember to have ```:setl tw=80``` or
something similar set first.

## Sort a selection

Pass the range from visual selection by highlighting it and then pressing
`:` (yes, it's that easy).

    :{range}sort u

## Reload vimrc file

    :so $MYVIMRC
    " or automatically
    augroup myvimrc
        au!
        au BufWritePost .vimrc,_vimrc,vimrc,.gvimrc,_gvimrc,gvimrc so $MYVIMRC | if has('gui_running') | so $MYGVIMRC | endif
    augroup END

## Navigating the help file

Use `ctrl-]` to follow a link and `ctrl-t` to move back.

