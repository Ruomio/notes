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
>    2.1 首先，编辑.gitignore文件。
>    2.2 然后如果是单个文件，可以使用如下命令从**仓库**中删除：
>    `git rm --cached logs/xx.log`
>    如果是整个目录：
>    `git rm --cached -r logs`
>    如果文件很多，那么直接
>    `git rm --cached -r .`
>    如果提示某个文件无法忽略，可以添加`-f`参数强制忽略。
>    `git rm -f --cached logs/xx.log`
>    2.3 然后
>    `git add .`
>    `git commit -m "Update .gitignore"`
>
>    



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



