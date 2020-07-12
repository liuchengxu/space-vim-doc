---
title: "Installation"
weight: 15
---

### Linux and macOS

#### one-line installer

```bash
$ bash <(curl -fsSL https://raw.githubusercontent.com/liuchengxu/space-vim/master/install.sh)
```

#### Makefile

```bash
$ git clone https://github.com/liuchengxu/space-vim.git ~/.space-vim
$ cd ~/.space-vim
$ make vim     # install space-vim for Vim
$ make neovim  # install space-vim for NeoVim
```

### Windows

The easist way is to download [install.cmd](https://raw.githubusercontent.com/liuchengxu/space-vim/master/install.cmd) and run it as administrator.

### Manual


Given git and Vim/NeoVim have been installed already:

1. Clone [space-vim](https://github.com/liuchengxu/space-vim)

```bash
$ git clone https://github.com/liuchengxu/space-vim.git ~/.space-vim
```

2. Install [vim-plug](https://github.com/junegunn/vim-plug), refer to vim-plug installation section for more information.

3. Create the symlinks.

    **Linux and macOS**

    ```bash
    # For Vim
    $ ln -s ~/.space-vim/init.vim ~/.vimrc

    # For NeoVim
    $ ln -s ~/.space-vim/init.vim ~/.config/nvim/init.vim

    # Both for Vim and NeoVim
    $ cp ~/.space-vim/init.spacevim ~/.spacevim
    ```

4. Open vim, then space-vim will automatically install the missing plugins. If auto-installation fails unexpectly, please try running `:PlugInstall` manually.
