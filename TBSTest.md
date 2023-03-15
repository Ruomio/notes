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
