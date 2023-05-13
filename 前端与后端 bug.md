前端与后端 bug
========================
## 前端 vue

### 语法问题

* 在所有HTML中几乎都可以使用th: text属性，将接受的数据显示在标签内容中
```html
<span th:text="${name}"></span> <!--request作用域-->
<span th:text="${session.name}"></span> <!--session作用域-->
<span th:text="${user.name}"></span> <!--对象作用域-->
```
* th: each用来遍历对象来展示; th:if 做判断
* th: unless 相当于else
* th: switch 条件判断
* th: case="1"

```html
<tr th:each="b:${list}">
    <td th:text="${b.userId}"></td>
    <td th:text="${b.userName}"></td>
    <td th:text="${b.userPasswd}"></td>
</tr>
```
* html表单属性名与对象类名不一致时，要是在参数前加上@RequestParam("")绑定

### axios:
#### get方法:

* 方式一

```js
axios.get(url,{
    params:{  
        username:this.form.name,
        password:this.form.pwd
    }    
}).then(res =>{
    if(res.data.code == 100){  
        //进行页面跳转
        this.$messsage({
            showClose: true,
            message: result.data.msg,
            type: "success"
        });
        this.$router.push("/home");
    }
    else{
        //登录失败
        this.$messsage({
            showClose: true,
            message: result.data.msg,
            type: "error"
        });
        
    }
});
```
* 方式二
```js
this.$http.get(url/login?name=" + 
    this.form.name +
    "&pwd=" +
    this.form.pwd
).then(res  =>{
    //结果
    console.log(result);
})
```

#### post

````markdown
# axios的post请求

## 1.使用 qs.stringify()

### qs.stringify() 作用:

**将对象序列化成URL的形式**

默认表单数据（json格式）：

![image-20230114184055776](/home/papillon/.config/Typora/typora-user-images/image-20230114184055776.png)

使用qs.stringify()之后的数据形式：

![image-20230114184248892](/home/papillon/.config/Typora/typora-user-images/image-20230114184248892.png)

### axios.post 代码

```js
this.$axios.post('http://localhost:8090/register1',
                 // this.data=JSON.stringify(this.user),
                 this.data=this.$qs.stringify(this.user),
                 // this.data=(this.user)
    )
    .then(res=>{
    if(res.data.code==100){
        this.$message({
            showClose: true,
            message: res.data.msg,
            type: "success"
        });
        // this.$router.push("/");
        alert("注册成功！")
    }
    else{
        console.log(res+"error-----------------------------");
        this.$message({
            showClose: true,
            message: res.data.msg,
            type: "error"
        });
    }
});
```

### UserController 代码

```java
// "/register1" 是传递 String username, String password
@PostMapping("/register1")
    public ResultVO signUp(String username, String password){
        System.out.println("register__1          :"+username+password);
        ResultVO insert = UserServiceImpl.Insert(username, password);
        System.out.println(insert);
        return insert;
    }

```



## 2. 使用 Map来接收前端表单传来json数据

### 原理解释：

* json格式为 {username : "aaaa", password : "1111"}，与Map格式一致，故可用Map对象接收

### axios.post 代码

```js
this.$axios.post('http://localhost:8090/register2',
                 // this.data=JSON.stringify(this.user),
                 // this.data=this.$qs.stringify(this.user),
                 this.data=(this.user)
    )
    .then(res=>{
    if(res.data.code==100){
        this.$message({
            showClose: true,
            message: res.data.msg,
            type: "success"
        });
        // this.$router.push("/");
        alert("注册成功！")
    }
    else{
        console.log(res+"error-----------------------------");
        this.$message({
            showClose: true,
            message: res.data.msg,
            type: "error"
        });
    }
});
```

### UserController代码

```java
// "register2" 用Map对象接收json形式数据
@PostMapping("/register2")
    public ResultVO signUp(@RequestBody Map<String,String> user){
        System.out.println("register__2       :"+user);
        ResultVO insert = UserServiceImpl.Insert(user.get("username"), user.get("password"));
        System.out.println(insert);
        return insert;
    }
```

## 3.使用实体类对象接收json格式数据  (老师上课演示)

### **特别注意**:

> 前端传递过来的数据必须和我们的bean实体对象属性一致，若不一样，我们可以在前端再定义一个和实体类属性相同的json格式对象！！！

### axios.post代码

```js
// 定义一个和自己实体类属性名一样的包含帐号密码的对象
//根据自己的实体类来，我的实体类属性帐号密码为， userName, userPasswd. 在你的环境要根据你的来！！！！！
let nameAndPwd = {
    userName : this.user.username,			
    userPasswd: this.user.password 
};



// post请求
this.$axios.post('http://localhost:8090/register3',this.data=nameAndPwd)
    .then(res=>{
    if(res.data.code==100){
        this.$message({
            showClose: true,
            message: res.data.msg,
            type: "success"
        });
        // this.$router.push("/");
        alert("注册成功！")
    }
    else{
        console.log(res+"error-----------------------------");
        this.$message({
            showClose: true,
            message: res.data.msg,
            type: "error"
        });
        // alert('131 row error');
    }
});

```

```java
//  使用对象接收必须保证表单属性 和 实体类的属性相同
    @PostMapping("/register3")
    public ResultVO signUp(@RequestBody User user){
        System.out.println("register__3       :"+user);
        ResultVO insert = UserServiceImpl.Insert(user.getUserName(), user.getUserPasswd());
        System.out.println(insert);
        return insert;
    }
```



## 4.使用JSON.stringify()

### JSON.stringify()作用: 

将json格式字符串化:  {username : "aaaa", password : "1111"}    ===>  {"username" : "aaaa", "password" : "1111"}

默认表单数据（json格式）：

![image-20230114184055776](/home/papillon/.config/Typora/typora-user-images/image-20230114184055776.png)

JSON.stringify() 格式化后：

![image-20230114192453776](/home/papillon/.config/Typora/typora-user-images/image-20230114192453776.png)

### 原理：

> 将数据转化为字符串传到后端， 利用相关函数分割字符串并提取出来所需要的数据。

**这种方法过于繁琐，且容易出错，这里不再进行演示.**



## PS: 前三种方法我已经测试，均可正确运行，如果有哪里说的不对的地方，欢迎大家一起讨论，一起进步！
````

### 在浏览器控制台查看 vue对象

* 使用 JSON.stringify(obj),  将json格式转化为字符串格式

## 后端 springboot

### 数据格式问题

* @Responebody  将json格式转化为java对象

  > 可以在controllor类头部加入，也可以在方法参数对象前加入

### MAVEN依赖问题

* 当引入的依赖集成了其他的依赖和目前依赖发生冲突时，要将含有的集成依赖注释掉，用自己原本的依赖！

  > 例如引入tk.mybatis集成了mybatis, 要把tk.mybatis中集成的依赖注释掉

### 关于tk.mybatis找不到实体类的问题

>  Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed: tk.mybatis.mapper.MapperException: 无法获取实体类com.example.demo.entity.User对应的表名!]

* 还是依赖问题，要使用springboot starter 合适版本的mybatis，并要解决依赖冲突问题，将集成的依赖注释掉。(鼠标右键转到定义)



# PwrTest 项目问题
## 找出RTDF的读取与转换
1. PTEditLog_Slot(Qstring msg);     from      MaintestWidget 
2. DealLogMsg_Slot(QString msg)     from      Thread;
3. OnDataLog                        from      ConnectQtAndMfcClass
4. DealLogMsg_Slot                  from      MainTestWidget



# 打包问题
在使用VS进行Qt项目打包release时，可能会出现缺少资源文件和dll库的情况。这是因为在Qt项目中，资源文件和dll库是以相对路径的方式引用的，而在发布时，这些文件可能无法正确地被复制到目标路径。为了解决这个问题，需要进行如下操作：

将需要发布的资源文件和dll库复制到发布目录中。可以在Qt项目的.pro文件中添加如下代码，将资源文件和dll库复制到指定目录中：

```markdown
# 将资源文件复制到发布目录中
DESTDIR = release
RESOURCES += resources.qrc
QMAKE_POST_LINK += $$quote(copy /y $$quote($$PWD\\resources\\*.* $$DESTDIR))
# 复制 dll 文件到发布目录中
win32:CONFIG(release, debug|release): LIBS += -L$$PWD/ -lmydll
else:win32:CONFIG(debug, debug|release): LIBS += -L$$PWD/ -lmydlld
INCLUDEPATH += $$PWD/
DEPENDPATH += $$PWD/
# 将 dll 文件复制到发布目录中
win32:CONFIG(release, debug|release): PRE_TARGETDEPS += $$PWD/mydll.dll
else:win32:CONFIG(debug, debug|release): PRE_TARGETDEPS += $$PWD/mydlld.dll
QMAKE_POST_LINK += $$quote(copy /y $$quote($$PWD\\mydll*.dll $$DESTDIR))
```

以上代码将资源文件和dll库复制到release目录中，其中mydll.dll和mydlld.dll分别表示release和debug模式下的dll库文件名。
2. 在Qt项目中添加相对路径。在Qt项目的.pro文件中，可以使用相对路径来引用资源文件和dll库。例如，可以将资源文件路径设置为"resources.qrc"，将dll库路径设置为"lib/mydll.dll"，这样在发布时就可以正确地引用这些文件了。
3. 在VS中添加Qt的bin目录到系统环境变量中。如果在发布时仍然缺少dll库文件，可以在VS中添加Qt的bin目录到系统环境变量中。在VS的菜单栏中选择“工具”→“选项”→“项目和解决方案”→“VC++目录”，在“包含目录”和“库目录”中添加Qt的bin目录，例如：C:\Qt\Qt5.12.8\5.12.8\msvc2017_64\bin。
通过以上步骤，就可以解决在VS中打包Qt项目时缺少资源文件和dll库的问题了。


# 命令行调用系统编译问题
在C++语言中，我们通常使用系统命令（system command）来调用编译器的编译命令。下面介绍一下如何调用Visual Studio、Clang++和MingGW64的编译命令。

Visual Studio 编译命令
在 C++ 中使用 Visual Studio 编译命令，我们需要打开“Developer Command Prompt for VS”命令行窗口，然后使用 cl 命令进行编译。

```c++
#include <cstdlib>

int main()
{
    system("cl /EHsc <source_file>.cpp");
    return 0;
}
```
上述代码使用了 system 函数来执行命令行编译器指令，在字符串中输入编译器命令cl /EHsc <source_file>.cpp，其中 /EHsc 表示启用标准异常处理。

如果要进行调试，可以添加 /Zi 和 /Od 参数：

```c++
system("cl /EHsc /Zi /Od <source_file>.cpp");
```
该命令将生成 PDB 文件以供调试，并设置优化等级为无。

Clang++ 编译命令
在 C++ 中使用 Clang++ 编译命令，同样也需要打开命令行窗口，然后使用 clang++ 命令进行编译。

```c++
#include <cstdlib>

int main()
{
    system("clang++ -std=c++11 <source_file>.cpp");
    return 0;
}
```
上述代码与 Visual Studio 编译命令的代码非常相似，只是把编译器名修改为 clang++ ，并且加了 -std=c++11 参数来指定 C++11 标准。其他参数同理。


# Qt 图元
在Qt中，图元（Graphics Item）是指可以在场景（Scene）或窗口中显示的二维图形对象。使用图元可以构建各种复杂的用户界面。以下是一些关于在Qt中使用图元的基本步骤：

创建场景：使用QGraphicsScene类创建一个场景对象。
QGraphicsScene *scene = new QGraphicsScene();
创建图元：使用QGraphicsItem及其子类创建图元对象。
QGraphicsRectItem *rectItem = new QGraphicsRectItem(0, 0, 100, 100);
将图元添加到场景中：使用场景的addItem()函数将图元添加到场景中。
scene->addItem(rectItem);
显示场景：使用QGraphicsView类创建一个视图对象，并将场景设置为该视图的场景。
QGraphicsView *view = new QGraphicsView(scene);
显示视图：将视图添加到窗口中，即可显示场景和图元。
view->show();
可以通过修改图元的属性、位置等来实现不同的效果。常用的图元类包括QGraphicsRectItem、QGraphicsEllipseItem、QGraphicsTextItem、QGraphicsPixmapItem等。同时，Qt还提供了一些更高级的图元类，如QGraphicsWidget和QGraphicsProxyWidget，它们可以与QWidget集成，方便地将QWidget作为图元添加到场景中。
## 标准图元
QGraphicsSimpleTextItem：提供了一个简单的文本标签项
QGraphicsTextItem：提供了一个格式化的文本项
QGraphicsLineItem：提供了一个直线项
QGraphicsPixmapItem：提供了一个图像项
QGraphicsRectItem：提供了一个矩形项
QGraphicsEllipseItem：提供了一个椭圆项
QGraphicsPathItem：提供了一个路径项
QGraphicsPolygonItem：提供了一个多边形项

## QFontMetrics
QFontMetrics类提供字体规格信息。
QFontMetrics函数计算给定字体的字符和字符串的大小。您可以通过三种方式创建QFontMetrics对象：
用QFont调用QFontMetrics构造函数会为屏幕兼容字体创建字体度量对象，即该字体不能为打印机字体。如果以后更改字体，则不会更新字体指标对象。
（注意：如果您使用打印机字体，则返回的值可能不正确。由于无法始终访问打印机字体，因此，如果提供了打印机字体，则使用最近的屏幕字体。）
QWidget :: fontMetrics（）返回小部件字体的字体指标。这等效于QFontMetrics（widget-> font（））。如果稍后更改窗口小部件的字体，则不会更新字体指标对象。
QPainter :: fontMetrics（）返回画家当前字体的字体度量。如果稍后更改画家的字体，则不会更新字体指标对象。
创建对象后，该对象将提供用于访问字体，其字符以及以字体呈现的字符串的各个度量的功能。
有几种对字体起作用的函数：ascent（），descent（），height（），leading（）和lineSpacing（）返回字体的基本大小属性。 underlinePos（），overlinePos（），

strikeOutPos（）和lineWidth（）函数返回下划线，上划线或删除字符的行的属性。这些功能都很快。
还有一些对字体的字形集起作用的函数：minLeftBearing（），minRightBearing（）和maxWidth（）。这些速度一定很慢，我们建议尽可能避免使用它们。
对于每个字符，您都可以使用inFont（）获得其width（），leftBearing（）和rightBearing（）并找出它是否在字体中。您也可以将字符视为字符串，并在其上使用字符串函数。
字符串函数包括width（）（返回像素的字符串宽度（或点，对于打印机）），boundingRect（），返回足够大的矩形以包含呈现的字符串的大小，以及size（），返回该矩形的大小。

## 自定义图元
QT自定义图形项中的boundingRect()和shape()函数的理解
实现自定义图形项经常需要重绘的函数有boundingRect()、paint()、shape()。
针对霍亚飞的Qt creator中所说，boundingRect()函数具有以下特点：
1.paint绘制的图像必须在boundingRect()函数之中。
2.用来确定哪些区域需要重构（repaint）。
3.用来检测碰撞 可以用shape() 改变检测碰撞范围

## 绘图更新五种模式
总共有五种模式，很容易理解：
QGraphicsView::FullViewportUpdate 全视口更新，整体都更新的意思啦
QGraphicsView::MinimalViewportUpdate 最小更新，哪里有变动更新哪里
QGraphicsView::SmartViewportUpdate 智能选择，它要自己选
QGraphicsView::BoundingRectViewportUpdate 来了，来了，它就是我们要注意的。
QGraphicsView::NoViewportUpdate 不更新
其中默认为QGraphicsView::MinimalViewportUpdate，也就是上例中我们没有进行设置的情况。事实上除了设置为FullViewportUpdate 其余四种皆会出现问题，不妨试一试。
我们可以通过在MyView的构造函数中设置为FullViewportUpdate 的全视口更新得到我们想要的结果，但是却是以牺牲性能为代价的。

## QPainterPathStroker
要生成可填充的轮廓，一般分为两步：

    定义原始绘图路径 QPainterPath path，调用 QPainterPathStroker::createStroke(path)，以 path 为样本创建一个新的绘图路径 QPainterPath outlinePath，outlinePath 表示 path 的可填充的轮廓。
    填充 outlinePath，绘制出原始绘图路径 path 的轮廓。
除此之外，还可以使用以下函数来控制轮廓的各种样式：

    setWidth()：宽度
    setCapStyle()：端点风格
    setJoinStyle()：连接样式
    setDashPattern()：虚线图案
注意： 由 createStroke() 生成的新绘图路径（outlinePath）应仅用于指定的绘图路径（path）的轮廓，否则，可能会引发意外行为。

## QPainter中的setRenderHint函数
setRenderHint函数是QPainter类中的一个函数，用于设置绘图选项。它的作用是在绘制图形时设置一些渲染选项，以改变绘图的效果。

QPainter类中的setRenderHint函数有多个参数，每个参数代表一种渲染选项。这些选项包括：

- QPainter::Antialiasing：启用反锯齿渲染，使得图形边缘更加平滑。
- QPainter::TextAntialiasing：启用文本反锯齿渲染，使得文本更加清晰。
- QPainter::SmoothPixmapTransform：启用平滑的Pixmap变换，使得Pixmap的缩放效果更加平滑。
- QPainter::HighQualityAntialiasing：启用高质量反锯齿渲染，比Antialiasing选项更加平滑。
- QPainter::NonCosmeticDefaultPen：使用非化妆品的默认笔，使得绘制的线条更加粗壮。
- QPainter::Qt4CompatiblePainting：启用Qt4兼容的绘图方式，使得绘制效果更加类似于Qt4。

使用setRenderHint函数可以根据需要设置不同的渲染选项，以达到更好的绘图效果。

## QPixmap
QPixmap是Qt框架中的一个类，用于表示一个像素图像。它可以加载各种格式的图像文件（如PNG、JPG、BMP等），并提供了一系列方法来操作和处理这些图像。

QPixmap类可以用于在Qt应用程序中显示图像，例如在窗口中显示一个图标或者在一个自定义控件中显示一张图片。它还可以用于处理图像，例如缩放、裁剪、旋转、转换颜色等等。

QPixmap类提供了许多方法来访问和修改图像数据。例如，可以使用load()方法从文件中加载图像，可以使用scaled()方法缩放图像，可以使用copy()方法复制一部分图像数据，等等。

总之，QPixmap是一个非常有用的类，可以在Qt应用程序中方便地处理和显示图像。

## QAction和QMenu
QAction和QMenu是Qt框架中常用的两个类，它们之间有着紧密的关系。

QAction是一个动作类，它代表一个可以在应用程序中执行的操作。这个操作可以通过菜单、工具栏、快捷键等方式触发。QAction可以设置图标、文本、快捷键等属性，也可以连接到一个槽函数，当用户触发这个操作时，槽函数会被调用。

QMenu是一个菜单类，它代表一个菜单项或者一个弹出菜单。QMenu可以包含多个QAction，每个QAction都代表一个菜单项。QMenu可以设置标题、图标、快捷键等属性，也可以添加子菜单、分隔符等。

## 在connect中声明信号函数
在Qt中，通常将QAction添加到QMenu中，以创建一个菜单项。当用户点击这个菜单项时，对应的QAction会被触发，执行相应的操作。例如，我们可以创建一个“打开文件”菜单项，将它添加到一个QMenu中，当用户点击这个菜单项时，QAction会打开一个文件对话框，让用户选择要打开的文件。

可以的。在Qt中，可以在connect函数中声明信号函数。connect函数的第一个参数是发送信号的对象，第二个参数是信号函数的名称，第三个参数是接收信号的对象，第四个参数是槽函数的名称。下面是一个示例：

```
connect(sender, SIGNAL(mySignal(int)), receiver, SLOT(mySlot(int)));
```

在上面的示例中，mySignal是发送信号的对象的信号函数，mySlot是接收信号的对象的槽函数。

## qt信号与槽的重载
Qt的信号和槽可以重载，但是需要注意以下几点：

1. 信号和槽的函数名必须相同；
2. 信号和槽的参数类型和数量必须不同；
3. 重载的信号和槽必须使用不同的参数列表；
4. 重载的信号和槽必须使用不同的名称，可以通过函数指针或lambda表达式来连接不同的信号和槽。

例如，下面的代码演示了如何重载一个信号和槽：

```cpp
class MyClass : public QObject
{
    Q_OBJECT
    
public:
    MyClass(QObject *parent = nullptr) : QObject(parent) {}
    
signals:
    void mySignal(int value);
    void mySignal(double value);
    
public slots:
    void mySlot(int value) { qDebug() << "int value:" << value; }
    void mySlot(double value) { qDebug() << "double value:" << value; }
};

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);

    MyClass obj;
    QObject::connect(&obj, &MyClass::mySignal, &obj, &MyClass::mySlot);
    QObject::connect(&obj, static_cast<void(MyClass::*)(double)>(&MyClass::mySignal), &obj, &MyClass::mySlot);

    emit obj.mySignal(123);
    emit obj.mySignal(3.14);

    return app.exec();
}
```

在这个例子中，MyClass类定义了两个重载的信号和槽，分别接受int和double类型的参数。我们可以通过函数指针或lambda表达式来连接不同的信号和槽。


## 弹窗提示
在 Qt 中弹出提示信息可以使用 QMessageBox 类。以下是一个简单的示例：

cpp
QMessageBox::information(this, tr("标题"), tr("提示信息"));

# VS 编译错误
## 链接错误
```
1>EduTest.obj : error LNK2001: 无法解析的外部符号 "public: void __thiscall EduTest_AutoLoader::LoadInfoChange_Signal(void)" (?LoadInfoChange_Signal@EduTest_AutoLoader@@QAEXXZ)
1>EduTest_AutoLoader.obj : error LNK2001: 无法解析的外部符号 "public: void __thiscall EduTest_AutoLoader::LoadInfoChange_Signal(void)" (?LoadInfoChange_Signal@EduTest_AutoLoader@@QAEXXZ)
1>EduTest.obj : error LNK2001: 无法解析的外部符号 "public: static struct QMetaObject const EduTest_AutoLoader::staticMetaObject" (?staticMetaObject@EduTest_AutoLoader@@2UQMetaObject@@B)
1>EduTest_AutoLoader.obj : error LNK2001: 无法解析的外部符号 "public: virtual struct QMetaObject const * __thiscall EduTest_AutoLoader::metaObject(void)const " (?metaObject@EduTest_AutoLoader@@UBEPBUQMetaObject@@XZ)
1>EduTest_AutoLoader.obj : error LNK2001: 无法解析的外部符号 "public: virtual void * __thiscall EduTest_AutoLoader::qt_metacast(char const *)" (?qt_metacast@EduTest_AutoLoader@@UAEPAXPBD@Z)
1>EduTest_AutoLoader.obj : error LNK2001: 无法解析的外部符号 "public: virtual int __thiscall EduTest_AutoLoader::qt_metacall(enum QMetaObject::Call,int,void * *)" (?qt_metacall@EduTest_AutoLoader@@UAEHW4Call@QMetaObject@@HPAPAX@Z)
```

+ 可能是字符编码格式问题，可用 UTF-8(BOM)