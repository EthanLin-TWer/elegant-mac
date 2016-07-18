# 快捷键Cheatsheet：成吨提高Java编程开发效率

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

## 本cheatsheet如何通用？

像这种cheatsheet的记录，有可能会随时间或版本变迁而不再通用，过多的定制也可能使得追踪和维护成本增加。为了尽可能多地减少维护成本，尽可能长地保持这份cheatsheet的通用，下列快捷键的选取遵循以下几个原则：

* 仅列出Mac版的快捷键
* 统一采用Mac OSX 10.5+版本的keymap作为基准
* 原则上对作为基准的Mac OSX 10.5+ keymap只删不改，即对不需要的快捷键可以删除，但对于已默认启用的快捷键不更改
* 少部分确实需要更改的快捷键，我会采用*星号标明，并标明原因

## 常用快捷键

本章主要分几个部分来总结：生产力大杀器、编辑、导航、重构、搜索、运行时六个部分。中间一栏是该操作在IDEA中的操作名称，可以在keymap中搜索到。

### 生产力（Productivity）

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 模板插入 | ⌘+J | 插入一个符合某结构特征的模板，详解见下 | Insert live template |
| 命令查询 | ⇧+⌘+S | 以名称的形式查询某个操作或快捷键，是声明式编程思想的践行者 | Find actions |
| 意图预测与智能帮助 | ⌥+Enter | 简单重构、移除死代码、结构调整、自动导包等| Show intention actions |

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

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 基本代码补全 | ^+Space | 一般都用这个补全，变量命名时及方法补全时常用 | Code/Completion/Basic |
| 智能补全 | ^+⇧+Space | 是否有必要记得两个快捷键？可以统一设成一个 | Code/Completion/SmartType |
| 语句补全 | ⇧+⌘+Enter | 直接补全当前语句，在括号特别多时非常有用 | Complete Current Statement |
|||||
| 从上方开始一行 | ⌥+⌘+Enter | | Start New Line Before Current |
| 从下方开始一行 | ⇧+Enter | | Start New Line |
| 上移/下移一行 | ⇧+⌥+↑/↓ | 上下移一行。一般用于以单行出现的元素，否则会破坏元素间的关系 | Move Line Up/Down |
| 上移/下移一个块 | ⇧+⌘+↑/↓ | | Move Statement Up/Down |
| 选中一个代码块 | ⌥+↑ | 常用 | Extend Selection |
| 取消代码块选中 | ⌥+↓ | | Shrink Selection |
|||||
| 重复当前行 | ⌘+D | | Duplicate Current Line or Block |
| 复制并且不删除当前行 | ⌘+C | | Edit/Copy |
| 剪切当前行并复制到粘贴板 | ⌘+X | | Edit/Cut |
| 关闭当前标签 | ⌘+W | 跟通常编辑器快捷键一致 | Edit Tabs/Close |
| 注释当前行 | ⌘+/ | 随手一注释 | Comment with Line Comment |
|||||
| 优化import | ^+⌥+O | 没啥用 | Optimize Imports |
| 格式化代码 | ⌥+⌘+L | 没啥用 | Reformat Code |

### 语言要素生成

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 测试、方法生成 | ^+Enter/ ⌘+N | 非常常用于创建测试方法、构造方法、覆写接口方法、覆写基类方法 | Code/Generate |
| 创建类、文件、目录 | ⌘+N | 常用 | Code/Generate |
| 创建override方法 | ^+O | 有用 | Override Methods |
| 创建接口方法实现 | ^+I | 有用 | Implement Methods |

### 导航（Navigation）

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 转到方法/字段的声明 | ⌘+B | 调试跟代码都很常用 | Navigation/Declaration |
| 转到方法/字段的实现点 | Navigation/Implementation(s) | ⌥+⌘+B | 同上，常用 |
| 转到方法/字段类型的类定义处 | ⇧+⌘+B/ ⇧+^+B | 常由下两个快捷键取代 | Navigation/Type Declaration |
| 当前类与单元测试间跳转 | ⇧+⌘+T | 非常方便 | Navigate/Test |
|||||
| 跳转到当前类的基类 | ⌘+U | 配套食用，效果更佳 | Super Method |
| 类继承体系 | ^+H | | Type Hierarchy |
| 方法继承层次 | ⇧+⌘+H | | Method Hierarchy |
| 当前方法调用链 | ^+⌥+H || Call Hierarchy |
| 本类及所有基类方法列表 | ⌘+F12 || File Structure |
|||||
| 类/方法/字段定义的快速预览 | ⌥+Space/ ⌘+Y | 小览实现，一般可以看到方法/字段参数、返回值、前几行实现，快速的信息足够了 | Quick Definition |
| 方法文档快速预览 | ^+J | 看文档，我不常用 | Quick Documentation |
| 方法参数快速预览 | ⌘+P | 常用 | Parameter Info |
|||||
| 前一个标签 | ⇧+⌘+[ | 导航常用，不过是否能以其他方式取代，比如声明式使用类查找⌘+O等。仍在探索 | Select Previous Tab |
| 后一个标签 | ⇧+⌘+] | | Select Next Tab |
| 往上一级 | ⌥+⌘+←/ ⌘+[ | 调代码，跟方法体系时，非常有用，下同 | Navigate/Back |
| 往下一级 | ⌥+⌘+→/ ⌘+] | | Navigate/Forward |
|||||
| 转到下一个错误或警告 | F2 | 代码见红时，常用此快捷键快速定位，并配合万能快捷键⌥+Enter快速修复 | Next Highlighted Error |
| 提示错误信息 | ⌘+F1 | 不常用 | Error Description |
| 意图预测与智能帮助 | ⌥+Enter | 简单重构、移除死代码、结构调整、自动导包等| Show intention actions |
|||||
| project视图 | ⌘+1 | 有时导航项目结构时常用，不知是否有替代方案 | Other/Project |
| search/find视图 | ⌘+3 | 除了这几个，其他视图都不常用 | Other/Find |
| run视图 | ⌘+4 | 有时开关测试视图 | Other/Run |
| debug视图 | ⌘+5 | | Other/Debug |
| VCS视图 | ⌘+9 | | Other/VCS |
| terminal视图 | * ⌘+0 | 自己改过，一是和各种视图快捷键保持一致，另外是原生的⌘+F12实在有点难按 | Other/Terminal |
| 隐藏所有工具视图 | ⇧+⌘+F12 | 同时开了工程和终端视图时一键回编程页面 | Hide All Tool Windows |
|||||
| 跳转到第...行 | Navigate/Line... | ⌘+L | 属于细节型的活，能少用就多思考替代方案 |


### 重构（Refactor）

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 复制类/目录等 | F5 | | Refactor/Copy |
| 移动类/目录等 | F6 | | Refactor/Move |
| 元素(类/方法/变量/…)重命名 | ⇧+F6 | 最常用的重构快捷键之一了吧 | Refactor/Rename |
| 类/方法签名修改 | ⌘+F6 | | Refactor/Change Signature |
|||||
| 字段(类级别)抽取 | ⌥+⌘+F | | Extract/Field |
| 常量(类级别)抽取 | ⌥+⌘+C | | Extract/Constant |
| 变量(方法级别)抽取 | ⌥+⌘+V | | Extract/Variable |
| 参数(方法级别)抽取 | ⌥+⌘+P | | Extract/Parameter |
| 方法抽取 | ⌥+⌘+M | 最常用的重构快捷键之一 | Extract/Method |
| 方法内联 | ⌥+⌘+N | | Refactor/Inline |


### 搜索（Searching)

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 搜索 | ⌘+F | 通常快捷键 | Find/Find |
| 替换 | ⌘+R | 正则发挥作用的地方 | Find/Replace |
| 查找引用点 | ⌥+F7 | 重构或调试的时候经常用到，使用频率高 | Find/Find usages |
|||||
| 查找类 | ⌘+O | 声明式编程，使用频率很高的快捷键 | Navigate/Class |
| 查找文件 | ⇧+⌘+O | 同上，使用频率很高 | Navigate/File |
| 查找symbol | ⌥+⌘+O | 基本不用，不知道与上两者有什么区别 | Navigate/Symbol |
| 全项目文本搜索 | ⇧+⌘+F | 搜索引用点和文本出现、改bug时非常有用 | Find/Find in path |
|||||
| 查找下一个 | ⌘+G | | Find/Find Next |
| 查找上一个 | ⇧+⌘+G | | Find/Find Previous |

### 运行时（Runtime）

| Operation | Mac OSX 10.5+ | Comments | Description |
| :---      | :---        | :---          | :---     |
| 编译 | ⌘+F9 | 调bug时可能是忘了编译最新代码 | Make Project |
| 运行(最近一个测试) | ^+R | 非常有用，有时可能节省在测试代码和源文件之间的切换 | Run/Run |
| 调试 | ^+D | | Run/Debug |
|||||
| 打断点/取消断点 | ⌘+F8 | | Toggle Breakpoints |
| 查看所有断点 | ⇧+⌘+F8 | | View Breakpoints |
| 跳入 | F7 | | Run/Step Into |
| 跳出 | ⇧+F8 | | Run/Step Out |
| 智能跳入(当前行多个调用时) | ⇧+F7 |
| 跳过(下一步) | F8 | | Run/Step Over |
| 求表达式值 | ⌥+F8 | | Evaluate Expression |
| 停止调试 | ⌘+F2 | | Run/Stop |
