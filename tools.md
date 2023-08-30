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



# MarkDowm

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


# Clang LLVM
查找默认include 路径
clang++ -c file.cc -v 编译将打印出其他内容:
```shell
#include "..." search starts here:
#include <...> search starts here:
/usr/bin/../lib/gcc/x86_64-linux-gnu/4.9/../../../../include/c++/4.9
```



# veovim
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


