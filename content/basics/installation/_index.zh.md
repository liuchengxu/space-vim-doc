---
title: "快速安装"
weight: 15
---

### Linux and macOS

#### 快速安装

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

1. [下载 git](https://git-scm.com/download/win)

2. [下载 Vim](https://github.com/vim/vim-win32-installer/releases)

3. 下载 [vim-plug](https://github.com/junegunn/vim-plug#installation):

    **windows (PowerShell)**

    ```powershell
    md ~\.vim\autoload
    $uri = 'https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
    (New-Object Net.WebClient).DownloadFile(
      $uri,
      $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath(
        "~\.vim\autoload\plug.vim"
      )
    )
    ```

4. 进入用户目录，右键打开 *Git Bash* 选择 `Git Bash Here`.

    下载 space-vim 并建立软连接。

    ```bash
    $ git clone https://github.com/liuchengxu/space-vim.git ~/.space-vim
    $ ln -s ~/.space-vim/init.vim ~/.vimrc
    $ cp ~/.space-vim/init.spacevim ~/.spacevim
    ```

5. 打开 Vim，执行 `:PlugInstall`.
