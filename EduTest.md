# EduTest

vs 2010版本问题，咱们不都是用的2015吗

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


### RTDFViewer 
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



### 测试项写入办法
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

