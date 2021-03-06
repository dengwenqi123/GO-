#### 设置工作目录

工作目录就是我们用来存放开发的源代码的地方，对应Go里的GOPATH这个环境变量。指定这个环境变量后，我们编译源代码等生成的文件都会放到这个目录下，该目录下有3个子目录，分别是:bin 、 pkg 、 src

- bin文件夹存放go install 命名生成的可执行文件，可以把GOPATH/bin路径加入到PATH环境变量里。
- pkg 文件夹是存在go编译生成的文件。
- src存放的是我们的go源代码，不同工程项目的代码以包名区分。

源代码都存放在GOPATH的src目录下，那么有多个项目的时候，怎么区分呢？答案是**通过包**，使用包来组织我们的项目目录结构。包以网站域名开头就不会重复，比如我的个人网站是flysnow.org,我就可以以flysnow.org 的名字创建一个文件夹，我自己的go项目都放在这个文件夹里，这样就不会和其他人的项目冲突，包名也是唯一的。

go 里面通过import 导入包。通过包路径，包路径就是从src目录开始，逐级文件夹的名字用/连起来就是我们需要的包名。

#### 安装程序

安装的意思，就是生成可执行的程序，以供我们使用，为此go为我们提供了很方便的install 命令，可以快速的把我们的程序安装到$GOPATH/bin目录下。 go install flysnow.org/hello

### 什么事Go语言中的包

在Go语言中，包也是类似的概念，它是把我们的go文件组织起来，可以方便进行归类、复用等目的。比如Go内置的net包

go 语言的包的命令，遵循简洁、小写和go文件所在的目录同名的原则，这样就便于我们引用，书写以及快速定位查找。

对于多于一个路径的包名，在代码中引用的时候，使用全路径最后一个包名作为引用的包名，比如net/http，我们在代码使用的是http,而不是net.

对于包的查找，是有优先级的，编译器会优先在GOROOT里搜索，其次是GOPATH，一旦找到，就会马上停止搜索。如果最终都没有找到，就报编译异常。

go get 工具可以递归获取依赖报，如果github.com/spf13/cobra也引用了其他的远程包，该工具可以一并下载下来。

##### 包的init函数

每个包都可以有任意多个init函数，这些init函数都会在main函数之前执行。init函数通常用来做初始化变量、设置包或者其他需要在程序执行前的引导工作。比如上面我们讲的需要使用 _ 空标志符来引入一个包的目的，这就是想执行这个包里的init函数。



























