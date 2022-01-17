# javac和java命令

## 引言

很多人写Java程序非常依赖IntelliJ IDEA、Eclipse等IDE，并使用这些IDE编译代码运行程序。如果离开了这些工具，只有Java提供的编译和运行命令，我们还能让我们的程序正确运行起来吗？

## Java程序从源代码到运行的过程概述

1. 开发者编辑.java文件（源代码文件）。

2. 将.java文件编译为.class文件（字节码文件）。

3. 启动JVM（Java Virtual Machine），让JVM运行.class文件。

## 本文实验用的目录结构与.java文件内容

- 目录结构
```
.
├── classes
└── java
    ├── Main.java
    └── lib
        └── Func.java
```

- Main.java
```java
import lib.Func;

public class Main {
    public static void main(String[] args) {
        System.out.println("Main");
        Func func = new Func();
        func.print();
    }
}
```

- Func.java
```java
package lib;

public class Func {
    public void print() {
        System.out.println("Func");
    }
}
```

## javac命令

javac命令的用途是将.java文件编译为.class文件。

1. 在本实验中主要参数
- -sourcepath
    指定查找输入的.java文件的位置
    默认为.
- -d
    指定放置生成的.class文件的位置
    默认为-sourcepath的值
- -classpath
    指定额外用于查找需要依赖的.class文件的位置
    默认为.


2. 相关实验

（每次运行命令后，需要复原初始实验目录结构）

- 尝试直接编译Main.java
```shell
$ javac ./java/Main.java
```
  结果提示编译失败，找不到Main.java中所引用的`lib`和`lib.Func`符号。

- 将Main.java和Func.java一起编译
```shell
$ javac ./java/Main.java ./java/lib/Func.java
```
编译成功，.class文件生成在了.java文件所在目录，成功后的./java目录结构如下
```
./java
├── Main.class
├── Main.java
└── lib
    ├── Func.class
    └── Func.java
```
如果有很多.java文件，不必将每个.java文件都输入，以下命令可以起到相同效果
```shell
$ javac ./java/**/*.java
```

- 指定-sourcepath参数
```shell
$ javac -sourcepath ./java ./java/Main.java
```
编译成功，结果与上两个命令的相同。可以观察到，指定-sourcepath参数后，不需要再输入所有.java文件，只需要输入包含主方法类的Main.java了。在这个实验中，指定了-sourcepath为./java，因此编译Main.java时，在./java下寻找引用的符号`lib.Func`（lib包下的Func类），于是从./java目录开始，寻找lib/Func.java。

- 指定-d参数

习惯上开发者不会将.class文件和.java文件混杂着放在一起，而是会将二者分开，放在不同的位置。以下命令尝试编译并用-d参数将生成的.class文件放置在./classes下
```shell
$ javac -sourcepath ./java -d ./classes ./java/Main.java
```
编译成功，.class文件生成在了./classes下，其组织结构与对应的.java文件相同。成功后的目录结构如下
```
.
├── classes
│   ├── Main.class
│   └── lib
│       └── Func.class
└── java
    ├── Main.java
    └── lib
        └── Func.java
```

- 指定-classpath参数

如果当前只有Func.class，而没有Func.java，当想要依赖Func.class编译Main.java时，应当使用-classpath参数，将存有lib/Func.class文件的目录（./classes）加入classpath，这样javac才能在classpath中找到`lib.Func`符号相应的.class文件（lib/Func.class），然后进行Main.java的编译。

为了使用-classpath参数进行实验，暂时调整实验目录结构为如下
```
.
├── classes
│   └── lib
│       └── Func.class
└── java
    └── Main.java
```
并使用以下命令
```shell
$ javac -classpath ./classes -d ./classes ./java/Main.java
```
编译成功，Main.class生成在了预期位置，成功后的目录结构如下
```
.
├── classes
│   ├── Main.class
│   └── lib
│       └── Func.class
└── java
    └── Main.java
```
如果想将多个目录（事实上可以是非目录的其他位置，如jar位置）加入classpath，可以将多个目录进行拼接后（在bash中使用':'符号拼接），一起传入-classpath参数。

## java命令

java命令的用途是启动JVM，并让JVM运行.class文件。

1. 在本实验中主要参数

- -classpath
    指定额外用于查找类文件（.class文件）的位置
    默认为.

2. 相关实验

在经过javac的实验后，编译后的.class文件已经被放置在./classes下了，./classes目录结构如下
```
./classes
├── Main.class
└── lib
    └── Func.class
```
java命令要输入含主方法类的全类名。在本实验中，因为Main.java开头没有package声明，所以Main类的全类名就是Main，如果声明了package，则需要将package声明的包加入到全类名中（例如声明为`package main;`，则全类名为`main.Main`）。

尝试运行.class文件
```shell
$ java Main
```
提示错误找不到或无法加载主类，尝试使用-classpath参数把Main类所在目录加入classpath，再运行
```shell
$ java -classpath ./classes Main
```
程序正确执行，执行结果与预期一致。需要注意的是，运行Main.class需要依赖Func.class，但lib/Func.class（全类名为`lib.Func`）是在./classes下的，所以java命令能在classpath中找到`lib.Func`，程序能正确执行。

如果想将多个目录（事实上可以是非目录的其他位置，如jar文件）加入classpath，可以将多个目录进行拼接后（在bash中使用':'符号拼接），一起传入-classpath参数。

## jar命令

jar文件是一种归档文件格式，与zip类似。一般被用来打包.class文件，作为标识Java库的基本单位。习惯上也叫做jar包。在依赖第三方库使用java命令运行自己的Java程序时，其实就是将第三方库通过-classpath参数加入到了classpath中。开发者也可以将自己的程序(.class文件)打包到jar文件中，作为一个完整成品呈现给他人。

jar命令的用途是归档创建jar文件或提取jar文件中内容。

1. 在本实验中主要参数
- -x
    解压缩
- -c
    创建/归档
- -v
    显示详细输出信息
- -f
    指定jar文件名
- -m
    包含指定清单文件中的清单信息

2. 实验

在实验目录下创建artifact目录
```shell
$ mkdir artifact
```
通过以下命令将之前实验生成的.class文件打包为jar包，放置在./artifact下
```shell
$ jar -cvf ../artifact/main.jar -C ./classes .
```
参数-C ./classes .代表将./classes下的所有文件归档，并在归档后的jar文件内目录结构中，将./classes路径更名为.路径，这样归档后，Main.class可以暴露在jar文件内目录结构第一层。
完成后，实验目录结构如下
```
.
├── artifact
│   └── main.jar
├── classes
│   ├── Main.class
│   └── lib
│       └── Func.class
└── java
    ├── Main.java
    └── lib
        └── Func.java
```
查看main.jar的内容，可以用软件例如WinRAR打开以查看，或者使用如下命令查看
```shell
$ jar -tvf ./artifact/main.jar
```
观察到归档后jar命令自动添加了META-INF/MANIFEST.MF文件，这是jar文件中自带的清单文件，声明了该jar包的一些信息。

java命令可以将jar文件添加到classpath中来查找类，因此尝试如下命令来在main.jar中找到实验程序并运行
```shell
$ java -classpath ./artifact/main.jar Main
```
运行成功。习惯上，开发者会将主类信息写在jar文件中的清单文件中，以便使用该jar文件运行程序时不需要手动输入主类的全类名。可以自己在./classes下创建一个清单文件，写入“Main-Class: Main”，然后在归档时指定用该清单文件里的内容创建清单文件，使用如下命令在归档时指定利用清单文件里的信息
```shell
$ echo “Main-Class: Main” > ./mymanifest
$ jar -cvfm ./artifact/main.jar ./mymanifest -C ./classes .
```
使用如下命令，运行main.jar而不指定主类全类名
```shell
$ java -jar ./artifact/main.jar
```
运行成功。

## 总结

通过本文的实验，可以了解如何使用javac和java命令对简单的Java源代码进行基本的编译和运行，并可以了解到如何使用jar命令对.class文件进行基本的打包。