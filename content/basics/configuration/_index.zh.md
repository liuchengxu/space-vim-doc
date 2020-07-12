---
title: "定制配置"
weight: 20
---

### 核心理念

space-vim 的模块化设计取自于 spacemacs，其核心理念是 layer，可以点击[这里](https://github.com/syl20bnr/spacemacs/tree/master/layers)查看 spacemacs 的 layer，点击[这里](https://github.com/liuchengxu/space-vim/tree/master/layers)查看 space-vim 的layer。其中，以 `+` 开头的目录我称之为 topic，其下层目录是该 topic 的一些 layer。[LAYERS.md](https://github.com/liuchengxu/space-vim/blob/master/layers/LAYERS.md) 是所有的 layer 清单。

```
layers
├── +lang
│   ├── c-c++
│   ├── graphviz
│   ├── html
│   ├── markdown
│   └── python
├── +themes
│   ├── airline
│   └── lightline
├── +tools
│   ├── fzf
│   └── ycmd
├── +version-control
│   ├── git
│   └── github
├── +vim
│   ├── better-defaults
│   ├── programming
│   └── text-align
└── LAYERS.md
```

### `.spacevim`

在 spacemacs 中，可以使用 `.spacemacs` 对 spacemacs 进行定制。与 spacemacs 相类似，space-vim 可以通过 `.spacevim` 来完成配置的个性化。`.spacevim`模板如下：

```vim
" Let Vim and NeoVim shares the same plugin directory.
" Comment it out if you don't like
let g:spacevim_plug_home = '~/.vim/plugged'

" Enable the existing layers in space-vim
function! Layers()

  " Default layers
  Layer 'fzf'
  Layer 'unite'
  Layer 'better-defaults'

endfunction

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

