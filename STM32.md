# STM32
## 常见术语
VDD: 电源正极 高电平
VSS: 电源负极 低电平


## 位操作
P置位第n位: P |= (1 << n)
Q清零第n位: Q &= ~(1 << n)

> 内存映射是对地址的封装，直接操作内存也可以实现。

## 引脚分类
电源
晶振IO
BOOT IO
复位IO
以上IO组成的系统称最小系统

## RCC
1. RCC_CR
2. RCC_CFGR
3. RCC_CIR
4. RCC_APB2RSTR
5. RCC_APB1RSTR
6. RCC_AHBENR
7. RCC_AHBENR
8. RCC_AHB2ENR
9. RCC_AHB1ENR
10. RCC_BDCR
11. RCC_CSR

## GPIO: 
专用总线:I2C, SPI, SDIO, FSMC, DCMI
普通总线: 蜂鸣器, LED, 按键
### 寄存器描述
1. CRL 配置低寄存器
2. CRH 配置高寄存器
3. ODR 输入数据寄存器
4. IDR 输入数据寄存器
5. BSRR 位设置/清楚寄存器
6. BRR 位清除寄存器
7. LCKR 配置锁定寄存器

```txt
1. 模拟输入: 不经过施密特触发器(TTL)直接接入
2. 浮空输入: 即高阻输入,相当于电压表。但外界没有输入时，容易受到外界电磁干扰.
3. 下拉输入: 无输入信号时端口电平被拉到低电平
4. 上拉输入: 无输入信号时端口电平被拉到高电平
5. 开漏输出: 只能输出低电平，只有接上拉电阻才能输出1。好处是更换外部电源即可以更改输出电源。
6. 推挽输出: 可以输出高低电平,高电平由VDD决定,低电平由VSS决定。由两个三极管互补信号控制,电流大,驱动能力强.
7. 复用开漏输出: 数据来自片上外设,而普通开漏输出来自输出数据寄存器(ODR)数据
8. 复用推挽输出: 同上

```



# st-link 烧录程序
## 常用命令
> st-flash reset

> st-info --probe

> st-flash read out.bin 0x8000000 0x40000

> st-flash write xxx.bin 0x8000000



# Arm-none-eabi-gcc

## 二进制复制

`arm-none-eabi-objcopy -O binary xxx.elf xxx.bin`

