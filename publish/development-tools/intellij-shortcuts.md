# 快捷键：成吨提高Java编程开发效率

列这个快捷键一览表，我希望它是所有常用快捷键下的一个精华子集，是主观上使用频率最高的一组快捷键，而非任何形式的凑字数，否则直接查看[官方推荐的keymap](https://resources.jetbrains.com/assets/products/intellij-idea/IntelliJIDEA_ReferenceCard_mac.pdf)就好了。

一方面快捷键需要刻意练习以至生巧，另一方面也要快捷背后的理念。IDE与电脑作为工具，永远是高效完成特定工作的辅助，因此，在这个过程 **工作** 是 工具辅助的核心对象。如何更高效地专注于工作本身呢？围绕Intellij快捷键展开的工作系统与思维模式本身，实质性提高效率的理念是什么呢？

* 更高层次的抽象
* 声明式使用

## 更高层次的抽象

指的是从代码、从语言本身特性的层面思考编程，而非单纯的文本或者字符串。要把思维从“剪切复制去到这行去到那行”等把代码当成无意义字符的低层面活动，转变到以作为语言核心的要素和特性为单位的思考，比如类、变量、方法、重命名、重构、if-else、循环、可循环元素等。

在这方面，IDE提供的 **Live Template**、**重构**、部分后向声明等，都是这种思想的产物，即允许你从更高的层级来思考代码，进行编程。

## 声明式使用

声明式使用，指的是直接使用你需要用于完成工作的元素（类、字段、方法等），让IDE为你自动补全缺少的声明或结构。这种思想同样贯穿这本工具集的始终，以更语义化（更高阶）的操作来使用工具。

在这方面，IDE提供的 **后向声明(Postfix Auto Completion)**、**自动补全(Auto Completion)** 等，都是这种思想的产物。你不需要关注操作所在的上下文，IDE会为你补全，你需要关注的是工作和操作本身。

## 常用快捷键

本章主要分几个部分来总结：生产力大杀器、编辑、导航、重构、搜索、运行时六个部分。中间一栏是该操作在IDEA中的操作名称，可以在keymap中搜索到。

### 生产力（Productive）

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |
| 模板插入 | Insert live template | ⌘+J | 插入一个符合某结构特征的模板，详解见下 |
| 命令查询 | Find actions | ⇧+⌘+S | 以名称的形式查询某个操作或快捷键，是声明式编程思想的践行者 |
| 意图预测与智能帮助 | Show intention actions | ⌥+Enter | 简单重构、移除死代码、结构调整、自动导包等|

#### 模板补全
* `ifn`: `if (<template> == null)`
* `inn`: `if (<template> != null)`
* `fori`: `for (int <template> = 0; i < <template>; i++)`
* `foreach`: `for (<className> <objectname> : <fromList>)`一般不这么用，一般在一个具体的可迭代元素（比如数组、List、Map等）上使用后向声明完成补全

* `thr`: `throw new <exception>`
* `todo`: `// TODO: `
* `fixme`: `// Fixme: `

* `inst`: `if (<variable> instanceof <target_class>)`
* `sout`: `System.out.println(<template>)`

#### 后向声明
根据类型不同而不同。

* string.`null`: `if (string == null)`
* string.`notnull`: `if (string != null)`

这两种形式我更倾向于使用模板补全，因为模板专注于“结构”本身，而后向声明的关注点依然在某个 元素（String）的行为（空还是非空），更倾向于细节，与声明式使用理念不符。
* string.`try`
* string.`cast`
* string.`var`
* string.`return`
* string.`format`
* string.`field`: 直接转换为类的字段
* string.`sout`

* integer.`try`
* integer.`var`
* integer.`field`
* integer.`switch`
* integer.`cast`
* integer.`return`
* integer.`sout`
* integer.`fori`
* integer.`forr(everse)`

* boolean.`if`
* boolean.`else`
* boolean.`not`

* lists.`for`
* lists.`iter`
* lists.`fori` 需要索引或中途退出时使用


### 编辑（Editing）

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |
| 基本代码补全 | Code/Completion/Basic | ^+Space | 一般都用这个补全，变量命名时及方法补全时常用 |
| 智能补全 | Code/Completion/SmartType | ^+⇧+Space | 是否有必要记得两个快捷键？可以统一设成一个 |
|||||
| 上移/下移一行 | Move Line Up/Down | ⇧+⌥+Up/Down | 上下移一行。一般用于以单行出现的元素，否则会破坏元素间的关系 |
| 上移/下移一个块 | Move Statement Up/Down | ⇧+⌘+Up/Down | |
| 选中一个代码块 | Extend Selection | ⌥+Up | 常用 |
| 取消代码块选中 | Shrink Selection | ⌥+Down | |
|||||
| 优化import | Optimize Imports | ^+⌥+O | 没啥用 |
| 格式化代码 | Reformat Code | ⌥+⌘+L | 没啥用 |

### 语言要素生成

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |
| 测试、方法生成 | Code/Generate | ^+Enter/ ⌘+N | 非常常用于创建测试方法、构造方法、覆写接口方法、覆写基类方法 |

### 导航（Navigation）

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |
| 从上方开始一行 | Start New Line Before Current | ⌥+⌘+Enter | |
| 从下方开始一行 | Start New Line | ⇧+Enter | |

### 重构（Refactor）

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |

### 搜索（Searching)

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |

### 运行时（Runtime）

| Operation | Description | Mac OSX 10.5+ | Comments |
| :---      | :---        | :---          | :---     |

## TODOLIST

* [ ] 新建一个子域名：intellij.linesh.tw，用于将本页所列出的快捷键和思想以UI友好的方式展示、备查
* [ ] 寻找或自己造一个轮子，能将日常intellij操作的快捷键记录下来，分析频率，同样展示在主页
* [ ] 自动化以上两步：本文更新到展示主页的同步、以及每天频率的自动提交与更新
