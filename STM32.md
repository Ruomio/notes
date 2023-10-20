# STM32
## 常见术语
VDD: 电源正极 高电平
VSS: 电源负极 低电平


## 位操作
P置位第n位: P |= (1 << n)
Q清零第n位: Q &= ~(1 << n)
R反转第n位: R ^= (1 << n)
### 位带操作
转换: (Addr & 0xF0000000)+0x02000000+((Addr & 0x00ffffff)<<5) + (n<<2)
     

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



# PlatforIO

## openocd权限问题

`sudo chown -R papillon:users /dev/stlinkv2_4  `





# GDB stlink调试程序

1. arm-none-eabi-as -mthumb  -mcpu=cortex-m3 -g xxx.s -o xxx.o        `-mthumb (16位指令集)`
2. arm-none-eabi-ld xxx.o -T xxx.ld -o xxx.elf
3. 先编译程序下载到板子上
4. 运行`st-util`命令来打开 gdbserver, 并记住端口号 ${port}
5. arm-none-eabi-gdb xx.elf
6. target remote *: ${port} 
7. stepi , next, finish, list , continue ，- (图形界面)，info break, display, bt (查看堆栈),  jump <linenum> 跳转到第几行， x (打印地址的值) 等命令



# 串口工具

minicom

`sudo minicom -s` 配置参数

`sudo minicom` 连接串口


# ARM 汇编
## 寄存器

> cortex-M 系列使用armv7架构，使用thumb 指令集(T32)

模式: User, FIQ, IRQ, ABT, SVC, UND, MON, HYP
* 1. R0-R12通用寄存器，放通用数据，32bit
* 2. 各个模式R0-R12与User模式是共享的（除了 FIQ的R8-R12), PC, CPSR 是共享的
* 3. USER模式没有SPSR
> SP 栈指针，存储栈地址
> LR 链接寄存器，存储子程序返回地址
> PC 程序计数器
> APSR/CPSR 应用程序状态寄存器/当前程序状态寄存器
