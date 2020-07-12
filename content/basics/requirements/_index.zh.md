---
title: "安装准备"
weight: 10
---

#### 引言

首先，肯定是先安装 [Vim](https://github.com/vim/vim) 或者 [NeoVim](https://github.com/neovim/neovim)。在这个环节需要注意的是，Vim 编译时是否包含了某个特性，比如 `+python`，因为很多插件使用了 Python 这样的扩展语言，而 NeoVim 安装时默认已包含全部特性。另外，由于 Vim8 才引入异步，时钟等特性，而这些会给用给用户体验带来很大的提升，因为有必要安装最新版本的 Vim。

如下图，在终端中执行 `vim --version`，或者在 Vim 中执行 `:version`，即可看到所有细节。带 `+` 的就是已包含该特性，`-` 则是不包含，比如下面的 `+python3` 就是支持 Python3, `-python` 就是不支持 Python2。

```bash
$ vim --version
VIM - Vi IMproved 8.0 (2016 Sep 12, compiled Oct 15 2017 09:28:05)
MacOS X (unix) version
Included patches: 1-1175
Compiled by Homebrew
Huge version without GUI.  Features included (+) or not (-):
+acl             +file_in_path    +mouse_sgr       +tag_old_static
+arabic          +find_in_path    -mouse_sysmouse  -tag_any_white
+autocmd         +float           +mouse_urxvt     -tcl
-balloon_eval    +folding         +mouse_xterm     +termguicolors
-browse          -footer          +multi_byte      +terminal
++builtin_terms  +fork()          +multi_lang      +terminfo
+byte_offset     -gettext         -mzscheme        +termresponse
+channel         -hangul_input    +netbeans_intg   +textobjects
+cindent         +iconv           +num64           +timers
-clientserver    +insert_expand   +packages        +title
+clipboard       +job             +path_extra      -toolbar
+cmdline_compl   +jumplist        +perl            +user_commands
+cmdline_hist    +keymap          +persistent_undo +vertsplit
+cmdline_info    +lambda          +postscript      +virtualedit
+comments        +langmap         +printer         +visual
+conceal         +libcall         +profile         +visualextra
+cryptv          +linebreak       -python          +viminfo
+cscope          +lispindent      +python3         +vreplace
+cursorbind      +listcmds        +quickfix        +wildignore
+cursorshape     +localmap        +reltime         +wildmenu
+dialog_con      +lua             +rightleft       +windows
+diff            +menu            +ruby            +writebackup
+digraphs        +mksession       +scrollbind      -X11
-dnd             +modify_fname    +signs           -xfontset
-ebcdic          +mouse           +smartindent     -xim
+emacs_tags      -mouseshape      +startuptime     -xpm
+eval            +mouse_dec       +statusline      -xsmp
+ex_extra        -mouse_gpm       -sun_workshop    -xterm_clipboard
+extra_search    -mouse_jsbterm   +syntax          -xterm_save
+farsi           +mouse_netterm   +tag_binary
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
 2nd user vimrc file: "~/.vim/vimrc"
      user exrc file: "$HOME/.exrc"
       defaults file: "$VIMRUNTIME/defaults.vim"
  fall-back for $VIM: "/usr/local/share/vim"
Compilation: clang -c -I. -Iproto -DHAVE_CONFIG_H   -DMACOS_X_UNIX  -g -O2 -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=1
Linking: clang   -L. -fstack-protector -L/usr/local/opt/libyaml/lib -L/usr/local/opt/readline/lib -L/usr/local/opt/libksba/lib -L/usr/local/opt/openssl/lib  -L/usr/local/lib -o vim        -lm  -lncurses -liconv -framework Cocoa  -L/usr/local/lib -llua -fstack-protector  -L/System/Library/Perl/5.18/darwin-thread-multi-2level/CORE -lperl  -L/Users/xlc/anaconda3/
lib/python3.5/config-3.5m -lpython3.5m -framework CoreFoundation  -lruby.2.3.0 -lobjc -L/Users/xlc/.rvm/rubies/ruby-2.3.0/lib
```

#### 安装

##### Neovim

[Installing Neovim](https://github.com/neovim/neovim/wiki/Installing-Neovim)

##### Vim

- macOS

    ```bash
    $ brew install vim --with-override-system-vi --with-python3 --with-lua
    ```
- Linux

  [Building Vim from source](https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source)
