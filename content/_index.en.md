---
title: "space-vim"
weight: 10
---

# space-vim

space-vim is a vim distribution for vim plugins and resources, compatible with Vim and Neovim.

It is inspired by [spacemacs](http://spacemacs.org) and mimics spacemacs in a high level, especially in the whole architecture, key bindings and GUI. if have ever tried spacemacs, you will find space-vim is very similar to it in user experience.

The distribution is completely customizable using `.spacevim`, which is equivalent to `.spacemacs` in spacemacs.

![screenshot1](images/screenshot1.png)

## Features

#### Beautiful interface

I have written a vim colorscheme [space-vim-dark](https://github.com/liuchengxu/space-vim-dark) based on spacemacs-dark theme. You could also try [spacemacs-theme.vim](https://github.com/colepeters/spacemacs-theme.vim).

#### Mnemonic key bindings

commands have mnemonic prefixes like `SPC b` for all the buffer commands.

Meanwhile, the whole key bindings have been well adapted for vim for the lack of great plugins similar to which-key in emacs. Most key bindings are limited to no more than two keystrokes without counting <Leader> or <LocalLeader> in, e.g. `SPC x d` to delete trailing whitespaces.

For different language layers, <LocalLeader>, , as default in space-vim, can be seen as the major-mode prefix in spacemacs.

#### Lean and mean

No nonsense wrappers, free from being bloated.

## For whom?

- the **novice** vim users
- the vimmers who pursuit a beautiful appearance
- the users **using both vim and spacemacs**

If you have been a vimmer for quite a while, just pick out the part you are interested in. space-vim is well-organized due to the layers concept, you can easily find what you want. Since some guys are interested in the statusline part of space-vim, this section has been extracted as [eleline.vim](https://github.com/liuchengxu/eleline.vim).

![statusline](images/statusline.png)

## Contribute to this documentation

Feel free to update this content, just click the **Edit this page** link displayed on top right of each page, and pullrequest it

{{% notice info %}}
Your modification will be deployed automatically when merged.
{{% /notice %}}
