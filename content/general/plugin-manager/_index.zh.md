---
title: "Vim 插件管理器概览"
weight: 20
---

### 什么是 Vim 插件

见 `:h plugin` :
>Vim's functionality can be extended by adding plugins.  A plugin is nothing
more than a Vim script file that is loaded automatically when Vim starts.  You
can add a plugin very easily by dropping it in your plugin directory.

一个 Vim 插件不过是 Vim 启动时自动加载的 Vim script 脚本而已. Vim 启动时会自动加载 runtimepath 中的 plugin 子目录下的所有文件. 那么, runtimepath 又是什么? `:h runtimepath`:

![runtimepath](http://upload-images.jianshu.io/upload_images/127313-b1aa434da6f5c4b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

runtimepath 就是 Vim 查找脚本文件的地方, runtimepath 之于 Vim ，
 有点类似 $PATH 之于 shell. `:echo &runtimepath` 即可进行查看.

runtimepath 下面有两个子目录需要注意:


![goyo.vim](http://upload-images.jianshu.io/upload_images/127313-bc79a8594adc630c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-  **plugin:** plugin 目录下面的所有文件都会在启动时进行加载. 

- **autoload:** autoload 里面的文件, 在启动时并不会进行加载, 而是通过一种特殊的方式进行加载, 主要是命名上有要求, 详情见 `:h autoload`, 这里就不展开了. 
autoload 只不过是为了加速 Vim 的启动, 因为要将所有的内容放在 plugin 下面的话，可能会导致启动时间增加, 而且也没有必要, 因为很多内容并不常用, 无须在启动时加载. "坏处" 就是需要在命名上进行规范. 

上图中还有一个 doc 目录, 它里面通常放的是插件的 help 内容.

如果不用插件管理器, 手动管理 Vim Script 脚本文件也可以. 但是当插件一多的话, 就会变得很可怕, 更新, 删除都会很麻烦. 直到目前为止, Vim 并没有标准的插件管理器, 尽管 Vim 8 已经引入了 packages 的管理功能 (`:h packages`).

### 主流插件管理器

主流的插件管理器有下面这几个,  从早期现在看来 "稍显简陋" 的 [pathogen](https://github.com/tpope/vim-pathogen), 到 [Vundle](https://github.com/VundleVim/Vundle.vim) 已经是真正有了几分 manager 的意思,  再到现在比较流行的 [vim-plug](https://github.com/junegunn/vim-plug) 和 [dein.vim](https://github.com/Shougo/dein.vim) ( [neobundle](https://github.com/Shougo/neobundle.vim) 是 dein 作者前一个插件管理器作品, 已经弃用了 ). vim-plug 和 dein.vim 现在都支持并行安装和延迟加载, 这对于有几十甚至上百个插件的人来说是非常重要的. 

我比较喜欢 vim-plug, [space-vim](https://github.com/liuchengxu/space-vim) 也是使用的 vim-plug, 因为它设计简单, 使用方便, 功能也都算完备.

![vim-plug](http://upload-images.jianshu.io/upload_images/127313-2a1729933485b28f.gif?imageMogr2/auto-orient/strip)

### 非主流插件管理器

除了主流的插件管理器, 还有很多非主流的管理器. 主流管理器都是用 Vim Script 实现的, 只是有些功能, 比如并行安装, 会有一些版本或是编译的特性 (`+python`等)要求, 使用上没有什么依赖. 而一些非主流管理器可能是用其他语言写的, 需要你事先安装了那个语言, 比如有用 Rust 和 Haskell 实现的.

其实一个管理器的主要功能就是到 GitHub 上下载插件 (`git clone`) 然后放到指定目录, [这里](https://junegunn.kr/2013/09/writing-my-own-vim-plugin-manager/) 是 vim-plug 的作者对 vim-plug 诞生写的一篇文章, 里面介绍了 vim-plug 的由来.

下面是一些非主流的 Vim 插件管理器, 有兴趣的可以自行查看:

- [pack](https://github.com/maralla/pack): Rust
- [miv](https://github.com/itchyny/miv): Haskll
- [vim-addon-manager](https://github.com/MarcWeber/vim-addon-manager)
- [minpac](https://github.com/k-takata/minpac)
- [apt-vim](https://github.com/egalpin/apt-vim)
- [vimogen](https://github.com/rkulla/vimogen)
