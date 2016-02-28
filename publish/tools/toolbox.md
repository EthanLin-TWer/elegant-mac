# 工具集 Toolbox

这部分工具来自[https://github.com/macdao/ocds-guide-to-setting-up-mac#1-os-x](https://github.com/macdao/ocds-guide-to-setting-up-mac#1-os-x)，我司员工总结。


## 包管理工具
* [brew](http://brew.sh/)。这里是[brew的Formulae仓库](http://braumeister.org/browse/a)，也可以通过运行命令`brew search`查看。一般用于下载一些开发工具（与bower/npm不同的是，这些是用于下载偏前端的开发工具）
* [brew-cask](http://caskroom.io/)。没找到brew cask的仓库，但可以通过运行命令`brew cask search`在终端查看所有工具，这个一般用来装应用软件，比如chrome，扣扣，iterm2等
* App Store。有些应用只有App Store的渠道可以安装。App Store没有命令行，还需要Apple ID，下载不方便，但更新起来比较方便


## 终端
* [iTerm3](https://www.iterm2.com/features.html)。这个终端具备比默认终端terminal更强悍的能力，具体的请见[iTerm3一节](./iterm3.md)
* [Oh My Zsh](http://ohmyz.sh/)。如果说有了终端，一切都有了命令行操作的可能，那么oh-my-zsh则是带领终端走入了彩色时代。它不仅提供了主题themes，还提供了一套插件和工具（比如全球通用的git别名表等），使许多终端的工作变得简单。[这里](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins-Overview)有许多有价值的插件。
* z/autojump。快速目录进入工具，应归属“终端/命令行使用”一类话题


## IAAS(基础设施即服务管理)神器
`brew install stow`，stow这个神器不仅可以帮你备份所有重要的dotfiles，还可以帮你进行版本管理，竟然还可以支持加密。简直满足了你搬运系统过程中需要备份配置文件的所有需求！具体的我还没用上，不过可以看[这篇文章](https://github.com/jcouyang/dotfiles)获得一些详细信息。


## 窗口管理工具
* [shiftit](https://github.com/fikovnik/ShiftIt)。支持基本的上下左右分屏等窗口管理，支持全屏，支持居中。除此以外，还支持sizeup需要插件才能做到的大小调整，大小调整的比例还是可配置的。支持margin调整，支持多显示器。目前首选
* [sizeup](https://www.irradiatedsoftware.com/sizeup/)。功能与shiftit基本相同，原生sizeup不支持大小（三分之一四分之一之类的）调整，必须装脚本；但sizeup支持在不同space(desktop)之间移动窗口，但反应速度较慢，目前需求不大
* [moom](https://manytricks.com/moom/)。据说功能强大


## 编辑器
* sublime2/3。现在在用的工具
* atom。传闻也很酷炫
* MacDown/Gitbook/Mou/CmdMarkdown...，markdown编辑器


## 全键盘操作
* Vimium(for chrome)/KeySnail(for firefox)
* [ShortCat](https://shortcatapp.com/)。还没用过，不过像这种工具肯定调用了系统的API来进行工作，可以拦截系统层级的输入，真的做到全系统键盘化


## Misc--杂七杂八的
* SourceTree，它是Atlassian公司出品的一款优秀的Git图形化客户端
* CheatSheet
* Alfred，它定义了强大的工作流workflows，并且有许多雷锋使用者提供现成的拓展，访问[这里](http://www.alfredworkflow.com/)查看更多
* Manico，一个快速切换app的支持器，支持使用键盘快速导航到指定的app，而且有贴心的左手操作模式，使用起来比alfred要更简明快速些，因为只做app导航这个垂直领域，而且只要25人民币买的话，害得我差点就手滑了。简单用了下，不能mute掉alfred（这个问题很大，因为alfred几乎是所有快速操作的入口）是个硬伤
* boom，音效调节软件。最直观的印象是我可以调低音增强，其他的有待发掘，也可以培养对银色的敏感啦啦啦啦啦
* bartender，可以收纳任务栏多余的图标，还可以调整它们的位置，比较有用，120人民币，不算贵
* popclip，传说中改变硬件不足带来的坏工作习惯的——连续粘贴软件！！！【搞错了，这货是支持鼠标复制粘贴的工具，对我这键盘流来说没啥卵用的感觉】


