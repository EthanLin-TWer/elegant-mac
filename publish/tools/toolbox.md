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
* [shiftit](https://github.com/fikovnik/ShiftIt)。快捷键冲突较小
* [moom](https://manytricks.com/moom/)。据说功能强大





