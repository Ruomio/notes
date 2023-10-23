# Git

## 命令

```shell
git remote add origin ${仓库地址}
git remote rm origin
git commit -m “代码提交信息”
git push origin master
git branch  develop
git push -u origin develop
git checkout -b <本地分支名 feature/***> <origin/develop>
或者
git fetch origin 远程分支名:本地分支名
git branch --set-upstream-to=origin/远程分支名    本地分支名
git pull origin develop //先拉取develop中的代码，因为有可能别人已经往上提交过代码了
git checkout  develop//切到develop分支
git merge <feature/**>//合并feature/**中的代码到develop中
git push //提交到develop远程分支上
git branch -d feature/** //删除本地的分支
git checkout -b <本地分支名realse-0.1> <远程分支名develop>//注意这个realse-tagNo分支的功能是对发布的代码进行改善的地方
git rm --cached ${file}  // 从远程仓库删除文件
git rm --cached -r ${fileDir} //从仓库删除文件夹
git status //	查看仓库当前的状态，显示有变更的文件。
git diff //比较文件的不同，即暂存区和工作区的差异。
git reset	//回退版本。
git rm	将文件从暂存区和工作区中删除。
git mv	移动或重命名工作区文件。
git fetch	从远程获取代码库
git pull	下载远程代码并合并
git push	上传远程代码并合并
$ git log --oneline --decorate --graph // 查看提交记录
git blame <file> // 查看文件修改记录
$ git tag -a <标签名>  // 打标签 
$ git tag -a <tagname> -m "message" //指定标签信息
$ git tag -a <标签名> <版本号> // 追加已经发布的版本
$ git tag // 查看所有标签
```

* 查看配置信息

> ➜  blogs git config --global user.email "1065940593@qq.com"
> ➜  blogs git config --global user.name "Ruomio"
> ➜  blogs git config --list

* 使用ssh协可以免去密码验证

> git remote set-url origin ${ssh协议地址}    来更改远程地址

###  git ignore规则

```shell
a# 忽略所有 .a 结尾的文件
!lib.a# 但lib.a 除外
/TODO# 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/# 忽略build/ 目录下的所有文件
doc/.txt# 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

> 1. 如果已经提交过的文件或者文件夹怎么办？此时更改.gitignore文件对已经提交的文件是无效的。
>
>    2.1 首先，编辑.gitignore文件。
>
>    2.2 然后如果是单个文件，可以使用如下命令从**仓库**中删除：
>
>    `git rm --cached logs/xx.log`
>
>    如果是整个目录：
>    `git rm --cached -r logs`
>
>    如果文件很多，那么直接
>    `git rm --cached -r .`
>
>    如果提示某个文件无法忽略，可以添加`-f`参数强制忽略。
>    `git rm -f --cached logs/xx.log`
>
>    2.3 然后
>    `git add .`
>    `git commit -m "Update .gitignore"`
>
>    

* 注意：应该在忽略某些文件之前，先将它们从仓库中删除，并确保其他人已经拉取了这个更新。或者，在忽略某些文件后，不要将它们提交到仓库中，以避免影响其他人的本地文件。

### 保留文件但不跟踪更改
+ --skip-worktree
* --assume-unchanged

```shell
$ git update-index --skip-worktree file1
$ git update-index --assume-unchanged file1
```
命令 git update-index 的 --skip-worktree 选项使 Git 假装文件的版本是最新的，而是从索引版本中读取。这对于配置文件特别有用。

> --assume-unchanged 假定开发人员不会更改文件。此标记旨在为无变化文件夹（如 SDK）改善性能。
> 
> --skip-worktree 用于命 GIT 不再染指特定文件——即便开发人员可能更改它——的情形。例如，如果主源码库上游承载某些即将投入生产的配置文件而你不希望意外的提交影响到那些文件

1.assume-unchanged 假定不变。

这个会关闭文件与远程仓库的跟踪，认为这个文件远程仓库是不会修改，所以每次pull都是本地的文件

2.skip-worktree 跳过工作树
这个不会关闭文件与远程仓库的跟踪，只是告诉Git不要跟踪对本地文件/文件夹的更改

pull拉取最新的变化,会提示冲突，但因为没有跟踪本地更改，所以需要no-skip-worktree再合并最新的变化
最合适的是skip-worktree，因为它还在跟踪远程库的修改。只是合并修改比较麻烦


## 统计提交代码
要统计一个Git仓库中提交了多少行代码，可以使用以下命令：

```git
git log --author=<作者名> --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "Added lines: %s, Removed lines: %s, Total lines: %s\n", add, subs, loc }' -
```

将 `<作者名>` 替换为你想要统计的作者名，或者省略该参数以统计整个仓库的代码行数。

该命令会输出三个数字，分别表示新增的行数、删除的行数和总行数。



# tar 命令

tar x *.rar 解压文件到同名目录

tar e *.tar 解压文件到同级目录





# MarkDowm

## 流程图

> 以下几个实例效果图如下：
>
> **1、横向流程图源码格式：**
>
> ````
> ```mermaid
> graph LR
> A[方形] -->B(圆角)
>     B --> C{条件a}
>     C -->|a=1| D[结果1]
>     C -->|a=2| E[结果2]
>     F[横向流程图]
> ```
> ````
>
> **2、竖向流程图源码格式：**
>
> ````
> ```mermaid
> graph TD
> A[方形] --> B(圆角)
>     B --> C{条件a}
>     C --> |a=1| D[结果1]
>     C --> |a=2| E[结果2]
>     F[竖向流程图]
> ```
> ````
>
> **3、标准流程图源码格式：**
>
> ````
> ```flow
> st=>start: 开始框
> op=>operation: 处理框
> cond=>condition: 判断框(是或否?)
> sub1=>subroutine: 子流程
> io=>inputoutput: 输入输出框
> e=>end: 结束框
> st->op->cond
> cond(yes)->io->e
> cond(no)->sub1(right)->op
> ```
> ````
>
> **4、标准流程图源码格式（横向）：**
>
> ````
> ```flow
> st=>start: 开始框
> op=>operation: 处理框
> cond=>condition: 判断框(是或否?)
> sub1=>subroutine: 子流程
> io=>inputoutput: 输入输出框
> e=>end: 结束框
> st(right)->op(right)->cond
> cond(yes)->io(bottom)->e
> cond(no)->sub1(right)->op
> ```
> ````
>
> **5、UML时序图源码样例：**
>
> ````
> ```sequence
> 对象A->对象B: 对象B你好吗?（请求）
> Note right of 对象B: 对象B的描述
> Note left of 对象A: 对象A的描述(提示)
> 对象B-->对象A: 我很好(响应)
> 对象A->对象B: 你真的好吗？
> ```
> ````
>
> **6、UML时序图源码复杂样例：**
>
> ````
> ```sequence
> Title: 标题：复杂使用
> 对象A->对象B: 对象B你好吗?（请求）
> Note right of 对象B: 对象B的描述
> Note left of 对象A: 对象A的描述(提示)
> 对象B-->对象A: 我很好(响应)
> 对象B->小三: 你好吗
> 小三-->>对象A: 对象B找我了
> 对象A->对象B: 你真的好吗？
> Note over 小三,对象B: 我们是朋友
> participant C
> Note right of C: 没人陪我玩
> ```
> ````
>
> **7、UML标准时序图样例：**
>
> ````
> ```mermaid
> %% 时序图例子,-> 直线，-->虚线，->>实线箭头
>   sequenceDiagram
>     participant 张三
>     participant 李四
>     张三->王五: 王五你好吗？
>     loop 健康检查
>         王五->王五: 与疾病战斗
>     end
>     Note right of 王五: 合理 食物 <br/>看医生...
>     李四-->>张三: 很好!
>     王五->李四: 你怎么样?
>     李四-->王五: 很好!
> ```
> ````
>
> **8、甘特图样例：**
>
> ````
> ```mermaid
> %% 语法示例
>         gantt
>         dateFormat  YYYY-MM-DD
>         title 软件开发甘特图
>         section 设计
>         需求                      :done,    des1, 2014-01-06,2014-01-08
>         原型                      :active,  des2, 2014-01-09, 3d
>         UI设计                     :         des3, after des2, 5d
>     未来任务                     :         des4, after des3, 5d
>         section 开发
>         学习准备理解需求                      :crit, done, 2014-01-06,24h
>         设计框架                             :crit, done, after des2, 2d
>         开发                                 :crit, active, 3d
>         未来任务                              :crit, 5d
>         耍                                   :2d
>         section 测试
>         功能测试                              :active, a1, after des3, 3d
>         压力测试                               :after a1  , 20h
>         测试报告                               : 48h
> ```
> ````

## 公式块

`$$`进入公式块编辑, 行间公式

`$***$`在中间写公式，行内公式

> `a\div{b}`:  $a\div{b}$
>
>  `a\pm{b}`: $a\pm{b}$
>
> `a\frac{a}{b}`: $\frac{a}{b}$
>
> `\sqrt{a}`: $\sqrt{a}$
>
> `\cdots`: $\cdots$
>
> `\sin{\theta}`: $\sin{\theta}$
>
> `\vec{`F`}`: $\vec{F}$
>
> `\sum_{i=1}^{n}{a_i}`: $\sum_{i=1}^{n}{a_i}$
>
> `\prod_{i=1}^{n}{a_i}`: $\prod_{i=1}^{n}{a_i}$
>
> `\lim_{a\rightarrow+\infty}{a+b}`: $\lim_{a\rightarrow+\infty}{a+b}$
>
> `\leg`: $\leq$
>
> `\geq`: $\geq$















# Make

## clean

> **make** clean 清除之前编译的可执行文件及配置文件。
> **make** **distclean** 清除所有生成的文件。

# hexo

##  命令

hexo clean 清除缓存

hexo (d)eploy  部署

hexo (g)ene

hexo d -g 同步到gitihub

# docker

## 备份和恢复mysql数据

单数据库

> ```shell
> docker exec -i mysql /bin/bash -c 'mysqldump -uroot -p123456 test' > /home/mysql/backup/emp_`date +\%F`.sql;
> ```

多数据库

> ```shell
> docker exec -i mysql /bin/bash -c 'mysqldump -uroot -p123456 --databases test' > /home/mysql/backup/emp_`date +\%F`.sql;
> ```

全数据库

> ```shell
> docker exec -i mysql /bin/bash -c 'mysqldump -uroot -p123456 --all-databases ' > /home/mysql/backup/emp_`date +\%F`.sql;
> ```

**还原：**

> 1. 进入mysql容器, 并选择数据库
>
> 2. ```shell
>    source /var/backup/emp_2023-01-13.sql
>    ```

## 复制到容器 

1.  从本机到容器

> docker cp
>
> $ docker cp new_file.txt 0c57de10362b:/usr/share

1. 从容器到容器

> docker volum 
>
> $ docker volume create volume_one
>
> $ docker volume ls
>
> $ docker run -d -v volume_one:/app nginx:latest
>
> $ docker inspect f2457d3eb8fe
>
> `docker volume` 命令的优点之一是创建与多个容器共享的单个目录。

# ffmpeg

## 主要参数

| 参数         | 说明                               |
| ------------ | ---------------------------------- |
| -version     | 显示版本。                         |
| -formats     | 显示可用的格式（包括设备）。       |
| -demuxers    | 显示可用的demuxers。               |
| -muxers      | 显示可用的muxers。                 |
| -devices     | 显示可用的设备。                   |
| -codecs      | 显示libavcodec已知的所有编解码器。 |
| -decoders    | 显示可用的解码器。                 |
| -encoders    | 显示所有可用的编码器。             |
| -bsfs        | 显示可用的比特流filter。           |
| -protocols   | 显示可用的协议。                   |
| -filters     | 显示可用的libavfilter过滤器。      |
| -pix_fmts    | 显示可用的像素格式。               |
| -sample_fmts | 显示可用的采样格式。               |
| -layouts     | 显示channel名称和标准channel布局。 |
| -colors      | 显示识别的颜色名称。               |

## 视频参数

| 参数                                                | 说明                                                         |
| --------------------------------------------------- | ------------------------------------------------------------ |
| -vframesnum（输出）                                 | 设置要输出的视频帧的数量。对于-frames：v，这是一个过时的别名，您应该使用它。 |
| -r [：stream_specifier] fps（输入/输出，每个流）    | 设置帧率（Hz值，分数或缩写）。作为输入选项，忽略存储在文件中的任何时间戳，根据速率生成新的时间戳。这与用于-framerate选项不同（它在FFmpeg的旧版本中使用的是相同的）。如果有疑问，请使用-framerate而不是输入选项-r。作为输出选项，复制或丢弃输入帧以实现恒定输出帧频fps。 |
| -s [：stream_specifier]大小（输入/输出，每个流）    | 设置窗口大小。作为输入选项，这是video_size专用选项的快捷方式，由某些分帧器识别，其帧尺寸未被存储在文件中。作为输出选项，这会将缩放视频过滤器插入到相应过滤器图形的末尾。请直接使用比例过滤器将其插入到开头或其他地方。格式是’wxh’（默认 - 与源相同）。 |
| -aspect [：stream_specifier] 宽高比（输出，每个流） | 设置方面指定的视频显示宽高比。aspect可以是浮点数字符串，也可以是num：den形式的字符串，其中num和den是宽高比的分子和分母。例如“4：3”，“16：9”，“1.3333”和“1.7777”是有效的参数值。如果与-vcodec副本一起使用，则会影响存储在容器级别的宽高比，但不会影响存储在编码帧中的宽高比（如果存在）。 |
| -vn（输出）                                         | 禁用视频录制。                                               |
| -vcodec编解码器（输出）                             | 设置视频编解码器。这是-codec：v的别名。                      |
| -vffiltergraph（输出）                              | 创建由filtergraph指定的过滤器图，并使用它来过滤流。          |

## 音频参数

| 参数                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| -aframes（输出）                                            | 设置要输出的音频帧的数量。这是-frames：a的一个过时的别名。   |
| -ar [：stream_specifier] freq（输入/输出，每个流）          | 设置音频采样频率。对于输出流，它默认设置为相应输入流的频率。对于输入流，此选项仅适用于音频捕获设备和原始分路器，并映射到相应的分路器选件。 |
| -ac [：stream_specifier]通道（输入/输出，每个流）           | 设置音频通道的数量。对于输出流，它默认设置为输入音频通道的数量。对于输入流，此选项仅适用于音频捕获设备和原始分路器，并映射到相应的分路器选件。 |
| -an（输出）                                                 | 禁用录音。                                                   |
| -acodec编解码器（输入/输出）                                | 设置音频编解码器。这是-codec的别名：a。                      |
| -sample_fmt [：stream_specifier] sample_fmt（输出，每个流） | 设置音频采样格式。使用-sample_fmts获取支持的样本格式列表。   |
| -affiltergraph（输出）                                      | 创建由filtergraph指定的过滤器图，并使用它来过滤流。          |

## 例子

>  ffmpeg [global_options] {[input_file_options] -iinput_url} ...
>                          {[output_file_options] output_url} ...

```shell
# 导出音频并指定起始位置
ffmpeg -i src.mp4 -i -ss %h:%m:%m.%ms -t %h:%m:%m.%ms  -vn -y out.mp3
# 合并音视频
ffmpeg -i test.mp4 -i test.mp3 -c copy out.mp4
```



# Qt
## 编译安装
1. configure.bat -static -prefix "D:\qt-5.12.2" -confirm-license -opensource  -debug-and-release -platform win32-msvc  -nomake examples -nomake tests -plugin-sql-sqlite -plugin-sql-odbc -qt-zlib -qt-libpng -qt-libjpeg -opengl desktop -mp
2. nmake // jom -j7
3. nmake install    // jom install -j7


# 正则表达式
## 如何使用
正则表达式（Regular Expression）是一种用于描述字符串模式的语言，它可以用来匹配、搜索、替换和验证文本。编写一个正则表达式需要遵循以下步骤：
```txt
确定匹配的模式：首先需要确定要匹配的字符串模式，这个模式可以是一个固定的字符串，也可以是一个含有通配符的模板。

选择合适的元字符：正则表达式包括一些特殊的字符，称为元字符，这些元字符可以在模式中表示某些特定的字符或字符集合，例如 "." 表示任意单个字符，"|" 表示或关系，"[]" 表示字符集等等。根据实际需求选择合适的元字符。

使用限定符：限定符用于指定匹配模式出现的次数，例如 "*" 表示出现零次或多次，"+" 表示出现至少一次，"?" 表示出现零次或一次，"{n}" 表示出现恰好 n 次，"{n, m}" 表示出现 n 到 m 次等。

处理边界情况：如果需要只匹配字符串的开头或结尾，可以使用 "^" 和 "$" 元字符，分别表示字符串的开头和结尾。

组合规则：将上述元字符、限定符和边界情况按照实际需求组合起来，形成一个完整的正则表达式。

测试验证：编写完成后，需要对正则表达式进行测试验证，看是否能正确匹配目标字符串，并根据需要进行调整和优化。
```

## () 作用
```txt
在正则表达式中，写进小括号 () 的作用是将括号内的模式定义为一个捕获组（capturing group），以便后续可以使用这个捕获组进行操作。例如，在搜索或替换文本时，我们可能需要引用正则表达式中某些子模式匹配的内容，这时就可以使用捕获组来实现。

具体来说，如果正则表达式中包含了一个或多个小括号，那么每对小括号内的模式都会被解释为一个捕获组，捕获组的序号按照左括号的出现顺序从左到右编号，从 1 开始。例如，正则表达式 "(ab)+cd(e?f)" 中包含两个捕获组，第一个捕获组对应的是模式 "ab"，第二个捕获组对应的是模式 "e?f"。

在使用捕获组时，可以通过在正则表达式中使用反向引用来引用捕获组所匹配的文本，即使用 "\n" （n 为捕获组的序号）来表示第 n 个捕获组所匹配的文本。例如，如果要将字符串 "abc123def" 中的数字替换成 "[123]"，可以使用正则表达式 "([0-9]+)" 匹配数字，并使用 "\1" 来引用捕获组所匹配的文本，然后将其替换为 "[\1]"。

总之，写进小括号 () 的作用是将括号内的模式定义为一个捕获组，可以在后续操作中使用该捕获组进行引用和处理。
```

# CMake

## 目录结构

### 多级目录

```txt
.
├── bin
├── build
├── CMakeLists.txt
└── src
    ├── CMakeLists.txt
    ├── main.cpp
    ├── model1
    │   ├── CMakeLists.txt
    │   ├── model1.cpp
    │   └── model1.h
    ├── model2
    │   ├── CMakeLists.txt
    │   ├── model2.cpp
    │   └── model2.h
    └── model3
        ├── CMakeLists.txt
        ├── model3.cpp
        └── model3.h
```

### 常用变量

> PROJECT_SOURCE_DIR：工程的根目录
>
> PROJECT_BINARY_DIR：运行cmake命令的目录，通常为${PROJECT_SOURCE_DIR}/build
>
> PROJECT_NAME：返回通过 project 命令定义的项目名称
>
> CMAKE_CURRENT_SOURCE_DIR：当前处理的 CMakeLists.txt 所在的路径
>
> CMAKE_CURRENT_BINARY_DIR：target 编译目录
>
> CMAKE_CURRENT_LIST_DIR：CMakeLists.txt 的完整路径
>
> EXECUTABLE_OUTPUT_PATH：重新定义目标二进制可执行文件的存放位置
>
> LIBRARY_OUTPUT_PATH：重新定义目标链接库文件的存放位置

## 语法

### 小demo

```cmake
cmake_minimum_required(VERSION 3.15)

# set the project name
project(Tutorial)

# add the executable
add_executable(Tutorial tutorial.cpp)
```

* 指定了项目名后，就可以用`${PROJECT_NAME}`来表示项目名

* 生成可执行文件需要指定相关的源文件，如果有多个，那么就用空格隔开，比如：

    > add_executable(${PROJECT_NAME} a.cpp b.cpp c.cpp)

* 也可以用一个变量来表示这多个源文件：

    > ```cmake
    > set(SRC_LIST a.cpp b.cpp c.cpp)
    > add_executable(${PROJECT_NAME} ${SRC_LIST})
    > ```

* `set`命令指定变量名后，可用`${var_name}`获取变量的值，如上`${SRC_LIST}`

### 配置头文件：

> configure_file(TutorialConfig.h.in TutorialConfig.h)

由于TutorialConfig.h 文件会被自动写入 build 目录，因此必须将该目录添加到搜索头文件的路径列表中。将以下行添加到 CMakeLists.txt 文件的末尾：

```cmake
target_include_directories(${PROJECT_NAME} PUBLIC
                           ${PROJECT_BINARY_DIR}
                           )
```

`PROJECT_BINARY_DIR` 表示当前工程的二进制路径，即编译产物会存放到该路径，此时`PROJECT_BINARY_DIR` 就是 build 所在路径。

然后创建TutorialConfig.h.in文件，包含以下内容：

```cmake
// the configured options and settings for Tutorial
#define Tutorial_VERSION_MAJOR @Tutorial_VERSION_MAJOR@
#define Tutorial_VERSION_MINOR @Tutorial_VERSION_MINOR@
```

当使用 CMake 构建项目后，会在 build 中生成一个 TutorialConfig.h 文件，内容如下：

```cmake
// the configured options and settings for Tutorial
#define Tutorial_VERSION_MAJOR 1
#define Tutorial_VERSION_MINOR 0
```

### 指定C++版本

```cmake
cmake_minimum_required(VERSION 3.25)

# set the project name and version
project(${PROJECT_NAME} VERSION 1.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
```

### **添加库**

在子文件夹中创建CMakeLists.txt,并添加下面一行

> add_library(MathFunctions mysqrt.cpp)

此时文件结构：

```txt
  ./
    build/
    MathFunctions/
       CMakeLists.txt
       MathFunctions.h
    mysqrt.cpp
    CMakeLists.txt
    tutorial.cpp
    TutorialConfig.h.in
```

为了使用 MathFunctions 这个库，我们将在顶级 CMakeLists.txt 文件中添加一个 `add_subdirectory(MathFunctions)` 命令指定库所在子目录，该子目录下应包含 CMakeLists.txt 文件和代码文件。

可执行文件要使用库文件，需要能够找到库文件和对应的头文件，可以分别通过 `target_link_libraries` 和 `target_include_directories` 来指定。

使用 `target_link_libraries` 将新的库文件添加到可执行文件中，使用 `target_include_directories` 将 MathFunctions 添加为头文件目录，添加到 Tutorial 目标上，以便 mysqrt.h 可以被找到。

顶级 CMakeLists.txt 的最后几行如下所示：

```cmake
# add the MathFunctions library
add_subdirectory(MathFunctions)

# add the executable
add_executable(${PROJECT_NAME} tutorial.cpp)

target_link_libraries(${PROJECT_NAME} PUBLIC MathFunctions)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(${PROJECT_NAME} PUBLIC
                           ${PROJECT_BINARY_DIR}
                           ${PROJECT_SOURCE_DIR}/MathFunctions
                           )
```

### 将库设为可选项

第一步是向顶级 CMakeLists.txt 文件添加一个选项。

```cmake
option(USE_MYMATH "Use tutorial provided math implementation" ON)
```

`option` 表示提供用户可以选择的选项。命令格式为：`option(<variable> "description [initial value])`。

`USE_MYMATH` 这个选项缺省值为 ON，用户可以更改这个值。此设置将存储在缓存中，以便用户不需要在每次构建项目时设置该值。

下一个更改是使 MathFunctions 库的构建和链接成为条件。于是创建一个 if 语句，该语句检查选项 `USE_MYMATH` 的值。

```cmake
if(USE_MYMATH)
  add_subdirectory(MathFunctions)
  list(APPEND EXTRA_LIBS MathFunctions)
  list(APPEND EXTRA_INCLUDES ${PROJECT_SOURCE_DIR}/MathFunctions)
endif()

# add the executable
add_executable(${PROJECT_NAME} tutorial.cpp)

target_link_libraries(${PROJECT_NAME} PUBLIC ${EXTRA_LIBS})

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(${PROJECT_NAME} PUBLIC
                           ${PROJECT_BINARY_DIR}
                           ${EXTRA_INCLUDES}
                           )
```

在 if 块中，有 `add_subdirectory` 命令和 `list` 命令，`APPEND`表示将元素`MathFunctions`追加到列表`EXTRA_LIBS`中，将元素 `${PROJECT_SOURCE_DIR}/MathFunctions` 追加到列表`EXTRA_INCLUDES`中。`EXTRA_LIBS` 存储 MathFunctions 库，`EXTRA_INCLUDES` 存储 MathFunctions 头文件。

### 添加库的使用要求

使用要求会对库或可执行程序的链接、头文件包含命令行提供了更好的控制，也使 CMake 中目标的传递目标属性更加可控。利用使用要求的主要命令是：

- target_compile_definitions()
- target_compile_options()
- target_include_directories()
- target_link_libraries()

`CMAKE_CURRENT_SOURCE_DIR` 表示 当前CMakeLits.txt所在目录

首先声明，链接 MathFunctions 库的任何可执行文件/库文件都需要包含 MathFunctions 目录作为头文件路径，而 MathFunctions 本身不需要包含，这被称为 `INTERFACE` 使用要求。

`INTERFACE`是指消费者需要、但生产者不需要的那些东西。在`MathFunctions/CMakeLists.txt` 最后添加：

```cmake
# MathFunctions/CMakeLists.txt
target_include_directories(MathFunctions
          INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
          )
```

`CMAKE_CURRENT_SOURCE_DIR` 表示 MathFunctions 库所在目录。

现在我们已经为 MathFunctions 指定了使用要求 `INTERFACE`，那么可以从顶级 CMakeLists.txt 中删除`EXTRA_INCLUDES`变量的相关使用：

现在只要是链接了 MathFunctions 库，就会自动包含 MathFunctions 所在目录的头文件，简洁而优雅。

> * INTERFACE
> * PRIVATE
> * PUBLIC

1、使用要求除了 `INTERFACE`，还有`PRIVATE` 和 `PUBLIC`。`INTERFACE`表示消费者需要生产者不需要，`PRIVATE`表示消费者不需要生产者需要，`PUBLIC` 表示消费者和生产者都需要。

2、这里使用 `add_library` 命令生成的 MathFunctions 库其实是静态链接库。动态库和静态库的区别是：静态库在**链接阶段**会被链接到最终目标中（比如可执行程序），缺点是同一个静态库如果被不同的程序引用，那么内存中会存在这个静态库函数的多份拷贝。动态库在链接阶段不会被拷贝最终目标中，程序在**运行阶段**才会加载这个动态库。所以多个程序就算引用了同一个动态库，内存中也只存在一份动态库函数的拷贝。

### build目录介绍

```txt
build/
    CMakeCache.txt
    CMakeFiles/
    cmake_install.cmake
    Makefile
    Tutorial.exe
    TutorialConfig.h
    MathFunctions/
```

其中 `Makefile` 是 cmake 根据顶级 CMakeLists.txt 生成的构建文件，通过该文件可以对整个项目进行编译。

`Tutorial.exe` 就是生成的可执行文件，通过该文件运行程序。

`TutorialConfig.h` 是用于配置信息的头文件，是 cmake 根据 `TutorialConfig.h.in` 文件自动生成的。

还有个 MathFunctions 文件夹：

```text
MathFunctions/
    CMakeFiles/
    cmake_install.cmake
    Makefile
    libMathFunctions.a
```

其中 `Makefile` 是 cmake 根据 MathFunctions 目录下的 CMakeLists.txt 生成的构建文件。

`libMathFunctions.a` 则是 MathFunctions 静态链接库，可执行文件会通过这个库调用 `mysqrt` 函数。

### 命令

> \# 打印控制台信息
>
> MESSAGE(STATUS "Current path : ${PROJECT_SOURCE_DIR}")

## VScode 预定义变量

```
${userHome} - 用户主文件夹的路径
${workspaceFolder} - 在 VS Code 中打开的文件夹的路径
${workspaceFolderBasename} - 在 VS Code 中打开的文件夹的名称，没有任何斜杠 (/)
${file} - 当前打开的文件
${fileWorkspaceFolder} - 当前打开文件的工作区文件夹
${relativeFile} - 当前打开的文件相对于workspaceFolder
${relativeFileDirname} - 当前打开的文件相对于的目录名workspaceFolder
${fileBasename} - 当前打开文件的基本名称
${fileBasenameNoExtension} - 当前打开的文件的基本名称，没有文件扩展名
${fileExtname} - 当前打开文件的扩展名
${fileDirname} - 当前打开文件的文件夹路径
${fileDirnameBasename} - 当前打开文件的文件夹名称
${cwd} - 启动 VS Code 时任务运行器的当前工作目录
${lineNumber} - 活动文件中当前选定的行号
${selectedText} - 活动文件中的当前选定文本
${execPath} - 正在运行的 VS 代码可执行文件的路径
${defaultBuildTask} - 默认构建任务的名称
${pathSeparator} - 操作系统用来分隔文件路径中的组件的字符

```

## 调试

```cmake
# 可以在CMakeLists里安排一个输出变量的调试点，以跟踪整个构造过程。
get_cmake_property(_variableNames VARIABLES)
foreach (_variableName ${_variableNames})
    message(STATUS "${_variableName}=${${_variableName}}")
endforeach()
```

## 找不到ui_xxx.h

```shell
解决方法:
在ui的文件夹下打开终端,输入
uic xxxx.ui -o ui_xxxx.h
编译得到ui_xxx.h文件,该问题解决.
```

## 提升控件后找不到类

```txt
**在提升的同时指定头文件的绝对路径** 
```

## qt项目使用opencv

```cmake
# 添加
set(OpenCV_DIR /usr/lib/opencv4)
include_directories(${OpenCV_INCLUDE_DIRS})
find_package(OpenCV REQUIRED)

link_directories(${OpenCV_LIBRARY_DIRS})

target_link_libraries(widget_demo PRIVATE Qt${QT_VERSION_MAJOR}::Widgets Qt${QT_VERSION_MAJOR}::OpenGLWidgets ${OpenCV_LIBS})

```



## QT信号槽未能触发的问题

```txt
记录以下六点：
 
1）槽函数未声明为 slots 类型， 信号函数未声明为 signals所致。(QT5新语法不用考虑这点)
 
2）槽函数和信号函数的参数不一致。
 
3）某事件循环被阻塞导致信号未能发出。
 
4) ui存在的情况下，使用代码添加按钮槽(on_控件objName_clicked())而不是在界面上右键按钮转到槽。
    (若是代码添加按钮槽，需要增加自动关联。)
 
5）注意connect的位置。（也许你发出信号的时候，connect这行代码还未能执行）
 
6）注意信号发出者和接收者的作用域。 (某对象提前释放)
```

## QT的ui界面按钮点不了、不更新、无响应的可能原因

* 解决方法是把build文件在本地删掉，然后再编译运行，就一切正常了。

### 加入进度条程序卡住

> 解锁和msleep() 顺序不对 

### 退出程序是线程仍在运行

> 在析构函数中加入： quit();    wait();

## 在类的头文件中的 GET（）方法获取私有成员，要直接定义

```c++
// 例如
class XImagePro
{
public:
    // 设置原图，会清理处理的结果
    void Set(cv::Mat mat1, cv::Mat mat2); 
    cv::Mat Get(){ return dst; }
    XImagePro();
    ~XImagePro();

private:
    // origin img
    cv::Mat mat1,mat2;
    // dst img
    cv::Mat dst;
};
```


# Qt技巧

## 在QTableWidget的表格中添加多个控件

```C++
    //水平布局
    QHBoxLayout *vLayout = new QHBoxLayout();
    // 新建Widget
    QWidget *Widget_btn = new QWidget;
    // 布局中添加了控件
    vLayout->addWidget(btn_edit);
    // 布局中添加了水平间隔
    vLayout->addSpacing(10);
    // 布局中添加了控件
    vLayout->addWidget(btn_exit);
    // Widget中添加布局
    Widget_btn->setLayout(vLayout);
    Widget_btn->setStyleSheet("QWidget{ border: 0px }");
    //表格中添加Widget
    ui->table_userAdmin->setCellWidget(rowIndex,6,Widget_btn);
```

## QT中的容器

* Qt提供了以下顺序容器:QList、QLinkedList、QVector、QStack和QQueue。对于大多数应用程序，QList是最好的类型。虽然它是作为数组列表实现的，但是它提供了非常快的前置和附加。如果你真的需要一个链表，使用QLinkedList;如果您希望您的项目占用连续的内存位置，请使用QVector。QStack和QQueue是提供LIFO和FIFO语义的便利类。
* Qt还提供了这些关联容器:QMap、QMultiMap、QHash、QMultiHash和QSet。“多”容器方便地支持与单个键相关联的多个值。“哈希”容器通过使用哈希函数而不是对排序集进行二进制搜索，从而提供更快的查找。
* 作为特殊情况，QCache和QContiguousCache类在有限的缓存存储中提供了对象的高效散列查找。

## QGraphics

### QGraphics图形视图框架由3部分组成：

+ QGraphics Scene
+ Graphics Item
+ Graphics View

> Scene无限大，负责管理所有的Items，View是用来查看的窗口，可以透过这个窗口看到Scene的一部分。

> 注：有一种使用方法，多个Scene对应一个View，该每个Scene有自己的Items，相当于多个Scene每个都有自己管理得对象，通过切换Scene实现显示Item组的切换。







# Clang LLVM

查找默认include 路径
clang++ -c file.cc -v 编译将打印出其他内容:
```shell
#include "..." search starts here:
#include <...> search starts here:
/usr/bin/../lib/gcc/x86_64-linux-gnu/4.9/../../../../include/c++/4.9
```



# neovim
## 基本操作
+ 打开文件：在终端中输入 nvim 命令，后跟要打开的文件的路径，例如 nvim filename.txt。

+ 模式切换：Neovim有多个模式，包括普通模式、插入模式和命令模式。默认情况下，Neovim启动后进入普通模式。按下 i 键进入插入模式，可以开始编辑文本。按下 Esc 键返回普通模式。在普通模式下，可以执行各种命令。

+ 保存和退出：在普通模式下，按下 :w 命令保存文件，按下 :q 命令退出编辑器。如果文件有未保存的更改，可以使用 :wq 命令保存并退出。

+ 移动光标：在普通模式下，可以使用 h、j、k 和 l 键（分别对应左、下、上和右）来移动光标。还可以使用其他移动命令，例如 gg（跳到文件开头）、G（跳到文件末尾）、w（跳到下一个单词的开头）等。

+ 复制、剪切和粘贴：在普通模式下，可以使用 yy 复制当前行，使用 dd 剪切当前行。在普通模式下，将光标移动到要粘贴的位置，然后按下 p 键粘贴剪切或复制的内容。

+ 撤销和重做：在普通模式下，按下 u 键可以撤销最近的更改。按下 Ctrl + r 可以重做撤销的更改。

+ 搜索和替换：在普通模式下，按下 / 键可以进入搜索模式。输入要搜索的文本并按下 Enter 键。按下 n 键可以跳到下一个匹配项。使用 :%s/old/new/g 命令可以替换所有匹配项。

+ 插件和配置：Neovim支持插件和自定义配置。可以使用插件管理器（如Vim-Plug、Vundle或Pathogen）来安装和管理插件。配置文件位于 ~/.config/nvim/init.vim（Linux）或 %userprofile%\AppData\Local\nvim\init.vim（Windows）。

## 分割区域
1.分割窗口：

+ 水平分割：使用命令 :split 或 :sp。这将在当前窗口的下方创建一个新窗口。
+ 垂直分割：使用命令 :vsplit 或 :vsp。这将在当前窗口的右侧创建一个新窗口。

2.切换焦点：

+ 切换焦点到下一个窗口：使用命令 Ctrl + w, w。
+ 切换焦点到上一个窗口：使用命令 Ctrl + w, p。

3.关闭窗口：

+ 关闭当前窗口：使用命令 :q 或 :quit。
+ 关闭所有窗口，退出Neovim：使用命令 :qa 或 :quitall。

4.调整窗口大小：

+ 调整窗口高度：在普通模式下，将光标移动到窗口的分割线上，然后按下 Ctrl + w, + 或 Ctrl + w, - 来增加或减少窗口的高度。
+ 调整窗口宽度：在普通模式下，将光标移动到窗口的分割线上，然后按下 Ctrl + w, > 或 Ctrl + w, < 来增加或减少窗口的宽度。

## 缩进
1.快速缩进：

在普通模式下，将光标定位到你想要缩进的行或选择文本块。
按下 > 键进行向右缩进，或按下 >> 进行整行缩进。

2.快速反缩进：

在普通模式下，将光标定位到你想要反缩进的行或选择文本块。
按下 < 键进行向左反缩进，或按下 << 进行整行反缩进。

3.你还可以使用数字来指定缩进的级别。例如，3>> 将选定的文本块向右缩进3级。

4.如果你想要缩进或反缩进多行文本块，可以使用可视模式。以下是具体的步骤：

在普通模式下，将光标定位到你想要缩进或反缩进的起始位置。
按下 v 键进入可视模式。
使用光标键移动光标来选择文本块。
按下 > 进行向右缩进，或按下 < 进行向左反缩进。

