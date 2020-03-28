# 备份体系 Storage and Synchronization

0. 为什么要备份
1. 备份什么
2. 如何快速取回
3. 恢复的次序
4. 自动化

为啥要备份，主要是为了防丢，其次是为了换电脑换系统的时候，不需要重新恢复系统，只需要重新安装一遍。借鉴基础设施即代码的理念，开发资产也是代码嘛。我希望的是，把系统所有使用到的软件、工具，都可以做成无状态的样子，只需要脚本就可以一键无痛安装到其他电脑上。为了达到这个目标，我列出了上面几个点，即我们需要用代码表达我们要备份的东西，确保它有快速、稳定、可靠的方式被快速取回，为此必须保持一定的恢复次序，比如 VPN、命令行、brew、系统假设 这些，可能是所需要的前置物品。

## 备份什么

需要这些信息：

* 它们各自的版本（重要工具才需要）
* 它们各自的依赖版本（重要工具才需要）
* 配置文件

一些工具性的文件需要再装好了。所以整理了一下，需要的只有下面这些：


## 恢复次序

* [x] system preferences
* [x] pre-requisites
  * [x] XCode dev-tools - in order to get `git` to work
  * [x] git - in order to get `brew` to work - but we'll replace it with brew installed ones later
  * [x] Java https://stackoverflow.com/a/52524114
  * [x] nvm https://github.com/creationix/nvm
    * [x] node dependencies
* [x] install brew & cask
  * [x] install: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"` 
    * 踩坑：[新来的Git要关闭sslVerify](https://confluence.atlassian.com/fishkb/unable-to-clone-git-repository-due-to-self-signed-certificate-376838977.html)
    * 踩坑：[不要开防火墙](https://stackoverflow.com/a/52787557)
    * 踩坑：[xcode-select --install](https://stackoverflow.com/a/33786214)
    * 踩坑：[如果还是不行，不要用https拉Homebrew代码]()
    * 连上手机热点终于成功了
  * [x] `brew update`: https://github.com/caskroom/homebrew-cask/blob/master/USAGE.md
  * [x] `brew cask` will install brew cask
  * [x] `brew tap buo/cask-upgrade`
  * [x] `brew tap homebrew/cask-versions` - 可以装一些有版本管理的包，比如Java
  * [x] 安装一下下面该装的软件
* [x] basic infrastructures
  * [x] install Brew apps: `brew install`  —— 新电脑配置好了可以到这边来更新
    ```bash
    adns			        jq			        openssl@1.1
    autojump		        kubernetes-cli	
    blueutil		        libassuan		    p11-kit
    brew-cask-completion	libffi			    pcre
    ccze			        libgcrypt		    pcre2
    clisp			        libgpg-error		pinentry
    			            libidn2 			pkg-config
    diff-so-fancy		    libksba		
    docker			        libsigsegv		    python@3.8
    emojify			        libtasn1		    readline
    			            libunistring		sphinx-doc
    gdbm			        libusb  			sqlite
    gettext     			libxmlsec1	    	thefuck
    ghi         			libzip			    tig
    git         			lua     			tldr
    git-lfs     			lzo		        	tokyo-cabinet
    git-quick-stats		    mas     			tree
    		                maven   			unrar
    gmp         			minikube    		watch
    gnupg               						watchman
    gnutls      			mysql   			wget
    gradle      			nettle			    xz
    groovy      			npth    			zsh
    highlight				zsh-completions
    hub         			oniguruma   		zsh-syntax-highlighting
    jenkins     			openssl
    ```
  * [x] cask apps —— 新电脑配置好了可以到这边来更新
    ```bash
    aerial                     java8                      
    alfred                     karabiner-elements         
    aliwangwang                keycastr                   shortcat
    baiducloud                 launchrocket               sizeup
    baidunetdisk               minikube                   sketch
    bartender                                             
    boom                       neteasemusic               slack
                               ngrok                      sogouinput
    charles                    obs                        sublime-text
    contexts                   paw                        
    dash                       pomotodo                   thunder
    docker                     provisionql                tickeys
    dropbox                    qlcolorcode                ticktick
    emacs                      qlimagesize                torbrowser
    evernote                   qlmarkdown                 typora
    fastlane                   qlprettypatch              vagrant
    flux                       qlstephen                  virtualbox
    gitbook                    qlvideo                    vlc
    gitbook-editor             qq                         vyprvpn
    go2shell                   quicklook-csv              webpquicklook
    google-chrome              quicklook-json             xmind
    google-chrome-canary       quicklookase               youku
    istat-menus                quicksilver                
    iterm2                     zoomus
    ```
  * [x] app store：它们都在 App Store 中存储着，只需要用一个同样的账号就可以了
    ```bash
    pages numbers smartkb keynote pocket amphetamine reeder3 hackrun deskcover xcode
    ```
  * [x] zsh(should be shipped with Mac OSX automatically) `zsh --version` to check 
  * [x] iterm configurations - see Ωff
  * [x] oh-my-zsh 
    * [x] `~/.zshrc`, `~/.oh-my-zsh` plugins and `ZSH_THEME_RANDOM_CANDIDATES`
    * [x] `~/.bashrc` & `~/.pathsrc`
    * [x] zsh plugins(mostly highlights and autocompletes)
    * [x] make `sudo` doesn't require a password: [https://apple.stackexchange.com/questions/239606/change-sudoers-to-stop-asking-for-password-when-running-a-systemsetup-comman]
  * [x] vpn
    * [x] openvpn
      * https://mail.google.com/mail/u/1/#search/vpn/15f19e206e08e205
      * https://github.com/Homebrew/homebrew-php/issues/4527
    * [x] vpn 
* [x] Setup folders: syncing / my / code
* [x] Setup dotfiles configurations: 
  * `~/.gitignore`, `~/.gitconfig`, `~/.gitignore_global`
  * `~/.pathsrc`, `~/.bashrc`, `~/.zshrc`
  * `~/.ssh`
* [x] 系统三件套
  * [x] Toolbox + WebStorm
  * [x] Chrome - can now all managed by an account
    * [x] bookmarks
    * [x] settings
    * [x] extensions
      * [x] configurations - should also be done manual, shitty
    * [x] shortcuts
  * [x] Sublime - 还是采用软件自身备份方式导出方式
  * [x] Alfred - 垃圾备份，最重要的配置不见了 - 还好我机智，瞬间又好了
  * [x] Dropbox 
  * [x] Sogou input
  * [x] Applications里所有软件的配置
  * [ ] Karabiner
* [x] 次重要：随开机启动
  * [x] Contexts: setup; license
  * [x] Flux 
  * [x] Boom: activate with license
  * [x] Dropbox: setup repos
  * [x] Bartender
  * [x] Pomodoro
  * [x] Ticktick
  * [x] Amphetamine
  * [x] iStats
  * [x] OctoMouse
  * [x] SogouInput
  * [x] Shortcat
  * [x] SizeUp
  * [x] Wechat
  * [x] SmartKB
  * [x] Dash
* [x] 三大备份系统设置
  * [x] Dropbox
  * [x] Google Drive
  * [x] BaiduYunDisk
  * [x] Megasync
* [x] other softwares
  * [x] Font Books - export collection
  * [x] what else...?

## 自动化

* 安装、版本
* 配置（设置项、快捷键）
* usually it requires a manual setup 

## System Preferences

> only changes required are listed

### general 

* automatically hide and show the menu bar
* ask to keep changes when closing documents - off
* default browser: chrome[depend on Chrome installation]
* recent items: 5 documents, apps and servers 

### desktop & screen saver

* [depend on install screen saver applications to install]
* screen saver - hot corners:
  * left bottom: start screen saver
  * right bottom: desktop
* screen saver - start after: never
* desktop - change picture: every 5 seconds
* desktop - random order

### Dock 

* adjust size to 75%
* **turn magnification on and set to max**
* **minimize windows into application icon - on**
* **automatically hide and show the dock** - on
* un-tick 'Show recent applications in Dock'
* **remove all applications from the dock manually**

### mission control

* **when switching to ... - no**
* **group windows by application - no**
* **displays have separate spaces - no**
* disable all 'keyboard and mouse shortcuts' except for 'show desktop - F11'

### language & region

* first day of week: monday
* time format: 24-hour time - yes
* advanced
  * dates: short: YYYY-MM-DD

### security & privacy

general: 

* **require password - immediately**
* show a message when the screen is locked - no
* disable automatic logic - yes

filevault: on or off

firewall: on with no changes

privacy:

* location services
  * enable location services - yes - changes required
  * only enable 'weather' and 'maps'
  * system services - details 
    * only enable 'Find My Mac'
    * clear 'Significant Locations - Details' 
* contacts: no applications allowed
* calendars: no applications allowed
* reminders: no applications allowed
* photos: no applications allowed
* accessibitity
  * Alfred 3
  * Alfred Text Service
  * Boom 2
  * Contexts
  * Dropbox
  * KeyCastr
  * OctoMouse
  * Shortcat
  * SizeUp
  * Switchem
  * System Preferences
  * Tickeys
* analytics: nothing ticked/allowed

### Spotlight

no changes

### Notifications

* turn on do not disturb: when the display is sleeping
* allow repeated calls - yes - changed
* change all alert style to none for all initial applications

### Displays

* show mirroring options in the menu bar when available - off - changed
* no changes for any other settings

### Energy saver

* show battery status in menu bar - off - replaced by iStats
* power adapter: 
  * turn display off: 2 hours
  * prevent computer from sleeping automatically when the display is off - on 
  * enable Power Nap while plugged into a power adapter

### Keyboard

keyboard

* key repeat: fastest
* delay until repeat: shortest
* adjust keyboard brightness in low light - 30 seconds
* use f1, f2, etc. keys as standard function keys - on
* **modifier keys - no change** - delegate all to Karabiner

text: no change at all

shortcuts: 

* **full keyboard access: all controls** - important
* (2019) Use keyboard navigation to move focus between controls
* launchpad & dock: all off
* mission control: 
  * show desktop: f11
  * mission control: move left a space: ^ <-
  * mission control: move right a space: ^ ->
  * mission control: switch to desktop 1: ^1
* keyboard: all off except 'move focus to next window: command + `'
* input sources: all off except 'select the previous input source: option + space' 
* screen shots: 
  * screenshots: 'shift + command + ' 1/2/3/4 order 
  * others: off
* services: all off
* spotlight: all off when setup's done
* accessibility: all off
* app shortcuts
  * All Applications
    * Show Help Menu: command + h
    * Minimize: shift + control + option + command + a
    * Emoji & Symbols: shift + control + option + command + space
  * Google Chrome
    * Email Page Location: shift + control + option + command + i

input sources

* show input menu in menu bar - on

dictation: no changes

### mouse 

* scroll direction: natural
* tracking speed: 8 / 10
* double click speed: 8 / 10
* scrolling speed: 6 / 8
* primary mouse button: left

### trackpad

point & click 

* Look up & data detectors: tap with three fingers 
* Secondary click: click or tap with two fingers
* **Tap to click: on** 
* Click: medium
* Tracking speed: 8
* Force Click and haptic feedback: on 

scroll & zoom

* scroll direction: natural - no change
* zoom in or out: pinch with two fingers - no change
* smart zoom: off
* rotate: rotate with two fingers - no change

more gestures

* swipe between pages - two fingers - no change
* swipe between full-screen apps: swipe left or right with **four** fingers - changed
* notification center: swipe left from the right edge with two fingers - on - no change
* mission control: swipe up with **four** fingers - changed
* app expose: off
* launchpad: off
* show desktop: off

### sound 

no changes

### icloud

don't use

### internet accounts

don't use

### Software Update

* automatically check for updates - yes
* download newly available updates in the bg - yes
* install macos updates - no
* install app updates - yes
* install system data files and security updates
* purchases and in-app purchases: always require

### networks

no changes

### bluetooth

no changes

### extensions

* all: enable: backup & sync from google, dropbox, ticktick - today
* actions: markup
* finder: dropbox finder integration, backup and sync from google
* photos editing: markup
* share menu: enable only notes, reminders, simulator
* today: enable only weather, itunes, ticktick, reminders

### sharing

* enable screen sharing on the left hand side

### users & groups 

you should have only one 'current user'.

login items:

* contexts
* iterm
* octomouse
* bartender 3
* sizeup
* Google Chrome
* baidu yun disk
* Ticktick
* dropbox
* Alfred 4
* Pomotodo
* backup and sync from google
* shortcat
* Karabiner-Elements 
* flux

### parental controls 

no changes

### siri

disable ask siri

### date & time

* clock - show date and time in menu bar - off

### accessibility

* general: all on with no changes
* voiceover: disable by default, no changes
* zoom: no changes required
* display: 
  * reduce transparency - yes
  * cursor size: 5 / 6 
* speech: no changes required
* descriptions: no changes required
* captions: larger text 
* audio: no changes required
* dictation: no changes required
* siri: no changes required
* keyboard: no changes required
* mouse & trackpad / Pointer Control
  * mouse options: scrolling speed: 6 / 8
  * **trackpad options: Enable dragging three fingers drag**
  * trackpad options: Scrolling speed: 7 / 8
* switch control: no changes required

## Brew installations

## iTerm configuration

general 

* Closing - Quit when all windows are closed
* Selection - de-select 'Copy to pasteboard on selection'
* Window - de-select 'Adjust window when changing font size'

tabs

* Tabs - de-select 'Show tab close buttons'
* Window & Tab Titles - 'Show profile name'
* Window - 'Hide scrollbars'

profiles

* general profiles: 
	* General - Basics - Name: 'Linesh TWer'
	* General - Working Directory: 'Reuse previous session's directory'
	* Colors - Cursor colors - select 'Smart Cursor color'
	* Text - Cursor - underline + blinking cursor
	* Text - Font - 24pt Monaco
	* Text - Font - Use a different font for non-ASCII text
	* Text - Non-ASCII Font - 24pt Monaco
	* Window - Window Appearance - Transparency - 18%
	* Window - Window Appearance - select 'Blur'
	* Window - Background Image - Blending: 20%
	* Terminal - Scrollback Buffer - select 'Unlimited scrollback'
	* Keys - Key Mappings - Left option Key: Esc+
	* Keys - Key Mappings - Right option Key: Esc+
* hotkey profiles
    * basically with all same configurations except: 
    * Window - Window Appearance - Transparency - 30%
    * Window - Settings for New Windows - Style - Fullscreen
    * Window - Settings for New Windows - Space - All Spaces    
    * Keys - Hotkey Window - select 'A hotkey opens a dedicated window with this profile'
        * Hotkey: '^;'
        * de-select 'Animate showing and hiding'
        * select 'Floating Window' - awesome

keys

* Navigation Shortcuts: To switch windows: none

pointer

* de-select 'option-click moves cursor'
* de-select 'triple-click selects entire wrapped lines'

advanced

* Hotkey - Duration in seconds of the hotkey window animation: 0 

## contexts 

welcome

* update to beta versions

appearance

* theme - vibrant dark
* increase contrast
* text size - largest

general 

* when switching to an app, perform Dock icon action
* when using multiple displays, use switching workaround
* de-select 'show app icon badges'

rules

* number of groups: 5
* apps to not show: 
  * cisco any connect security
  * deskcover
  * finder
  * gotometting v8.18.0
  * neteasemusic
  * otp manager
  * photos
  * pomotodo
  * react native debugger
  * terminal
  * vyprvpn
  * wechat
  * iterm2

sidebar

* show sidebar on: no display
* when cursor not over: hide
* when cursor over: narrowest

panel 

* panel width: 7
* de-select 'moving the cursor over Panel changes the selected item'
* de-select 'scrolling when Panel is visible changes the selected item'

search 

* search with 'command + control + return'
* de-select 'fast search with: fn-<characters>'

command-tab

* on command-tab: 
  * de-select 'move up list with command + backtick'
  * typing characters starts Fast Search when Panel is visible

number switcher

* Show numbers on sidebar

gestures

* show selection on: sidebar
