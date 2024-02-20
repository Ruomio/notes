# EduTest

vs 2010版本问题，咱们不都是用的2015吗

## 报销流程
ADD ADTS 车票 出差申请 时间

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
24-4.5 -3 = 16.5


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
6.13        |   DCSequrnce 保存实现                                     |
6.14        |   TimeSet 保存的实现: 从文件读 并保存到变量Map                |
6.15        |   TimeSet 保存的实现: 从表格读,并写入文件; 保存配置信息到成员变量  |
6.16        |   ACSpec Saving;      out文件夹下自动写入Pattern Master.txt   |
6.19        |   阅读 Shmoo Margin源码                                       |
6.20        |   更改所有的路径获取方式   ，清楚与AITest的交互方式               |
6.21        |   与lepo沟通，知晓aitest的消息交互方式                        |
6.25        |   将shmoo margin并入项目, 向winter要有关依赖文件              |
6.26-6.29   |   Shmoo 与 Margin 功能得集成                                 |
6.30        |   Shmoo与Margin 工具栏图标                                    |


### 7月
date        |                           Worklog                          |
| --------- |:----------------------------------------------------------:|
7.3         |   ChannelMap与Signals的表格导出为JSON文件                    |
7.4         |   DCExec PatternExec DCLevel 导出Json                      |
7.5         |   上午去车间组装. DCSpec,DCSquence导出Json文件               |
7.6         |   TimeSet导出json                                          |
7.10        |   从json导入ChannelMap   SignalAndGroup                    | 
7.11        |   从json导入DCExec PatternExec DCLevel                     |
7.12-7.13   |   写文档;    DCSpec/DCSeq/Timeset import from json         |
7.14 7.17   |   解决ACSpec的顺序问题      所有table的清除功能              |
7.18        |   解决若干bug                                             |
7.19        |   操作手册  删除默认stil  编译前清除 *.gz  新增pattern后 更新PatternExec的include |
7.20-7.21   |   美化UI，是的父子界面风格统一                            |
7.24        |   优化UI     编写操作手册                                 |
7.25-7.30   |   学习MFC并将Shmoo和Margin编译成可执行文件                |
7.31-8.1    |   表格初始设置为 1行， 导入逻辑                           |
8.2-8.3     |   DataLog Option function                             |
8.4         |   尝试使用Cmake管理项目                                   |
8.7-8.11    |   尝试使用Cmake管理项目      制作EduTest安装包            |
8.14        |   将AITest后台集成，达到不需要额外安装AITest的效果        |
8.15        |   Cmake 编译项目成功，只有链接错误                        |

## bugs
1. - [x] channelMap更新时刻
2. - [x] 填表省略 统一一下
3. - [x] 每个按钮是否绑定了同一个对象
4. - [x] DCSeq写入顺序不对  ???
5. - [x] 点击dialog后显示的是父级界面
6. - [x] pattern save 空表终止
7. - [x] back delete ctrl+s 保存等按键响应
8. - [x] 写完vector  要修改 patternExec 中的Include
9. - [x] 新工程 要删除默认的stil文件 signal.stil exec.stil timing.stil vector/vector.stil
10. - [x] 编译前清理out文件夹下文件
11. - [x] 插入行 单元格为普通item   行高  widget的map  
12. - [x] 快捷键 复制粘贴 patternExec 清理
13. - [x] 所有工具  
    a. DataLog(x) <br/>
    b. SHmoo & Margin & VectorDebugger & InnerChecker & RCSDebug & RTDFViewer & TDRTest    <br/>
    c. start & stop & override & pause & repeat & formattanslate    <br/>
14. - [x] 表格初始 3-5 行  1行
15. - [x] 防呆设置 (限制为数字字母下划线)
16. - [x] line:534 PlotScopeData(&v[0], static_cast<int>(v.size()), name, dut, "V");
17. - [x] 安装包
18. - [ ] 按照规范 文档 
19. - [ ] vs2015 AITest EduTest 放在同一个安装包
20. - [x] license.dat 是根据环境变量读取得  AITest:  C:/AITest
21. - [ ] 需要修改的地方： a.所有出现AITest环境变量的地方 b. 所有引用.dll, .lib的地方

## EduTest文档
模块编号：
模块名称：
输入：
处理：
算法描述：
输出：


## 全局变量
Signals , vector中的文件名, 所有STIL文件名
QRegularExpression re("[A-Za-z0-9]+");

mainTestWidget -> MaintestDockWidget -> EduTest -> mSettingParamsWidget -> updateAllStil;

## 周期安排：

5月： ChannelMap模块，Signal模块

六月：DCExec，PatternExec模块

七月：TestItems模块，WxFlow模块以及整体测试

## Requirement

1. - [x] 不需要切换用户
2. - [x] 不需要 基本信息显示
3. - [x] 卸载flow
4. - [x] 关闭按钮
5. - [x] 更改名称
6. - [x] 停止测试 logo
7. - [x] pause <- 停止icon
8. - [x] 全项测试 <- override
9. - [x] 格式转换 -> 向量转换
10. - [x] pause -> 状态保持
11. - [x] 状态栏 修改 
12. - [x] logo
13. - [x] 右上角picture
14. - [x] logo 主改掉- 

1. - [x] channelmap 拿掉
2. - [x] 菜单栏 工具栏 协调
3. - [x] flow位置显示
4. - X 快速模式 学习模式
5. - X 一行一个测试项, 只允许模范方式
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
17. - [x] 联系burce,需要一些exe
18. - [x] 参数配置表 新增测试项
19. - [x] rtdfViewer 无法读取问题
20. - [x] DCSpec Param, ACSpec Param
21. - [x] 参数配置 提供 导入CSV功能(JSON)
22. - [x] 显示之前填入的数据
23. - [x] shmoo margin 的可执行文件
24. - [x] 功能树，到excel标注时间。
25. - [x] 向量转换 cancel
26. - [x] ACSpec, Pattern import from json
27. - [x] Clear 清除表格数据功能
28. - [x] ACSpec 变量先后顺序问题
29. - [ ] EduTest 函数文档
30. - [ ] Shmoo Margin 生成EXE



### shmoo margin 功能模块
2.4.0_p2 version
searching 功能 hosea交流

消息发送机制:gxSequence->callJobTask, gxSequence->PostSequence
> 说明文档
>
> IWXSeqence.h 
>
> esxOasisData.h 

```cpp
// 要先在SequenceId.h的枚举中新填一个成员
enum UXSEQUENCE_TYPE {
    // 原先的不动

    WM_USER     // 新增
}    

// 仅以Margin为例 假设成员都在类A中

void A::MsgConnect()
{
    Connect2GUI(WM_USER, m_hWnd);
     gxGlobalData->SetTaskHwnd(m_hWnd);

}

BEGIN_MESSAGE_MAP(A, CWnd)
    ON_WXOS_MESSAGE(WM_USER, showWindow)
END_MESSAGE_MAP()

void A::showWindow(WPARAM wParam, LPARAM lParam){

    func_Open_Margin_Window();

}


// 需要实现显示Margin窗口的函数

void B::BtnOpenMargin(){

    gxSequence->GenerateBasic(WM_USER, 0, 0);

}
```


```C++
void make_margin_organicdata(COasisData* pOrganic, MARGIN_ARGUMENT& margindata, int bOutPinMargin)
{
	// Common
	pOrganic->SetAString(margindata.title);
	for (int n = 0; n < 8; n++)
		pOrganic->SetInt(margindata.dut[n]);
	pOrganic->SetInt(margindata.individual);
	pOrganic->SetInt(margindata.stepbystep);
	pOrganic->SetInt(margindata.sequence);
	pOrganic->SetInt(margindata.orgin);
	pOrganic->SetInt(margindata.algorythm);
	pOrganic->SetInt(margindata.skip);
	pOrganic->SetDouble(margindata.udelay);
	pOrganic->SetAString(margindata.measSignal);

	// Axis
	pOrganic->SetAString(margindata.axis.szSetname);
	pOrganic->SetAString(margindata.axis.szType);
	pOrganic->SetAString(margindata.axis.szTimeset);
	pOrganic->SetAString(margindata.axis.szWFC);
	pOrganic->SetAString(margindata.axis.szEDGE);
	pOrganic->SetAString(margindata.axis.szSignal);
	pOrganic->SetDouble(margindata.axis.start);
	pOrganic->SetDouble(margindata.axis.end);
	pOrganic->SetDouble(margindata.axis.interval);

	// OutPin Margin
	pOrganic->SetInt(bOutPinMargin);
}


OASISHEAD head = { JOB_SC_EXEC, JOB_FC_EXEC_MARGIN, };
COasisData Organic(300, 300);
Organic.SetHead(&head);
// make_margin_organicdata(&Organic, marginArgument, dlg.m_bOutPinMargin == TRUE ? 1 : 0);	// 先不赋值
Organic.SetSize();
// m_Margin.SetUnit(AtoTS(m_AxisData.szEnd));

void* pResponse = NULL;
gxSequence->CallJobTask(Organic.GetPtr(), Organic.GetLength(), &pResponse);
if (pResponse) {
	free(pResponse);
}

```

需要头文件: TWM.h, TextInputDialog.h, WFCEditCtrl.h, EdgeEditCtrl.h, FloatEditCtrl.h, ComboBoxBold.h, TitleMenu.h, 




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







# Shmoo

## 代码解释

### ShmooControl.h

```markdown
该代码定义了一个名为CShmooControl的类，该类是从CWnd类派生而来的，用于创建一个绘制图形的控件。

代码中的主要成员函数包括：

Create：创建控件并指定其样式、位置等属性。
CalRange：计算绘制图形的范围。
Reset：重置控件的状态。
GetXMarkValue、GetYMarkValue、GetZMarkValue：根据给定的数值返回相应的字符串表示。
DrawBackground：绘制控件的背景。
DrawAxis：绘制坐标轴。
DrawShmooContent：绘制Shmoo内容。
DrawSearchContent：绘制搜索内容。
DrawCurrentSearchResult：绘制当前搜索结果。
DrawProgrammedValue：绘制已编程的值。
ClearData：清除数据。
StoreAssumeData、StoreData：存储数据。
Save：保存数据到文件。
Print：打印数据。
ReDraw：重新绘制控件。
SelectDut：选择DUT（Device Under Test）。
SetMergeMode：设置合并模式。
SetUnit：设置单位。
SetPlotType：设置绘图类型。
GetPlotType：获取绘图类型。
PreSubclassWindow：在子窗口创建前执行的操作。
析构函数。
该类还包含一些成员变量，用于存储控件的状态和数据。其中包括绘制所需的各种参数和选项，以及存储的数据结构。

此外，代码还定义了一些消息处理函数，用于处理控件的各种事件，如绘制、鼠标操作等。

整体上，该代码实现了一个用于绘制图形的自定义控件，并提供了一系列功能用于操作和显示数据。
```

### ShmooControl.cpp

```markdowm
这段代码是一个ShmooControl类的实现。该类是一个自定义的控件，用于显示Shmoo图形。

代码的功能包括：

定义了一些颜色常量，如NOTEST_BRUSH、ASSUME_FAIL_BRUSH等。

定义了一个名为"round"的内联函数，用于将浮点数四舍五入为整数。

实现了CShmooControl类的构造函数和析构函数。

实现了RegisterWindowClass()函数，用于注册窗口类。

定义了消息映射表，包括对窗口绘制、擦除背景、大小变化和鼠标事件的处理函数。

实现了OnEraseBkgnd()函数，用于处理擦除背景的消息。

实现了PreSubclassWindow()函数，用于在子类化窗口之前执行一些操作。

实现了Create()函数，用于创建控件。

实现了OnPaint()函数，用于处理绘制消息。

实现了CalRange()函数，用于计算绘图范围。

实现了OnSize()函数，用于处理窗口大小变化的消息。

实现了ReDraw()函数，用于重新绘制控件。

实现了Reset()函数，用于重置控件。

实现了SelectDut()函数，用于选择测试器件。

实现了一些辅助函数，如GetXMarkValue()、GetYMarkValue()和GetZMarkValue()，用于获取坐标轴上的刻度值。

实现了DrawBackground()函数，用于绘制控件的背景。

实现了DrawAxis()函数，用于绘制坐标轴。

函数DrawProgrammedValue用于绘制一个编程值（programmed value）。函数接受一个CDC（Device Context）对象指针pDC和一个布尔值bProcess作为参数。首先，根据给定的范围和网格大小计算x和y的间隔。然后，根据原始的x和y值计算出对应的索引xindex和yindex，如果索引越界，则直接返回。接下来，根据bProcess的值选择绘制的样式：如果为真，则使用黑色画笔和无刷子（填充颜色为空），绘制一个椭圆形；如果为假，则使用白色画笔和无刷子，绘制一个椭圆形。最后，将画笔设置为无画笔状态。

函数DrawShmooContent用于绘制Shmoo图的内容。首先检查网站数量是否为0，如果是则直接返回。然后根据是否处于合并模式进行相应的处理。如果处于合并模式，首先计算合并数据，然后检查网格大小和合并结果的大小是否匹配，如果不匹配则返回。接下来创建字体和画笔对象，设置文本颜色和背景模式。然后遍历每个网格，并根据合并结果的值设置相应的颜色，绘制矩形和文本。最后恢复原来的字体对象。

函数DrawSearchContent用于绘制搜索图的内容。首先检查网格大小和所选DUT的范围，如果不满足条件则直接返回。然后根据序列类型选择相应的绘制方式。如果是X-First类型，则遍历每个数据点，根据原点的位置计算坐标，并根据左右结果的值选择相应的颜色，绘制矩形。如果是Y-First类型，则也是类似的操作，只是计算坐标的方式不同。



函数DrawSearchContent用于绘制搜索内容，接收一个CDC*类型的指针参数pDC，表示绘图设备的上下文。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，m_SelDut在有效范围内），则执行绘图操作。否则，函数提前返回。

接下来，定义了一些用于绘制图形的画刷（CBrush）对象，分别代表通过（brPass）、失败（brFail）、绿色（brGreen）和红色（brRed）。

根据条件判断和计算，使用SelectObject方法选择不同的画刷对象，并调用Rectangle方法绘制矩形图形。具体绘制的形状和颜色根据不同的条件分支来确定。

函数DrawCurrentSearchResult用于绘制当前的搜索结果，接收一个DBL_POING类型的引用参数dbl_point，表示搜索结果的坐标和状态。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，m_SelDut在有效范围内），则执行绘图操作。否则，函数提前返回。

与上一个函数类似，根据条件判断和计算，使用SelectObject方法选择不同的画刷对象，并调用Rectangle方法绘制矩形图形。

函数CalculateMergeData用于计算合并后的数据。

首先创建了一个大小为m_nX*m_nY的整型向量m_vMergeResult，并初始化所有元素为0。

然后，通过遍历m_dblPoint中的数据，根据条件进行计数操作，将计数结果存储在m_vMergeResult中。

函数StoreAssumeData用于存储假设数据。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，坐标在有效范围内），则执行数据存储和绘图操作。

根据传入的数据参数和循环遍历的当前位置，创建一个SHMOODATA对象shm，并设置其坐标和结果。

接着，根据m_dut数组的位运算，判断当前位置的m_Data中的数据是否需要存储。

根据数据的结果值，选择合适的画刷对象，并使用SelectObject方法选择画刷对象，绘制矩形图形。

函数StoreData用于存储数据。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，坐标在有效范围内，并且传入.

Print()函数用于打印Shmoo图形，它的主要步骤如下：

创建字体对象并设置字体属性。
创建打印对话框，并显示对话框，获取打印设备上下文（hDC）。
如果打印设备上下文不存在，则返回。
创建设备上下文对象（CDC）并将其附加到打印设备上下文。
开始打印文档，并开始打印页面。
选择之前创建的字体对象。
设置地图模式和窗口、视口的大小。
根据绘图类型（m_PlotType）选择绘制Shmoo内容或搜索内容。
绘制编程值。
恢复原始字体对象。
结束打印页面和文档。
释放设备上下文对象。
分离设备上下文和打印设备上下文。
删除设备上下文对象。
OnShmoo()函数是一个消息处理函数，用于处理Shmoo消息。它接收WPARAM和LPARAM参数，其中WPARAM参数传递了一个指向数据的指针，LPARAM参数没有使用。函数根据消息的类型执行不同的操作，包括错误消息、全局变量、范围、Shmoo数据、结束Shmoo、假设结果、旧的xy值、单元定义和保存结果文件等。

具体的操作包括：

错误消息：通过SendMessage发送错误消息给主窗口。
全局变量：从字符串中解析出各种全局变量的值。
范围：解析字符串并清除数据，设置新的范围，并调用CalRange()、Reset()和Invalidate()进行重新绘制。
Shmoo数据：将数据存储到内部数据结构中，并调用DrawProgrammedValue()和Invalidate()重新绘制。
结束Shmoo：重新绘制并发送消息给父窗口和主窗口。
假设结果：将假设数据存储到内部数据结构中。
旧的xy值：从字符串中解析出原始xy值，并重新绘制。
单元定义：从字符串中解析出xstop和ystop，并调用SetUnit()设置单位。
保存结果文件：将结果保存到文件。
其他消息类型：不执行任何操作。
这些函数是CShmooControl类的成员函数，用于处理Shmoo图形控件的打印和消息处理相关的功能。

OnLButtonDown：鼠标左键按下事件处理函数。根据鼠标点击的位置计算出对应的数据点的索引，并根据当前的显示模式（PF mode、Fail Count、Fail Address）设置要显示的信息，并在窗口上绘制出对应的文本。
OnLButtonUp：鼠标左键释放事件处理函数。根据鼠标释放的位置确定选择的数据点的索引。
OnMouseMove：鼠标移动事件处理函数。根据鼠标的移动绘制出一个矩形框，并在窗口上绘制出该矩形框。
OnMenuShmoo：响应菜单项"Shmoo"的函数。向父窗口发送一个自定义消息UWM_MENU_SHMOO。
SetUnit：设置单位函数。根据传入的字符串参数设置X轴、Y轴、Z轴的单位。
OnRButtonDown：鼠标右键按下事件处理函数。根据鼠标点击的位置显示一个设置菜单。
OnSettingProgramPoint：响应设置菜单中的"Setting"菜单项的函数。根据点击的位置确定选择的数据点的索引，并根据该索引设置新的数据点的值。
SetPlotType：设置绘图类型的函数。传入一个整数参数来设置绘图类型。
GetPlotType：获取当前绘图类型的函数。返回一个整数值表示当前的绘图类型。
make_search_test_data：生成搜索测试数据的函数。可能是用于生成一些测试数据以进行搜索相关的功能测试。
```

### ShmooExecDlg.h

```markdown
该代码定义了一个名为CShmooExecDlg的对话框类，它是从CDialog类派生而来的。

代码中的主要成员函数包括：

构造函数 CShmooExecDlg：用于创建对话框实例，并初始化一些成员变量。
析构函数 ~CShmooExecDlg：用于清理资源。
DoDataExchange：用于数据的传递和验证。
OnInitDialog：对话框初始化的处理函数。
OnBnClickedOk：当用户单击对话框上的确定按钮时触发的处理函数。
OnBnClickedButtonMdut07、OnBnClickedButtonMdut815、OnBnClickedButtonMdut1623、OnBnClickedButtonMdut2431：当用户单击相应的按钮时触发的处理函数。
OnBnClickedCheckDut1：当用户勾选或取消勾选DUT 1时触发的处理函数。
该类还包含一些成员变量，用于存储对话框的状态和数据。其中包括：

m_nTestDUT：存储测试DUT的数组。
m_strMeasSignal：存储测量信号的字符串。
m_bStepByStep：表示是否逐步执行的布尔值。
m_nAlgorythm：存储算法的整数值。
此外，代码还定义了一些消息映射函数，用于处理对话框中的控件事件，如按钮点击和复选框勾选等。

总体而言，该代码实现了一个用于显示和设置Shmoo执行参数的对话框，包含了一些按钮、复选框和文本框等控件，用于与用户交互获取参数。

```

### ShmooExecDlg.cpp

```markdowm
这段代码是实现了 CShmooExecDlg 类的成员函数的定义，包括构造函数、析构函数、数据交换函数和消息映射函数。

构造函数 CShmooExecDlg::CShmooExecDlg 初始化了类的成员变量 m_nAlgorythm、m_strMeasSignal 和 m_bStepByStep。

数据交换函数 CShmooExecDlg::DoDataExchange 使用宏 DDX_Text 和 DDX_Check 将对话框上的文本框和复选框控件与类的成员变量进行关联。

消息映射函数 BEGIN_MESSAGE_MAP 和 ON_BN_CLICKED 定义了对话框中控件事件的响应函数，包括按钮点击事件和复选框勾选事件。

函数 CShmooExecDlg::OnInitDialog 在对话框初始化时被调用，根据条件设置对话框上的控件状态。根据变量 IS_JOBLOADED 的值，如果已加载作业，会根据 gxShared->TotalSite 的值来设置对应的复选框和按钮的状态。

函数 CShmooExecDlg::OnBnClickedButtonMdut07、OnBnClickedButtonMdut815、OnBnClickedButtonMdut1623、OnBnClickedButtonMdut2431 分别响应对应按钮的点击事件，根据 m_nAlgorythm 的值对一组复选框进行勾选或取消勾选。

函数 CShmooExecDlg::OnBnClickedOk 响应确定按钮的点击事件，将对话框中的选中状态更新到 m_nTestDUT 数组中，然后调用 OnOK 函数。

函数 CShmooExecDlg::OnBnClickedCheckDut1 响应复选框勾选事件，根据选中的复选框的ID，将其他复选框的勾选状态取消，并将当前复选框勾选。

这些函数的具体实现逻辑根据业务需求和对话框中控件的交互逻辑而定，上述代码片段提供了对这些函数的框架和大致思路的理解。
```

### ShmooWindow.h

```markdown
这段代码定义了一个名为 CShmooWindow 的类，该类是从 CWindowDialog 类派生而来，并包含了一些成员变量和函数。

CShmooWindow 类的构造函数和析构函数用于创建和销毁对象。

CShmooWindow 类包含了许多成员函数，用于实现各种功能，例如连接和断开连接、调整控件大小、加载和卸载页面、暂停页面、启用和禁用项目等。这些函数根据具体的业务需求来实现对话框的交互逻辑。

CShmooWindow 类的私有成员变量包括布尔型变量 m_bAlwaysOnTop 和图标句柄 m_hIcon，以及其他用于存储设置数据的变量。

CShmooWindow 类还定义了一些私有函数，用于读取和保存轴设置信息、将数据转换为参数形式、设置不同的模式等。

CShmooWindow 类还包含一些消息响应函数，例如窗口命令、绘图、鼠标拖动图标等。这些函数根据消息的类型和具体需求来实现相应的功能。

最后，CShmooWindow 类的消息映射函数 DECLARE_MESSAGE_MAP 声明了该类的消息映射表，用于将消息与相应的消息处理函数关联起来。

总体而言，这段代码定义了一个用于控制 Shmoo 窗口的类 CShmooWindow，其中包含了与窗口交互、控件操作、消息处理等相关的函数和成员变量。
```

### ShmooWindow.cpp

```markdown
#include：包含所需的头文件。
IMPLEMENT_DYNAMIC：用于实现动态创建对话框类的宏。
CShmooWindow::CShmooWindow：构造函数，用于初始化成员变量。
CShmooWindow::~CShmooWindow：析构函数。
CShmooWindow::DoDataExchange：用于在对话框和成员变量之间进行数据交换。
CShmooWindow::OnInitDialog：初始化对话框，包括设置图标、工具栏、菜单、控件等。
CShmooWindow::OnDestroy：对话框销毁时的处理，包括保存对话框位置。
CShmooWindow::OnSysCommand：处理系统菜单命令，包括处理"Always on top"选项。
CShmooWindow::OnPaint：绘制对话框。
CShmooWindow::OnQueryDragIcon：获取拖动对话框时的光标图标。
CShmooWindow::PreTranslateMessage：在消息被翻译并分派之前的预处理，用于处理按键消息。
CShmooWindow::OnSize：处理对话框大小改变事件，调整控件大小。
CShmooWindow::PostNcDestroy：在窗口销毁后的处理，发送消息给父窗口。
CShmooWindow::OnSetFocus：处理对话框获取焦点事件。
CShmooWindow::OnClose：关闭对话框的处理，保存对话框状态。
CShmooWindow::ResizeControls：调整控件的大小和位置。
CShmooWindow::Connect：连接到GUI。
CShmooWindow::Disconnect：断开与GUI的连接。
CShmooWindow::LoadedPage：加载页面时的处理。
CShmooWindow::UnloadedPage：卸载页面时的处理。
CShmooWindow::PausedPage：暂停页面时的处理。
CShmooWindow::OnUpdateAlwaysOnTop：更新"Always on top"菜单项的状态。
CShmooWindow::OnUpdatePlotShmoo：更新"Plot Shmoo"按钮的状态。
CShmooWindow::OnUpdateStopShmoo：更新"Stop Shmoo"按钮的状态。
CShmooWindow::OnAlwaysOnTop：处理"Always on top"菜单项的点击事件，切换窗口置顶状态。
OnBnClickedButtonPrint(): 在点击“打印”按钮时调用m_Shmoo对象的Print()方法。m_Shmoo是该窗口类的成员变量。

OnBnClickedButtonSave(): 在点击“保存”按钮时调用m_Shmoo对象的Save()方法。首先创建一个文件对话框，然后获取所选择的文件名，并检查该文件是否已存在。如果文件已存在，弹出一个消息框询问用户是否覆盖原有文件，如果用户选择是，则调用m_Shmoo的Save()方法保存数据。

OnShmooMessage(): 该函数是在接收到自定义消息时调用的。根据传递的参数进行条件判断，当flag为0时表示Shmoo测试开始，为1时表示Shmoo测试结束。在Shmoo测试开始时，禁用IDC_BUTTON_SHMOO按钮，然后获取X轴和Y轴的一些信息并保存在m_AxisData数组中，最后在下拉菜单m_comboTDUT中添加一些选项并设置默认选择项。在Shmoo测试结束时，填充当前选项卡的信息并在m_comboTDUT中添加一个合并选项。

OnShmooMenu(): 该函数是在接收到自定义菜单消息时调用的。根据选定的Shmoo图区域的起始和结束索引计算相应的起始和结束数值，并更新X轴和Y轴的一些信息。然后根据当前选项卡的选择，调用FillTabInfo()函数填充选项卡信息，并调用OnBnClickedButtonShmoo()函数。

SaveCurrentTabInfo(): 将当前选项卡中的设置信息保存到m_AxisData数组中。

OnTcnSelchangeTabAxis(): 该函数在选项卡切换时被调用。调用SaveCurrentTabInfo()函数保存当前选项卡的设置信息，根据选项卡的选择填充相应的信息。

OnCbnDropdownComboXsetname(): 在下拉列表m_comboXSetName展开时调用。获取charsetup文件夹下的所有json文件名，并将它们添加到下拉列表中。

OnCbnDropdownComboYsetname(): 在下拉列表m_comboYSetName展开时调用。获取charsetup文件夹下的所有json文件名，并将它们添加到下拉列表中。

ReadAxisSet(): 根据给定的轴索引和名称，读取相应的设置信息。

FillTabInfo(int naxis): 根据给定的轴索引 naxis 填充选项卡的信息。根据当前轴的类型，选择相应的模式并设置控件的状态。

OnCbnSelchangeComboXsetname(): 当 X 轴设置名称的下拉列表发生变化时调用。根据所选名称，调用 ReadAxisSet() 函数读取相应的设置信息，并根据当前选项卡的选择调用 FillTabInfo() 函数填充选项卡信息。

OnCbnSelchangeComboYsetname(): 当 Y 轴设置名称的下拉列表发生变化时调用。根据所选名称，调用 ReadAxisSet() 函数读取相应的设置信息，并根据当前选项卡的选择调用 FillTabInfo() 函数填充选项卡信息。

OnCbnSelchangeComboType(): 当类型选择的下拉列表发生变化时调用。根据所选的类型，调用相应的模式设置函数，并根据选择的类型重置时间设置的下拉列表内容。

OnCbnSelchangeComboSelectDut(): 当选择DUT的下拉列表发生变化时调用。根据所选的选项，调用 m_Shmoo 对象的相应方法。

OnBnClickedButtonCondition(): 当"ButtonCondition"按钮被点击时调用。首先检查是否加载了作业，如果没有加载则直接返回。然后保存当前选项卡的信息。接下来，根据当前轴的选择，获取X轴或Y轴设置名称的下拉列表中的当前选择，并将其存储在name变量中。然后弹出一个对话框，要求用户输入一个标题名字，并将用户输入的内容存储在name变量中。然后构造一个文件路径，并将一些设置信息保存到一个JSON文件中。如果写入文件失败，则弹出一个消息框显示错误信息。

SetTimesetMode(): 设置时间设置模式。首先检查是否加载了作业，如果没有加载则直接返回。然后重置时间设置的下拉列表内容，并根据当前共享数据中的时间组信息，填充时间设置的下拉列表。

SetACVariableMode(): 设置交流变量模式。首先检查是否加载了作业，如果没有加载则直接返回。然后根据当前共享数据中的模式执行跟踪信息，填充时间设置的下拉列表。

SetDCVariableMode(): 设置直流变量模式。首先检查是否加载了作业，如果没有加载则直接返回。然后重置时间设置的下拉列表内容，并根据当前共享数据中的直流执行跟踪信息，填充时间设置的下拉列表。

OnCbnSelchangeComboAlgorithmShmoo(): 当"ComboAlgorithmShmoo"下拉框的选择改变时调用。首先通过UpdateData(TRUE)将用户界面的数据更新到对应的成员变量中。然后根据当前选择的算法类型进行不同的操作。如果选择的算法类型为2，则将m_nMode和m_nSkip设置为0，并禁用"ComboModeShmoo"和"EditSkip"控件。否则，启用这两个控件。最后通过UpdateData(FALSE)将成员变量的值更新到用户界面上。
```


#pragma once
#define MARGINCONTROL_CLASSNAME    _T("MFCMarginControlCtrl")  // Window class name

#include "CMarginControl.h"

#include <vector>
#include <string>
#include <UXDataStructure.h>
#include <QPainter>


class MarginData
{
public:
	MarginData(int sitecount, unsigned int* tdut, int indivisual);
	~MarginData();
	void SetSignalName(const char* signame, const char* settingsignal);
	void SetItemName(const TCHAR* item);
	void SetRangeData(double start, double end, double step);
	QString GetValue(double value);
	void SetRectangle(const QRect& rect);
	void OffsetRectangle(int height);
	void SetProgrammedValue(double value);
	QRect GetRectangle() const;
	void Draw(QPainter* pDC);
	void DrawMark(QPainter* pDC, const QPoint& pt);
	void DrawBackground(QPainter* pDC);
	void StoreData(QPainter* pDC, int x, const char* p);
	BOOL IsContains(const QPoint& pt);
	void SaveData(FILE* out);
	void SetSelectedDut(int dut);
	void SetUnit(const QString& strUnit, double div);
	void ChangeProgramValue(const QPoint& pt, const char* szTimeset, const char* szWfc, const char* szEdge);

private:
	QString _TsName;
	QString _SigSetting;
	QRect   _GlobalRc;
	int     _SelectedDut;
	int     _w;
	int     _num;
	TCHAR   _unit[5];
	TCHAR   _szItem[MAX_NAME_SIZE];
	double  _unitdiv;
	double  _begin;
	double  _end;
	double  _interval;
	double  _OrgValue;
	int     m_nSiteCount;
	int     _indivisual;
	vector<char>  _result[32];
	unsigned int*        _pTestDut;
};









# Qt MFC

## Qt中的调用代码:

```C++
connect(ui.actionMargin, &QAction::triggered, this, [=](){
	if(!cMarginWindow){
		cMarginWindow = new CMarginWindow();
		MFCWindow mfcWindow;
		mfcWindow.setMFCInstance((CWnd*)cMarginWindow);
		mfcWindow.raise();
		mfcWindow.show();
	}
	else{
		MFCWindow mfcWindow;
		mfcWindow.setMFCInstance((CWnd*)cMarginWindow);
		mfcWindow.raise();
		mfcWindow.show();
	}
});
```

## 自定义中间类

头文件 MFCViewClass.h

```C++
#pragma once

#include <WinSock2.h>
#include <afxwin.h>

#include <QtWinExtras/QtWin>
#include <QtGui/QWindow>
#include <QVBoxLayout>


class MFCWidget : public QWidget
{
public:
    MFCWidget(QWidget *parent = nullptr);

    void setMFCInstance(CWnd* mfcInstance);

    ~MFCWidget();

private:
    CWnd* m_mfcInstance;
};

// 在Qt的窗口中使用MFCWidget
class MFCWindow : public QWidget
{
public:
    MFCWindow(QWidget *parent = nullptr);

    void setMFCInstance(CWnd* mfcInstance);
private:
    MFCWidget *m_mfcWidget;
};
```

源文件 MFCViewClass.cpp

```C++
#include "MFCViewClass.h"

MFCWidget::MFCWidget(QWidget *parent)
    : QWidget(parent), m_mfcInstance(nullptr)
{
    QVBoxLayout *layout = new QVBoxLayout(this);
    layout->setContentsMargins(0, 0, 0, 0);
    setLayout(layout);
}

void MFCWidget::setMFCInstance(CWnd* mfcInstance)
{
    m_mfcInstance = mfcInstance;

    if (m_mfcInstance)
    {
        // 设置 MFC 实例的父窗口为 QWidget
        m_mfcInstance->SetParent(CWnd::FromHandle((HWND)winId()));
        CRect rect(0,0,640,480);
        GetClientRect((HWND)winId(), &rect);
        m_mfcInstance->MoveWindow(rect);
        m_mfcInstance->ShowWindow(SW_SHOW);
    }
}

MFCWidget::~MFCWidget()
{
}


MFCWindow::MFCWindow(QWidget *parent)
    : QWidget(parent), m_mfcWidget(nullptr)
{
    QVBoxLayout *layout = new QVBoxLayout(this);
    layout->setContentsMargins(0, 0, 0, 0);
    setLayout(layout);
}

void MFCWindow::setMFCInstance(CWnd* mfcInstance)
{
    m_mfcWidget = new MFCWidget(this);
    m_mfcWidget->setMFCInstance(mfcInstance);
    layout()->addWidget(m_mfcWidget);
}
```



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