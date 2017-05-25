# iTerm2实用特性 Handy Features [TODO: 待起名]

为什么要使用命令行？为什么要使用 iTerm2 作为命令行？它提升了什么效率？如何衡量这个提升？

相比与 GUI + 鼠标点击，命令行是与计算机或应用交互更高效的手段。要让计算机完成一个任务，我们需要做的事情是：

* 通过某种方式「告诉」计算机执行特定指令 - 交互时间
* 计算机执行指令 - 执行时间
* 执行完毕，给出反馈 - 反馈时间

我们可以得出下列公式：

```
任务完成时间 = 交互时间 + 执行时间 + 反馈时间
t(task complete) = t(interaction) + t(computation) + t(feedback cycle)
```

可以看到，执行时间与反馈时间属于被调用程序（bash 程序、npm 模块等）本身的问题，优化应该发生在应用端；使用命令行，其实是优化了交互时间这个部分。它是如何减少交互时间的呢？以在 Mac OS 系统下进行「连接 vpn」这个任务为例，假定不需要任何键入用户名密码的操作，在 GUI 和命令行下的操作步骤分别为：

### GUI 交互

1. 通过 Mac 的触发角或 `F11` 功能键，回到桌面或 dashboard
2. 通过人眼或习惯找到 VPN 这个软件
3. 将鼠标移动到这个软件图标上，停止
4. 双击软件，弹出主界面
5. 点击「连接 VPN」
6. 等待连接成功，任务完成

### 命令行交互

1. 通过 iTerm2 的 hotkey Window，一键呼出 hotkey window
2. 键入 `vpn` 三个字母，按回车键确认
3. 等待连接成功，任务完成

可以看到，在 GUI 交互方式下，为了完成你需要的任务本身，你必须先定位到程序所在，并因此被迫进行大量无关的操作，比如打开桌面、移动鼠标、寻找软件、双击再双击等。其中操作效率主要受「寻找软件」和软件本身的交互方式所影响，打开桌面、移动鼠标都可以变成下意识的行为，不需要占用大脑的资源和精力，但「寻找软件」不行，你的大脑必须通过眼睛来搜索、匹配那个尺寸不过100  x 100的图标，并且还需要控制鼠标移动到特定的位置，这一切都是需要占用大脑资源的。这里为了简化探讨，我还略去了通过 GUI 输入密码的过程，这个过程又需要你的大脑或习惯或等待软件的响应方式，以做下一步决定，每一个过程，都蕴含了一些假设，都占用和浪费了大脑的资源。而命令行的方式，只要保证导航到命令行的时间最少，马上就可以进入「交互」的阶段，其节省了少量的操作时间，却节省了大脑无谓的精力消耗。

**一个命令行工具的衡量标准，就是它能在多短的时间内达到可用的交互状态**。其他的特性，无非是锦上添花而已。

这里的参考：[https://www.iterm2.com/features.html](https://www.iterm2.com/features.html)

iTerm这个终端具有比系统默认终端更强的能力，而term3则是最近刚发布的beta版本。它比起系统默认终端具备更加丰富且实用的功能，比如：

* 即时窗口(Hotkey Window)
* 窗口切分(Split Panes)
* 搜索，支持正则表达式 -> 没用
* 全键盘复制(Mouseless Copy) -> ?
* 自动补全(Auto Complete) -> ?
* 粘贴版历史记录(Paste History) -> ?
* 即时回放(Instant Replay) -> 接近没用
* 触发器(Triggers)(虽然还不知道是什么鬼)
* ...等


## 即时窗口 Hotkey Window

> iTerm2 offers a special terminal window that is always available with a single keystroke.

前面也提到了，**一个命令行工具的衡量标准，就是它能在多短的时间内达到可用的交互状态**。而 iTerm3 的即时窗口，就是对这个问题的需求的一个完美方案，这也是它之所以能成为最优秀的命令行工具的首要因素。对于**随手可达的命令行**这个需求，我探索过几种解决方案，列举分析如下：

1. Alfred 的 RunCommand 插件
2. iTerm 的非即时窗口

//todo: gif 

这两种方案各有其毛病。先说第一种，通过 Alfred 的插件作为接口，也可以完成即时输入的任务，它实质上是把你输入的命令作为参数传入给 shell，从而也避免了 GUI 的交互。不过，缺点在于每次它都会创建一个新的会话，都需要调用 shell 的初始化脚本（如初始化 `~/.bash_profile` / `~/.bashrc` 等），增加了多余的时间支出；第二种使用非即时窗口，不论是每次通过 Alfred 呼出一个新的 iTerm 命令行，还是每次切换到一个已打开的 iTerm 窗口上，都不是好的方案。前者依然有每次初始化 shell 的时间负担，后者则需要更多无关的操作成本，比如定位该已打开 iTerm 窗口、焦点对齐等。

因此，一个随手可达的命令行，必须不能是每次使用时才开始初始化的（有初始时间的负担），同时它必须被很容易地定位（从而对使用者没有定位、对焦等精力消耗）。前者要求命令行必须常驻后台，后者的一个解决方案就是通过快捷键。这两种功能结合的命令行，就是 iTerm 的即时窗口提供的，对**随手可达的命令行**这个需求的完美解决方案。

//todo: gif

![iTerms2-hotkey-window](./figures/iterm2-hotkey-window.png)



## 窗口切分 Split Panes

iterm2 支持把窗口进行横向纵向切分，自己可以调整占据的比例，并且不活跃的窗口（inactive panel）还会变暗以强调活跃的窗口，对于需要一个工作区间做多件事的需求是很有用的。

![iTerm2-panes-split](./figures/iterm2-panes-split.png)

* 纵向切分：`Command+D`
* 横向切分：`Shift+Command+D`
* 窗口切换：`Command+[` / `Command+]` / `Option+Command+Left` / `Option+Command+Right`




## 搜索与全键盘复制粘贴 Search and Mouseless Selection

这个功能其实我不太常用，就是可以在iterm2窗口中搜索内容，跟在编辑器中搜索一样，支持正则表达式搜索。此外，还支持选中当前搜索内容一键复制等，功能强大，就是没怎么用到。

![iTerm2-search-and-mouseless-selection](./figures/iterm2-search-and-mouseless-selection.png)

* 搜索：`Command+F`
* 复制选中内容：`Enter/Return`
* 拓展选择（反向拓展）：`tab/Shift+tab`


## 自动补全与粘贴板历史 Autocomplete and Paste History

只要是在终端输入过的词或者命令，iterm2就可以帮你提供自动补全的建议，快捷键是`Command+;`，调出后即可通过纯键盘输入来筛选，比较适合快速输入一些长命令，如下，其快捷键也比`Control+R`友好一点，可视化程度更高一些。在其他相似的场景下，这个功能有一些替代品，比如目录导航时使用autojump/z、搜索历史命令时使用`Control+R`、`history`等。

另外，iterm2也帮你保存了你粘贴过的命令，通过快捷键`Shift+Command+H`即可调出，但仅限于通过粘贴板的方式进入的命令。

![iTerm2-autocomplete](./figures/iterm2-autocomplete.png)

![iTerm2-paste-history](./figures/iterm2-paste-history.png)


## 即时回放 Instant Replay

逆天功能，可以回放过去任一__时刻__里iterm窗口的状态，在你需要之前窗口的一些信息时特别有用，可以回过去查看。虽然我不怎么用到这个功能，但你知道出事了随时都可以回去查看以前的信息。快捷键是`Option+Command+B`，每个session的即时回放缓存默认是4MB，可以在设置里面改。


## 智能选择 Smart Selection

iterm2能够只能识别邮件地址、URL、文件名、文件夹等名称，按住`Command`键点击即可去到相应的地方。比较handy，用处不小也不大。


## 系统配置

### 要打开的选项

* General -> Closing -> Confirm 'Quit iTerm2' command。`Command+Q`离`Command+W/1/2/3/Tab`如此之近，保不齐你什么时候手一滑按错所有窗口就都归西了
* Appearance -> Window -> Hide scrollbars。据经验基本没必要，没用的元素就不打开让它占据空间
* Profiles -> Text -> Cursor: Underline, Blinking cursor，光标指示符采用下划线并且加闪烁效果。个人喜好
* Profiles -> Text -> Font: 12pt Monaco，此字体甚好

### 要关闭的选项

* General -> Selection -> Copy to pasteboard on selection。选中即复制，这不烦人嘛
* General -> Window -> Adjust window when changing font size。比较建议关掉，虽然调整字体大小的时候不常见，但若窗口大小跟着变又得调窗口大小
* Appearance -> Tabs -> Show tab close buttons。有`Command+W`和`exit`就行了
* Keys -> Navigation Shortcuts -> To switch split panes，关掉
* Keys -> Navigation Shortcuts -> To switch windows，关掉


## 快捷键

除了上面提到的在一些场景下比较常用的快捷键，这里尽可能地要精简整个软件所使用的快捷键，其他不常用的能删都删了。

* `Shift+delete`，打开hotkey window，这里更改了默认的配置，因为空格的组合其他程序都在用，比如`Control+Space`是Intellij的上下文提示，`Command+Space`是Alfred/Spotlight的全局快捷键，`Option+Space`是系统默认的幻灯片播放，`Option+Command+Space`被我也因为前面快捷键被占的原因被我定制成输入法切换，`Shift+Space`是输入法的简繁体切换。太难记了，所以hotkey window的快捷键不这么用
* `Control+A/E`，系统默认的快捷键，师承vim系风格，分别是跳到行头/行尾的快捷键，在编辑的时候对效率有一定帮助
* `Command+Up/Down`，上一行/下一行
* `Control+U`，直接删掉一行