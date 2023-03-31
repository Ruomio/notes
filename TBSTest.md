# First Day

## T800A/B/C/D

slot:6 

数字板卡：HDM800 64ch B/C：一个pogo D：两个pogo； 可用来供电，精度差于电源板卡，但优于控制板卡

电源板卡：SMU10E 32ch	两个pogo

控制板卡：UTP128	128ch	一对二，两个pogo， 可以用来供电，但精度不高，差于数字板卡

模拟板卡：ADU8 4ch 引脚较少

### B

slot:10

数字板卡：HDM800 64ch

电源板卡：SMU10E 32ch

控制板卡：UT128	128ch

### C

slot:16

数字板卡：HDM800 64ch

电源板卡：SMU10E 32ch

控制板卡：UT128	128ch

### D

slot:16

数字板卡：HDM800 128ch

电源板卡：SMU10E 96ch

控制板卡：UT128	256ch

## DIB母板 DUT子版

套接到pogo上交流信号

## 校准板卡 

DC、AC、CUL

### SVM LVM 向量内存

存放pattern

## GUI AITEST 测试软件 （仅有Windows环境）

# 业务流程
## 1.Signals/Group
将芯片针脚命名类型 (In, Out, InOut, Supply等)
命名组: 组名(变量名) = {Singal 集合 ,支持 +,- 运算符}
## 2.DCExec
包含DCLevel,DCLevel包含DCSPec 和 Category&Selctor
```
STIL 1.0;
Include "PinLevel.stil"

DCExec "level_3v"{
	Category		"level_3V";
	Selector		"Seletcot_Typ";
	DCLevels		"PinLevel";
}

DCExec "level_3v"{
	Category		"level_4.5V";
	Selector		"Seletcot_Typ";
	DCLevels		"PinLevel";
}

DCExec "level_3v"{
	Category		"level_5.5V";
	Selector		"Seletcot_Typ";
	DCLevels		"PinLevel";
}

DCExec "level_5.5_min_max"{
	Category		"level_5.5V";
	Selector		"Seletcot_min_max";
	DCLevels		"PinLevel";
}
```
### DCLevel,PinLevel
```
STIL 1.0;
Include "Signals.stil"
Include "DCSpec.stil"

DCLevels "CON"{

	VCC{
		VForce		'VCC';
		IRange		'0.25';
		Delay		'0.005';
	}

	all{
		VIL			'VIL';	
		VIH			'VIH';
		VOL			'VOL';
		VOH			'VOH';
		IOH			'IOH';
		IOL			'IOL';
	}
}
```
## 3.DCSeqence

## 4.PatternExec
## 5. Test Items
## 6.Test Flow


# 集成电路测试
## 流程
设计->制造->封装-> 可靠性-> 出入场-> 应用
## 数字电路测试流程
Continuity->Gross Func. Test->IDD->DC->Functional->AC->AP.
## 分类
Wafer Test:测试晶圆
Package Test:晶圆被切割成弗里德电路单元，每个单元封装出来后仍需要测试，也称Final Test， FT测试、成品测试等。
Quality Assurance Test:质量保证测试，抽样检测确保pass的产品没有不合格的产品。
Device Characterization:器件特性描述，决定器件工作参数范围的极限值。
Pre/Post Burn In:在器件Burn-in 之前和之后进行的测试，用于验证老化过程没有引起一些参数的漂移，清楚潜在失效的芯片。
Miliary Test:军品测试，执行更为严格的老化测试标准，如扩大温服范围，对测试结果进行归档。
Incoming Inspection:收获检验，终端客户为保证购买芯片质量在应用之前的检测。
Assembly Verification:封装验证，用于检验芯片经过了封装过程中是否仍然完好并检测正确性，通常在FT测试一并实现。
Failure Analysis:失效分析，分析失效芯片的故障以确定失效原因，找到影响良率的关键因素，提高芯片的可靠性。
## 按测试目的分类
验证测试：确保设计的正确性
制造测试：保证制造的良品率
老化测试：保证器件的可靠性
入厂测试：保证器件的一致性
## 按测试内容分类
参数测试：只要测试器件的性能
功能测试：主要测试器件的功能
结构测试：主要测试器件的结构
## 按照制造阶段分类
晶圆测试：Chip Probing
成品测试：Final Test
质保测试：QA/QC Test
## 按产品类型分类
数字信号集成电路测试
模拟信号集成电路测试
混合信号集成电路测试
数字存储集成电路测试
SoC集成电路测试
## 测试机和治具
探针台（Prober）：量产晶圆的取放和对准
载板/Pogo Tower：用于固定和连接测试机和探针卡
探针卡（Probe Card）：PCB电路板，上边安装有探针，用于将测试机台各种资源连接到被测晶片的pad上，同时提供测试所需要的外围电路。PCB可采用通用公版或定制专板
探针（Probe）：安装在探针卡上，一头连接探针卡通道，另一头扎到裸片对应的pad上，实现信号和电源的连接。常用的有悬臂针和垂直针。

# DC测试
直流电测试。
## 开短路（OS）测试
IO pins OS, Power Pin OS
### OS测试定义和目的
Open-Short Test 也称为Continuity Test，用以确认在器件测试时所有的信号引脚与测试系统相应的通道在电性能上完成了连接
## IDD测试
### Gross IDD
电源到地之间的电流大小
### Static/Dynmic IDD
测量工作以及非工作状态下电流，确认芯片功耗
### IDDQ测试
通过数字信号设置到多种状态，分别测试各个状态下的静态电流
## VOH/VOL
VIL/VIH VOL/VOH
## Leakage
IIL/IIH, IOZL/IOZH
## IOS测试
输出短路电流

# Functional Test
验证DUT是否正确实现所设计的逻辑功能，需要生成测试向量或真值表义检测DUT中的错误。测试向量和测试时序组成功能测试的核心
## 基础术语
+ output Mask:输出屏蔽，让测试通道的输出比较功能打开或关闭的方法
+ Output Sampling:输出采样，在功能测试中，DUT的输出信号在周期内的某个时间点被评估的过程
+ Test Pattern:测试向量，是逻辑功能的输入输出状态的描述。
+ + Signal Format: 信号格式，PE驱动电路提供的输入信号波形。
# AC测试


# 程序执行顺序
load->sot->function->eot->unload
sot: start on test:test之前初始化
eot: end on test: 清理