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