# EduTest

vs 2010版本问题，咱们不都是用的2015吗

## 每日周报
每天工作内容。
每周汇报
### 4月 (从有git记录开始)
date        |                           Worklog                          |
| --------- |:----------------------------------------------------------:|
4.4         |   更新.gitignore; 熟悉整个项目结构                           |
4.5-4.7     |   实现右键console,将测试结果保存为rtdf格式                    |
4.8         |   每次加载新测试项目,删除旧rtdf文件;rtdf保存方式改变;编译按钮;  |
4.10-4.13   |   探索LibView图像化编程,尝试后放弃LibView,选择使用Qt框架开发;  |
4.10-4.12   |   搭建整个项目结构                                           |
4.13        |   所有的图元结构体定义                                       |
4.14        |   实现连接线的曲率计算，实时更新曲率                          |
4.17        |   所有图元的菜单操作，以及鼠标滚轮操作                        |
4.18        |   MainWindowWidget搭建，包括工具栏和侧边栏                   |
4.19        |   箭头图元的实现                                             |
4.20        |   从侧边栏拖动到Scene生成图元                                 |
4.21        |   修改昨天的bug，图元基类到派生类数据阶段，造成空指针异常        |
4.23        |   解决图元范围超过View的绘图范围，造成view有像素残留问题          |
4.24        |   解决EduTest中测试出的bug                                    |
4.25        |   修改icon，修改菜单问题，工具栏，关闭逻辑等                    |
4.26        |   参数配置 界面                                               |
4.27        |   SetAllParamsSetting界面，table中插入行列的实现                 |
4.28        |   PatternExec 的子界面。                                     |

### 5月
date        |                           Worklog                          |
| --------- |:----------------------------------------------------------:|
5.4         |   重构项目的项目名                                           |
5.5-5.6     |   请假了                                                     |
5.8         |   存channelmap功能实现     修正tooltip                        |
5.9         |   在界面显示flow的路径 改变tdr位置     打开项目文件夹           |
5.10        |   按钮样式，icon样式                                          |
5.11        |   pause overrride的逻辑修改                                   |
5.12        |   SetAllParamsSetting中所有按钮的槽函数实现                    |
5.15        |   修改project显示位置，从flowwidget到menuBar                  |
5.16        |   改变flowwidget布局                                         |
5.17        |   修改编译的实现，使程序在开发环境和测试环境都可正常使用。修复编译后加载的问题|
5.18        |   CreateItemWidget 界面及实现                                 |
5.19        |   改变projectPath显示方式，试了很多方法，无法在menuBar悬浮显示，改成点击切换全路径|
5.22        |   上机测试发现vectorDebugger的问题，和Burce交涉后解决         |
5.23-5.25   |   RTDF问题，没有按格式写入文件头信息和尾信息，参考stdf理解结构后解决问题|
5.26        |   继承QCpmboBox实现复选框，并以逗号分割                       |
5.29        |   修改所有QTableWidget实现拉伸效果，修改插入cpp逻辑           |
5.30        |   停电                                                      |
5.31        |   GraphTest的垂直磁吸线错位问题，右键拖动视图问题              |

5.31 0.5
5.30 1
5.19 0.5
5.12 0.5
5.5 1
5.6 1
共计 4.5 天
24-4.5 = 19.5


### 6月
date        |                           Worklog                          |
| --------- |:----------------------------------------------------------:|
6.1         |   图元像素区域超过视图绘制矩形范围的问题                      |
6.2         |   QGraphicsView中的 像素 绘制bug，（高分屏引起的）,exe icon   |
6.5         |   rtdf多次测试后无法正常保存问题。换一套存入方式解决(win api)  |
6.6         |   毕业典礼请假                                              |
6.7         |   override与pause布局问题。写入头文件，但中文乱码             |
6.8         |   参与专利申请交流会， 在 .cpp插入所需头文件                  |
6.9         |   与西安SOC讨论方案；改进写入Signal.stil文件逻辑；保存rtdf逻辑完善；参数配置界面完善|
6.12        |   SignalAndGroup保存方式大改                                  |


## 周期安排：

5月： ChannelMap模块，Signal模块

六月：DCExec，PatternExec模块

七月：TestItems模块，WxFlow模块以及整体测试

## Requirement

1. [x] 不需要切换用户
2. [x] 不需要 基本信息显示
3. [x] 卸载flow
4. [x] 关闭按钮
5. [x] 更改名称
6. [x] 停止测试 logo
7. [x] pause <- 停止icon
8. [x] 全项测试 <- override
9. [x] 格式转换 -> 向量转换
10. [x] pause -> 状态保持
11. [x] 状态栏 修改 
12. [x] logo
13. [x] 右上角picture
14. [x] logo 主改掉

1. [x] channelmap 拿掉
2. [x] 菜单栏 工具栏 协调
3. [x] flow位置显示
4. X 快速模式 学习模式
5. X 一行一个测试项, 只允许模范方式
6. - [x] 配置文件 和 cpp 分开界面
7. - [x] wxflow留一套入口
8. - [x] tdr 位置放到菜单栏
9. - [x] 文件右键打开文件夹 [] 另存为
10. - [x] inner checker 
11. - [x] 全项测试 位置 图片样式 勾选
12. - [x] 重复测试 tooltip 
13. - [x] 打开工程从tool 去掉
14. - [x] 更改名称 去掉
15. - [x] 删除测试项， 给出确认提示
16. - [x] 当前项目
17. - [] 联系burce,需要一些exe
18. - [x] 参数配置表 新增测试项
19. - [x] rtdfViewer 无法读取问题
20. DCSpec Param, ACSpec Param
21. - [] 参数配置 提供 导入CSV功能
22. - [] 显示之前填入的数据
23. - [] shmoo margin 的可执行文件

### shmoo margin 功能模块
2.4.0_p2 version
searching 功能 hosea交流





## RTDFViewer 
AITest 只有测试结果导出的rtdf：
> FAR ATR SDR PMR PMR PMR PMR PMR PMR PMR PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PIR
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
PRR
HBR
SBR
PCR
MRR

PwrTest 只有测试结果rtdf:
> PIR
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
PRR

AITest 所有的rtdf导出结果：
> FAR
ATR
SDR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
STR
TEXT
STR
STR
STR
STR
STR
STR
STR
TEXT
STR
TEXT
TEXT
TEXT
TEXT
TEXT
STR
STR
STR
STR
TEXT
TEXT
TEXT
STR
STR
TEXT
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
TEXT
TEXT
STR
STR
STR
STR
STR
STR
TEXT
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
TEXT
TEXT
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
STR
TEXT
STR
STR
STR
STR
STR
STR
PRR
PRR
HBR
SBR
PCR
MRR
FAR
ATR
SDR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PMR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PGR
PIR
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
FTR_EXT
PTR_EXT
PRR
HBR
SBR
PCR
MRR

### RTDF文件尾部写入失败
复现：
只要测试次数超过10次。尾部信息被识别为TEXT

对比同样操作与AITest区别：


## 测试项写入办法
1. 通过模板：参数要开放很多


2. X 通过初步设计的填表，填写太复杂



## 复选框实现
- DSCheckComboModel类
```c++
class DSCheckComboModel : public QStandardItemModel
{
	Q_OBJECT

public:
	explicit DSCheckComboModel(QObject* parent = nullptr);

	virtual Qt::ItemFlags flags(const QModelIndex &index) const;
	virtual QVariant data(const QModelIndex &index, int role = Qt::DisplayRole) const;
	virtual bool setData(const QModelIndex &index, const QVariant &value, int role = Qt::EditRole);

Q_SIGNALS:
	void checkStateChange();
};
```
> 这段代码定义了一个名为DSCheckComboModel的类，该类继承自QStandardItemModel类。在该类中声明了三个成员函数：flags()、data()和setData()。此外，还声明了一个信号checkStateChange()。
>
> DSCheckComboModel是一个自定义的数据模型类，用于实现一个带有复选框的下拉列表控件。flags()函数用于设置模型数据项的标志，以指示该数据项是否具有特定属性（如可编辑、可选中、可勾选等）。data()函数用于获取模型数据项的值，根据参数role不同可以返回不同的数据类型（如显示文本、图标、状态等）。setData()函数用于设置模型数据项的值，同时发出数据变化信号，以便更新视图上的相关内容。checkStateChange()信号表示复选框的选中状态已经改变。
>
> 通过继承QStandardItemModel类并重载其中的函数，可以方便地实现复杂的数据模型，并与Qt框架中的其他组件进行无缝集成。

- DSCheckComboBoxPrivate 类
```c++
class DSCheckComboBox;
class DSCheckComboBoxPrivate : public QObject
{

	Q_DECLARE_PUBLIC(DSCheckComboBox)
	DSCheckComboBox* q_ptr;

public:
	DSCheckComboBoxPrivate(QObject* parent = Q_NULLPTR);
	bool eventFilter(QObject* obj, QEvent* e);

	QString separator;
	QString defaultText;
	bool containerMousePress;

	void updateCheckedItems();
	void toggleCheckState(int index);
};
```
> 这段代码定义了一个名为 DSCheckComboBoxPrivate 的类，它是 QObject 类的子类。该类中声明了一个指向 DSCheckComboBox 类对象的指针 q_ptr，以及一些成员变量和成员函数。
>
> 其中，Q_DECLARE_PUBLIC(DSCheckComboBox) 宏用于在类的私有部分声明一个指向公共部分的指针，它允许私有部分访问公共部分成员函数和数据成员。
>
> DSCheckComboBoxPrivate 中的成员变量包括：
>```txt 
> separator：分隔符；
> defaultText：默认文本；
> containerMousePress：容器鼠标按下。
> 成员函数包括：
> ```
>```markdown
> DSCheckComboBoxPrivate(QObject* parent = Q_NULLPTR)：构造函数；
> bool eventFilter(QObject* obj, QEvent* e)：事件过滤器；
> void updateCheckedItems()：更新已选项；
> void toggleCheckState(int index)：切换选框状态。
> ```

- DSCheckComboBox 类
```c++
class DSCheckComboBox : public QComboBox
{
	Q_OBJECT

	Q_PROPERTY(QString separator READ separator WRITE setSeparator)
	Q_PROPERTY(QString defaultText READ defaultText WRITE setDefaultText)
	Q_PROPERTY(QStringList checkedItems READ checkedItems WRITE setCheckedItems)

public:
	DSCheckComboBox(QWidget *parent = Q_NULLPTR);
	~DSCheckComboBox();

	//隐藏下拉框
	virtual void hidePopup();

	//获取默认文本
	QString defaultText() const;
	//设置默认文本
	void setDefaultText(const QString& text);

	//获取勾选状态
	Qt::CheckState itemCheckState(int index) const;
	//设置勾选状态
	void setItemCheckState(int index, Qt::CheckState state);

	//获取字符串分割方式
	QString separator() const;
	//设置字符串分割方式
	void setSeparator(const QString& separator);

	//获取所有勾选的文本
	QStringList checkedItems() const;
	//获取所有勾线的下标
	QVariantList checkedIndexs() const;

public Q_SLOTS:
	void setCheckedItems(const QStringList& items);

Q_SIGNALS:
	void checkedItemsChanged(const QStringList& items);

protected:
	virtual bool eventFilter(QObject *watched, QEvent *event);
	virtual void wheelEvent(QWheelEvent *e);

private:
	QScopedPointer<DSCheckComboBoxPrivate> d_ptr;
	Q_DISABLE_COPY(DSCheckComboBox)
	Q_DECLARE_PRIVATE(DSCheckComboBox)
	Q_PRIVATE_SLOT(d_func(), void updateCheckedItems())
	Q_PRIVATE_SLOT(d_func(), void toggleCheckState(int index))
};
```

> 这是一个自定义的 Qt 组件类 DSCheckComboBox，继承自 QComboBox。该类添加了一些额外的属性和方法，以支持多选、获取勾选状态、获取所有勾选的文本等功能。
> 
> 以下是该类的主要成员和作用：
> ```markdown
> - Q_PROPERTY：宏定义，用于声明属性，包括读取和写入该属性的函数。
> - hidePopup()：重载了 QComboBox 中的方法，用于隐藏下拉框。
> - defaultText() 和 setDefaultText()：用于获取和设置默认文本。
> - itemCheckState() 和 setItemCheckState()：用于获取和设置下拉框中某一项的勾选状态。
> - separator() 和 setSeparator()：用于获取和设置字符串分割方式。
> - checkedItems() 和 checkedIndexs()：分别用于获取所有勾选的文本和所有勾选项的索引。
> - setCheckedItems()：用于设置勾选的文本。
> - checkedItemsChanged()：信号，当勾选的项目发生变化时发出该信号。
> - eventFilter()：事件过滤器，用于在事件处理之前捕获并处理事件。
> - wheelEvent()：鼠标滚轮事件，用于处理鼠标滚轮事件。
> - d_ptr 和 d_func()：用于实现 PIMPL 模式，隐蔽了类的实现细节。
> ```

## 新增测试项
+ PwrTest策略
> .temp 表格的模板
> 
> .test cpp测试项的模板

### 问题
1. 判断编码格式
2. 手动粘贴代码
3. 



# 专利只是交流会
## 自动化项目
> 市场需求： IGBT 功率半导体
>           自动化：
>           作用： ATE测试机，Handler自动化设备，探针台Wafer Prober。 
>           1.上料
>           2.测试, 模拟工作环境，极限温度（高低温）。检查
>           3.分析
>
## 专利交流
非正常申请，短时间内大量的申请。
拼凑出来的专利。
申请专利的资助和奖励取消。
专利要根据项目来整。
加急程序，高质量申请。
### 专利基础知识
1. 发明
提出新的技术方案
2. 外观
富有美感的设计，六视图
3. 实用
形状结构

### 不能申请：
科学发现、智力活动、动植物新品种、平面印刷、违反法律道德、原子核变换方法、疾病诊断和治疗方法。

### 审查
新颖性，创造性，实用性
先申请专利，再发表论文和期刊，甚至微信公众号
无效化专利，成功后会失效，编程公开技术
最后复审三次

### 文件
权力要求书
说明书
说明附图：流程图

### 高价值专利
战略新兴产业
在海外有同族专利
维持年限超过10年
实现较高融资
获得国家技术奖，中国专利奖的发明专利

1-3年左右可以授权
专利预审，半年内可以授权

找合肥申请，转让，或者当第二申请人

检索工具
专利汇，中国及多国专利审查
