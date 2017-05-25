# 开发工具集 Development Toolbox

## 开发工具

* Java。Java可以通过brew cask来安装，通过tap version来管理版本：
```bash
   brew tap caskroom/versions
   brew cask install java7
```

其实原理也是通过环境变量`JAVA_HOME`来指向当前最新版本的方法来实现的：`JAVA_HOME=/Library/Java/JavaVirtualMachine/1.x.x.jdk/Contents/Home`。


## IDE

这个 Intellij/WebStorm 必须无敌了。Intellij的使用除了基础的效率增强外，还需要根据项目和语言的需要来学习不同的效率提高方法。具体可以参考我写过的关于intellij的一些总结。

* 自定义的 todolist & 自定义的 todolist filter。这样可以搜索只由自己添加上去的 todo