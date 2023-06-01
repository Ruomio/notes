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

