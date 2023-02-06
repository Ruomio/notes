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
