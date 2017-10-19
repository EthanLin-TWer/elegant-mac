# 备份体系 Storage and Synchronization

0. 为什么要备份
1. 备份什么
2. 如何快速取回
3. 恢复的次序
4. 自动化

为啥要备份，主要是为了防丢，其次是为了换电脑换系统的时候，不需要重新恢复系统，只需要重新安装一遍。借鉴基础设施即代码的理念，开发资产也是代码嘛。我希望的是，把系统所有使用到的软件、工具，都可以做成无状态的样子，只需要脚本就可以一键无痛安装到其他电脑上。为了达到这个目标，我列出了上面几个点，即我们需要用代码表达我们要备份的东西，确保它有快速、稳定、可靠的方式被快速取回，为此必须保持一定的恢复次序，比如 VPN、命令行、brew、系统假设 这些，可能是所需要的前置物品。

## 备份什么

* 浏览器所有东西
  * 插件及其使用习惯、配置等
* 通过 brew 安装的软件
* 通过 cask 安装的软件
* 通过 APP Store 安装的软件
* 手动安装的软件
* 前置软件
  * iTerm + zsh 
  * brew + cask

### Brew 

```bash
ant		docker		git-quick-stats	isl011		libmpc08	mpfr2		repo		xz
aria2		emojify		gmp4		isl@0.11	libmpc@0.8	mpfr@2		ruby-build	yarn
autoconf	fortune		gmp@4		jansson		libpng		oniguruma	sbcl		youtube-dl
autojump	freealut	go		jenkins		libsigsegv	openssl		sqlite		zsh-completions
automake	freetype	gradle		jenv		libtiff		openvpn		stow
awscli		gcc48		groovy		jpeg		libtool		pcre		tig
bazel		gcc@4.8		gtm		jq		libxml2		pinentry	tldr
clisp		gdbm		httpie		jshon		libzip		pkg-config	tomcat
cloog		ghi		httpstat	lastpass-cli	lzo		python3		tree
cloog018	git		hub		libassuan	makedepend	rbenv		watchman
coreutils	git-flow	imagemagick	libgpg-error	maven		readline	wget
```

### Cask 

```bash
aerial                            frappe                            macdown                           skype
airmail-beta                      freshback                         macvim                            slack
android-studio                    genymotion                        manico                            sogouinput
anki                              gitbook                           microsoft-remote-desktop-beta     sourcetree
bartender                         gitbook-editor                    mindnode-pro                      sublime-text
bettertouchtool                   go2shell                          neteasemusic                      tickeys
boom                              google-chrome-canary              ngrok                             toggldesktop
calibre                           google-hangouts                   paw                               torbrowser
cmdtap                            gpgtools                          pomotodo                          typora
contexts                          intellij-idea                     popclip                           vagrant
dayone-cli                        istat-menus                       qingg                             virtualbox
dropbox                           istat-menus5                      qq                                vyprvpn
emacs                             jitouch                           quicksilver                       xmind
evernote                          keycastr                          react-native-debugger             youku
expo-xde                          lantern                           shortcat                          zeplin
flux                              launchrocket                      sizeup                            zoomus
```

### App Store 

```bash
OTP
GIPHY
Irvue
Outline Edit
Xcode 
Marboo List
Slack 
Wechat 
```

### 最最常用的软件

#### 自动启动

* Alfred 
* Dropbox
* Pomodoro
* Ticktick
* Amphetamine
* Bartender
* iStats
* OctoMouse
* SogouInput
* Shortcat
* BaiduYunDisk old version with auto-sync enabled
* SizeUp
* Google Drive
* SmartKB
* Flux 
* Boom

#### 开发三件套

* WebStorm 
* Chrome
* Sublime

#### 其他常用

* Wechat
* 


## 恢复次序



## 自动化


