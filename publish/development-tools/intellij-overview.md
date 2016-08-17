# 史上最贵的IDE——Intellij IDEA特性概览

> 本章总结并未完成。

* 为什么用IDEA？为什么用IDE？为什么不用其他的IDE？

码代码并非简单的文本编辑，作为代码的文本具有更高层级的原子操作，IDE在这个方面能带来的贴心与质感自无需赘言。打个比方，如果你编辑的是一串文本，那么简单的全选、复制、粘贴、替换、去到行头行尾等功能应该能够满足大部分的需求了，而编程所操作的文本是基于某种语言的代码，这些代码呈现的是具备语言特性的结构，比如类、对象、继承、字段、方法等，而远非普通的字符串。再者，IDEA对语言世界中的其他语素也提供了原生的支持，比如重构、后向声明、根据类型自动补全（“类型”，就是一个在特定语言中才存在的特性，普通的文本字串不会存在类型这个概念）等。如下面一段打印小票的代码，我们想要把它重构成为更可读的样子：

```java
public void printReceipt(List<Product> purchasings) {
    System.out.println("*******************************");

    double total = purchasings.stream().reduce(0, (pur, chasing) -> {
        return pur.getPrice() + chasing.getPrice();
    });
    System.out.println("total: " + total);

    System.out.println("-------------------------------");
}
```

我们想要把它重构成这样更易读的样子：

```java
public void printReceipt(List<Product> purchasings) {
    printBanner();
    printTotalAmount(purchasings);
    printFooter();
}

public void printBanner() {
    System.out.println("*******************************");
}

public void printFooter() {
    System.out.println("-------------------------------");
}

public void printTotalAmount(List<Product> purchasings) {
    double total = purchasings.stream().reduce(0, (pur, chasing) -> {
        return pur.getPrice() + chasing.getPrice();
    });

    System.out.println("total: " + total);
}
```

下面是我们要完成这个重构所需要的操作，分别是将文本当成纯字符串及具有语言结构的代码来完成的步骤：

| 作为字符串的代码 | 作为代码的代码 |
| :--- | :--- |
| 1. 选中banner一行，移到行头，全选该行 | 1. 使用鼠标或键盘将光标定位到banner一行 |
| 2. 剪切该行 | 2. 使用重构快捷键：Command+Alt+M，输入新重构的方法名`printBanner`，回车确认 |
| 3. 使用鼠标或键盘将光标移动到方法末尾，换行 | |
| 4. 打字：`public void printBanner() {}` 以创建新的方法 | |
| 5. 将光标移动到中括号{}中间，粘贴刚刚剪切的一行代码 | |
| 6. 回到老代码所在位置，打字：`printBanner();` 以调用重构的新方法 | |
| 7~12. 重复1-6的步骤，重构`printFooter`方法 | 3~4. 重复1~2的步骤，重构`pringFooter`方法 |
| 13~18. 重复1-6的步骤，重构`printTotalAmount`方法 | 5~6. 重复1~2的步骤，重构`printTotalAmount`方法 |
| 19. 使用鼠标或键盘定位光标到`double total = ...`一行 | |
| 20. 移到行头，全选、剪切该行 ||
| 21. 使用鼠标或键盘定位光标到重构的`printTotalAmount`方法起始处 ||
| 22. 粘贴刚剪切的代码，换行，完成重构| |

可以看到，除了在操作步骤上节省了大量时间和精神之外，IDE提供的快捷键能让你更专注“重构”这个具有编程含义的工作本身，而无需关注底层细节。它使得更高mind-set的“重构”操作就像低层面的复制粘贴一样简单、花费微小。
