---
title: "Configuration"
weight: 20
---

You can use `.spacevim` in your home directory to customize space-vim, where you can enable the existing layers, add your extra plugins and private configurations.

If `.spacevim` does not exist, vanilla vim will be loaded! Refer to [init.spacevim](https://github.com/liuchengxu/space-vim/blob/master/init.spacevim) as an example.

### Presetting

```vim
" Let Vim and NeoVim shares the same plugin directory
let g:spacevim_plug_home = '~/.vim/plugged'

" Change the background color of theme space-vim-dark (default 235)
let g:space_vim_dark_background = 234
```

### `Layers()`

Please refer to [LAYERS](layers/LAYERS.md) to take a look at the whole shipped layers.

```vim
" Enable the existing layers in space-vim
function! Layers()

  " Default layers
  Layer 'fzf'
  Layer 'unite'
  Layer 'better-defaults'

endfunction
```

### `UserInit()`

```vim
" Add your own plugins
function! UserInit()

  " The default leader key is space key.
  " Uncomment the line below and modify "<\Space>" if you prefer another
  " let g:spacevim_leader = "<\Space>"

  " The default local leader key is comma.
  " Uncomment the line below and modify ',' if you prefer another
  " let g:spacevim_localleader = ','

  " Install personal plugins
  " Plug 'hecal3/vim-leader-guide'

endfunction
```

### `UserConfig()`

```vim
" Override the default settings as well as adding extras
function! UserConfig()

  " If you have installed the powerline fonts and want to enable airline layer
  " let g:airline_powerline_fonts=1

  " Use gui colors in terminal if available
  if has('termguicolors')
    set termguicolors
    if g:spacevim_tmux
      " If use vim inside tmux, see https://github.com/vim/vim/issues/993
      " set Vim-specific sequences for RGB colors
      let &t_8f = "\<Esc>[38;2;%lu;%lu;%lum"
      let &t_8b = "\<Esc>[48;2;%lu;%lu;%lum"
    endif
  endif

endfunction
```
