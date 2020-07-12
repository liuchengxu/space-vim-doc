---
title: "文本对象（2）"
weight: 20
---

接 [Vim 文本对象 (1)](http://www.jianshu.com/p/8915a2eb6ff8), 关于插件使用, 可以查看完整配置 [space-vim](https://github.com/liuchengxu/space-vim).

---------

## 编程语言的文本对象

Vim 基于常见编程语言结构提供了几个常见的文本对象. 其实都是**一对儿**符号，主要可以分为:

- 成对的标点符号，比如单引号，双引号，反引号。
- 成对的括号，比如小括号，中括号，大括号。
- 标记语言标签，它们也是成对的，比如 HTML 的标签，`<div></div>`。

模式为 `操作 + a/i + 符号`，这样操作的就是文本对象。不加 a 或者 i 的话就不是一个对文本对象的操作了。对文本对象进行操作时，Vim 不会考虑你的光标位置。而非文本对象操作时，会从当前光标处开始生效。

举个例子， `ci"` 指的是 `change inner "`, 改变 `""`所包含的内容，也就是删除 `""` 里面的内容并进入插入模式。

使用 a (around) 时，操作的范围包括标点符号，括号，标签本身。使用 i (inner) 时，不包括符号，括号，标签等。动手试一下，很快就能学会了。

### 字符串 (string)

- a” – a double quoted string
- i” – inner double quoted string
- a’ – a single quoted string
- i’ – inner single quoted string
- a` – a back quoted string
- i` – inner back quoted string

```
puts 'Hello "world"'
```

`ci"`

```
puts 'Hello ""'
```

### 圆括号

对于各种括号, 操作时使用前括号或后括号都可以, 比如 `da(` 等同于 `da)`.

- a) – a parenthesized block
- i) – inner parenthesized block

```
Project.all(:conditions => { :published => true })
```

`da)`

```
Project.all
```

### 方括号

- a] – a bracketed block
- i] – inner bracketed block

```
(defn sum [x y]
  (+ x y))
```

`di]`

```
(defn sum []
  (+ x y))
```

### 大括号

- a} – a brace block
- i} – inner brace block

```
puts "Name: #{user.name}"
```

`ci}`

```
puts "Name: #{}"
```

这些文本对象同样可以通过 `aB` 和 `iB` 来操作, 但是并不如使用 `a}` 和 `i}` 来的直观.

`%` 同样适用于 {}. 但是也有着 () 和 [] 一样的限制性.

### 标记语言标签

标记语言标签分为两类: t 和 >, t 所操作的是标签内包含的内容, 比如 `<p>content</p>`，`<p>` 与 `</p>` 之间包含的内容就是 t 来操作. `<` 或 `>` 的内容指的是 `<p>` 里面的 p. 具体可以看下面的例子。

- at – a tag block
- it – inner tag block

```
<h2>Sample Title</h2>
```

`cit`

```
<h2></h2>
```
因为操作后光标并不在 `<h2>` 里面, 所以 `cit` 替换标记里面的内容是非常方便的.

- a> – a single tag
- i> – inner single tag

```
<div id="content"></div>
```

`di>`

```
<></div>
```

这个文本对象也可以被用来快速操作单个标记及其属性.

参考:
[1] [Vim Text Objects: The Definitive Guide](http://blog.carbonfive.com/2011/10/17/vim-text-objects-the-definitive-guide/)
