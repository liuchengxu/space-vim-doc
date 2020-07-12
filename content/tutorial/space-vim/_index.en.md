---
title: "space-vim"
---

Most of key mappings are defined according to the mnemonic priciples from spacemacs.

Using `:verbose` to take a closer look at a defined key map, e.g., `:verbose nmap <Leader>bh`:

```
:verbose nmap <Leader>bh
n  <Space>bh   * :Startify<CR>
        Last set from ~/.space-vim/layers/+distributions/better-defaults/keybindings.vim
```

{{% notice info %}}
When 'verbose' is non-zero, listing the value of a Vim option or a key map or
an abbreviation or a user-defined function or a command or a highlight group
or an autocommand will also display where it was last defined.  If it was
defined manually then there will be no "Last set" message.  When it was
defined while executing a function, user command or autocommand, the script in
which it was defined is reported.
See `:h verbose-cmd`.
{{% /notice %}}
