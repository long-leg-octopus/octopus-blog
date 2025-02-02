---
title: STM32G030系列_硬件设计指导
slug: stm32g030-seriesgrimal-design-guidance-z2pecbe
url: /post/stm32g030-seriesgrimal-design-guidance-z2pecbe.html
date: '2025-01-13 16:16:14+08:00'
lastmod: '2025-02-02 14:25:21+08:00'
tags:
  - 赢家设计指导
categories:
  - 硬件设计
keywords: 赢家设计指导
toc: true
isCJKLanguage: true
---

## 芯片选型

​![0](assets/0-20250113161631-92w8bli.png)​

## 硬件设计

### 1.1 电源部分

​![0](assets/0-20250113161631-utyszhl.png)​

官方提供的功耗数据：

​![0](assets/0-20250113161631-vi3obvm.png)​

​![0](assets/0-20250113161631-0aeah4r.png)​

电源拓扑图如下:

​![0](assets/0-20250113161631-9ekzzg6.png)​

### 1.2 时钟电路

|Power Pin|Pin Number|Design Reference|
| ---------------------| ------------| -----------------------------------|
|PC14-OSC32_IN/OSC32|2|外部高速时钟输入。VDD供电，8MHz。|
|PC15-OSC32_OUT|3|RTC时钟输出|

1、STM32G030提供高精度内部时钟，0℃-90℃范围内可达到±1%精度。常规应用无需外接晶振。

2、STM32G030K6T6系统高速时钟（HS）和低速时钟均可以采用内部提高或者外部提供。考虑到时钟的稳定性，尽量使用外部时钟。只有48脚 的封装（STM32G030C8T6） 才可以使用 HSE无源晶振。其它 SON8 TSSOP20 LQFQ32 HSE由于封装的限制，只能用有源晶振，并且是和OSC32引脚是共用的。

### 1.3 启动方式配置

支持3种启动方式

|启动模式|说明|
| ------------| ----------------------------------------------------------|
|主FLASH|从主闪存启动。<br />想要运行我们自己的程序就要选择这种方式|
|系统存储器|从系统存储区启动。<br />想要通过串口下载程序就要选择这种方式|
|嵌入式SRAM|SRAM启动，一般不用。|

具体配置如下，设计可采用纯软件方式启动。

​![0](assets/0-20250113161631-mj90v3i.png)​

### 1.4 SWD调试接口

SWD引脚如下，由于已经嵌入上拉和下拉电阻，因此无需添加外部电阻。

​![0](assets/0-20250113161631-3qqedhr.png)​

为了所有产品保持一致。SWD接口线序如下：

​![0](assets/0-20250113161631-iveimuy.png)​

‍

‍

2

‍

参考原理图：BSY1U-FAN-1901A101

参考链接：[STM32G0x0 Value line - Cost-effective Arm Cortex-M0+ MCUs - 意法半导体STMicroelectronics](https://www.st.com.cn/zh/microcontrollers-microprocessors/stm32g0x0-value-line.html)

                  [STM32G070KBT6最小系统板绘制和晶振配置、BOOT模式配置_stm32g0 boot-CSDN博客](https://blog.csdn.net/qq_48211392/article/details/135705593)

                  [STM32G0系列的启动配置与程序下载_stm32g0包-CSDN博客](https://blog.csdn.net/Naisu_kun/article/details/114018570#:~:text=System%20memory%20%E4%BB%8E%E7%B3%BB%E7%BB%9F%E5%AD%98%E5%82%A8%E5%8C%BA%E5%90%AF%E5%8A%A8%EF%BC%8C%E6%83%B3%E8%A6%81%E9%80%9A%E8%BF%87%E4%B8%B2%E5%8F%A3%E4%B8%8B%E8%BD%BD%E7%A8%8B%E5%BA%8F%E5%B0%B1%E8%A6%81%E9%80%89%E6%8B%A9%E8%BF%99%E7%A7%8D%E6%96%B9%E5%BC%8F%EF%BC%9B%20Embbeded%20SRAM%20%E4%BB%8E%E5%86%85%E5%AD%98%E5%90%AF%E5%8A%A8%EF%BC%9B%20STM32G0%E7%B3%BB%E5%88%97%E8%8A%AF%E7%89%87%E9%80%9A%E8%BF%87%E9%80%89%E9%A1%B9%E5%AD%97%E8%8A%82%EF%BC%88option%20byte%EF%BC%89%E4%B8%AD%E7%9A%84,nBOOT1%20%E3%80%81%20nBOOT_SEL%20%E3%80%81%20nBOOT0%20%E8%BF%99%E5%87%A0%E4%BD%8D%E5%8A%A0%E4%B8%8A%E5%A4%96%E9%83%A8%E7%9A%84%20BOOT0%20%E7%AE%A1%E8%84%9A%E7%9A%84%E7%94%B5%E5%B9%B3%E6%9D%A5%E7%A1%AE%E5%AE%9A%E5%90%AF%E5%8A%A8%E6%96%B9%E5%BC%8F%E3%80%82)

                  [为什么SWD烧录STM32时BOOT0脚要接高电平，否则SWD下载失败_如果reset给定的低电平的话,为什么swd接高电平也可以运行-CSDN博客](https://blog.csdn.net/RockHill_001/article/details/103198039)

‍
