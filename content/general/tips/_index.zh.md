---
title: "Vim 小知识点"
weight: 20
---

`:set` 将会显示所有默认值被修改过的选项 (option):

![set](http://upload-images.jianshu.io/upload_images/127313-354a8e454e159efd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在一个选项后面加上 `?` 来查看当前的选项值, 比如, `:set undodir?` .

在一个选项后面加上 `&` 恢复其默认值, 比如, `:set number?` . 在使用 AsyncRun 时就曾经遇到过一个问题, [#37](https://github.com/skywind3000/asyncrun.vim/issues/37) .

`:scriptenames`, 按 source 的先后顺序列出所有 source 的文件, source 其实就是 load, 加载文件:


![scriptnames](http://upload-images.jianshu.io/upload_images/127313-8e9285efeb1ccb72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`:smile`, 彩蛋:


![smile](http://upload-images.jianshu.io/upload_images/127313-0a9d162ec3b49d0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

使用 <Esc> 或者 `<Ctrl-c>` 从 insert mode 回到 normal mode.

`:windo` 对于所有的 window 执行一个操作, `:bufdo` 对所有的 buffer 执行一个操作.

`ZZ` (两个大写的 Z)等于 `:wq`, 保存并退出.

`:ls` 列出所有的 buffer.

`:e .` 或者 `:Ex` 打开内置的文件或目录浏览器.


![Ex](http://upload-images.jianshu.io/upload_images/127313-ec9c9007bfc9fa0c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`:only` 关闭所有其他窗口而仅保留当前窗口.

如果你的光标处是一个 url, 那么 `gx` 将会在默认浏览器中打开该 url.

`:h index`, 查看所有模式下的默认键位. 更细致地, `:h insert-index` 可以查看插入模式 (insert mode) 下的默认键位, `:h objects` 查看文本对象的介绍等. 

![index](http://upload-images.jianshu.io/upload_images/127313-7cd6de7abdf7e51b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
