---
title: "Some Vim commands to keep handy"
tags: vim
original_date: 2015-08-01
---
## Sort a selection

Pass the range from visual selection by highlighting it and then pressing
`:` (yes, it's that easy).

```vim
:{range}sort u
```

## Reload vimrc file

```vim
:so $MYVIMRC
" or automatically
augroup myvimrc
    au!
    au BufWritePost .vimrc,_vimrc,vimrc,.gvimrc,_gvimrc,gvimrc so $MYVIMRC | if has('gui_running') | so $MYGVIMRC | endif
augroup END
```

