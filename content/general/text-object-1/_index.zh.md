---
title: "文本对象（1）"
weight: 20
---


本文还是介绍一些基本内容, 关于插件使用, 可以查看完整配置 [space-vim](https://github.com/liuchengxu/space-vim).

---------

如果想要在 Vim 里拥有高效编辑的能力, 必然要掌握超过单个字符编辑的能力, 不然就可能出现像之前看到过的一个笑话 :

> 在你刚开始使用 Vim 的时候做过什么令你 “难忘” 的事情? 答: 使用
 j 跳转到 5000 行 :).

也就是说, 要掌握词 (word), 句子 (sentense), 段落 (paragraph)  级别的编辑能力. 在 Vim 里, 这样的概念叫做 **文本对象 (text objects)** . 详见 Vim 的 help  `:h text-objects`. 另外, 这些概念对于只是对英文表现比较好, 因为英文可以按照空格划分词, 但是中文并不可以.

本文的内容实际很多来自 Vim 的 help. 如果开始知道不懂的时候去查看 Vim 的 help, 基本上也就真正知道如何学习 Vim 了.

对于普通文本文件和常见程序语言结构, Vim 都提供了文本对象. 你可以通过 Vim script 定义新的文本对象.

## 一个编辑命令的结构

在 Vim 中, 编辑命令 (editing commands) 有着如下的结构:

```viml
<number> <operator> <text object or motion>

<数字> <操作符> <文本对象或移动命令>
```

**number:** 数字用于在文本对象或移动操作上进行多次执行, 比如说, 向后 3 个单词, 向前 2 个段落. 数字是可选的, 可以出现命令(command) 的前面，也可以放在命令的后面.

>If the motion includes a count and the operator also had a count before it, the two counts are multiplied.  For example: "2d3w" deletes six words.

如果是 motion 和下面所提到的 operator 都有数字修饰, 那么效果是两个数字相乘. 比如, `2d3w` 是删除 6 个单词.

**operator:** 操作符, 比如, change, delete (删除), yank (复制). 操作符也是可选的. 但是如果没有操作符的话, 那么就只剩一个移动命令, 而非一个编辑命令了.

见 `:h operator`, Vim 默认提供的 operator 有:

![operator](http://upload-images.jianshu.io/upload_images/127313-f73fb0d05fb0964d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**text object** 或者 **motion** 可以是一个文本对象, 比如, 一个单词, 一个句子, 一个段落, 或者是一个移动, 比如, 向下移动一行, 向后翻一页, 到一行末尾.

`:h text-objects` :
![text-objects](http://upload-images.jianshu.io/upload_images/127313-fd348538221b6d5c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`:h motion` :
![motion](http://upload-images.jianshu.io/upload_images/127313-093f9b2636700dba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

一个**编辑命令(editing command)** 等于一个操作符加上一个文本对象或者移动, 比如, 删除一个单词, 改变一个句子, 复制一个段落.

>`an editing command` = `an operator` + `a text object/motion`

## 普通文本对象

Vim 为普通文本文件提供了三种类型的文本对象: 词(word), 句子(sentence), 段落(paragraph).

### 词

- aw - a word (包含在周围的空格)
- iw - inner word (**不**包括周围的空格)

```
Lorem ipsum dolor sit amet...
```

`daw`

```
Lorem dolor sit amet...
```
以 `a` 开头的文本对象包含周围的空格, 以 `i` 开头的文本对象不包含. 这个原则对所有的文本对象都适用.

`w` 看起来与 `aw` 效果差不多. 区别在于光标位置. 比如, 如果用 `dw` 来删除一个词, 光标必须在词的开头. 如果在除了开头的其他位置使用 `dw`, 只能删除部分单词. 但是, `daw` 允许光标在一个词的任何位置删除整个单词.

![w & aw](http://upload-images.jianshu.io/upload_images/127313-b5fa27011f4ddd1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果你已经懂得了 word 的 w 与 aw 的区别, 下面句子与段落就已经掌握了, 道理是一样的, 只是将 w 换成了 s 与 p.

### 句子

- as -- a sentence
- is -- inner sentence

```
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
```
`cis`
```
 Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
nisi ut aliquip ex ea commodo consequat.
```
注意, "inner" 文本对象**不包含**尾部的空格.

### 段落

- ap -- a paragraph
- ip -- inner paragraph

```
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.
```

`dap`

```
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.
```

## 移动命令 vs. 文本对象命令

- 一个使用移动的命令, 比如, `cw`, 是从光标处开始生效.
- 一个使用文本对象的命令, 比如, `ciw`, 如果光标在何处, Vim 都将在整个文本对象上生效.

是一个移动命令还是一个文本对象命令, 区别在于是否有 a (around) 或者 i (inner) 这样的限制. 对于每个类型的文本对象都是如此. 尽管使用文本对象的方式需要多输入一个字符, 但是这可以节省你的时间将光标移动到 "正确" 的位置.

参考:
[1]  [Vim Text Objects: The Definitive Guide](http://blog.carbonfive.com/2011/10/17/vim-text-objects-the-definitive-guide/)

