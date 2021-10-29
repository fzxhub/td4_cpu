# 把玩DT4_CPU

## 背景

发现一个十分精简的4bit的CPU，觉得不错，就来试玩一下。

[原项目仓库](https://github.com/wuxx/TD4-4BIT-CPU)

[本项目仓库](https://github.com/fzxhub/td4_cpu)

## 说明

1. 该CPU是4bit的。寻址空间是16，每次寻址1字节，最大寻址是16Bytes。
2. 使用同步二进制计数器74HC161作为A、B、OUT、PC寄存器。
3. 使用4bit全加器74HC283作为运算器。
4. 74HC154进行程序数据寻址，最大16Bytes。
5. 还有数据选择器、其他逻辑门构成控制器部分。
6. 多谐振荡器作为时钟信号

## 接口说明

1. 输入接口拨码开关4bit。
2. 输出接口LED 4bit。
3. 程序存储拨码开关16Bytes。

## 指令说明

程序存储拨码高4bit是指令，低四位作为数据存储。

| 指令（汇编） | COM | 说明 |
| :---: | :---: | :---: |
| ADD A,Im | 0000 | 将A寄存器中数据与立即数相加 |
| MOV A,B | 0001 | 将B寄存器中数据存入A寄存器中 |
| IN A | 0010 | 将输入存入A寄存器中 |
| MOV A,Im | 0011 | 将立即数中数据存入A寄存器中 |
| MOV B,A | 0100 | 将A寄存器中数据存入B寄存器中 |
| ADD B,Im | 0101 | 将B寄存器中数据与立即数相加 |
| IN B | 0110 | 将输入存入B寄存器中 |
| MOV B,Im | 0111 | 将立即数中数据存入B寄存器中 |
| OUT B | 1001 | 将B寄存器中数据输出 |
| OUT Im | 1011 | 将立即数输出 |
| JNC Im | 1110 | 当C寄存器溢出 |
| JMP Im | 1111 | 跳转到立即数所指向的地址开始执行 |

