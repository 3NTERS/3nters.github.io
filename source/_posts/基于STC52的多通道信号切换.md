---
title: 基于STC52的多通道信号切换装置
date: 2022-11-07 20:44:36
categories: 嵌入式项目
tags: 嵌入式
---

# 前言
有好一段时间没有更新博客了，还有前面的一些坑也没填...（虽然没人看😶‍🌫️）
解释一下就是最近考试和实习的任务有点多，今天要写的就是其中的一个项目，没什么技术含量但一些细节和流程值得以后做项目参考。

# 项目背景
>大概是不同频率电刺激小老鼠之类（?）

# 项目要求

如下
![X3eYQ.png](https://c2.im5i.com/2022/11/07/X3eYQ.png)
![X3zp3.png](https://c2.im5i.com/2022/11/07/X3zp3.png)

# 分析需求
## 硬件
- 双路信号切换
> 双路继电器、`stc52`芯片

- 网口输出
> `RJ45`网口

- `5V`供电
> `micro-B`或电池

- 继电器驱动
> `NPN`三极管 

- 调试显示
> `OLED`

## 软件

- 三组三模式切换
>双标志判断
>定时中断

# 原理图
![X3ajO.png](https://c2.im5i.com/2022/11/07/X3ajO.png)

# AD预览图
![X34eR.png](https://c2.im5i.com/2022/11/07/X34eR.png)

# 源代码

{% hideToggle 点击以查看代码 %}

```c
#include<reg52.h>

typedef unsigned int u16;
typedef unsigned char u8;
sbit MODE_1=P3^0;
sbit MODE_2=P3^1;
sbit MODE_3=P3^2;
sbit MODE_4=P3^3;
sbit OUT_1=P1^1;
sbit OUT_2=P1^2;
sbit OUT_3=P1^3;
sbit OUT_4=P1^4;
sbit beep=P2^3;
u16 flag= -1;
u16 t_flag=-1;
u16 k=0;//默认100s

//11.0592MHZ延时，n=1为1ms	
void delay(u16 n){
	u16 i,y;
	for(i=n;i>0;i--)
		for(y=114;y>0;y--);
}
void Timer0Init(){
	TMOD|=0X01;//选择为定时器 0 模式， 工作方式 1， 仅用 TR0 打开启动。
	TH0=0XFC; //给定时器赋初值， 定时 1ms
	TL0=0X18;
	ET0=1;//打开定时器 0 中断允许
	EA=1;//打开总中断
	TR0=1;//打开定时器
}


void main(){
	Timer0Init();
	while(1){

		delay(100);//延时消抖
		if(MODE_4==1){
			delay(100);//延时消抖
			if(MODE_1==0)
				flag=1;			
			else if(MODE_2==0)
				flag=2;
			else if(MODE_3==0)
				flag=3;
		}
		if(MODE_4==0){
			delay(100);//延时消抖
			if(MODE_1==0)
				t_flag=1;
			else if(MODE_2==0)
				t_flag=2;
			else if(MODE_3==0)
				t_flag=3;
			}
	
	}
}

//定时中断0中断函数
void Timer0() interrupt 1{
	u16 count;
	TH0=0XFC; //给定时器赋初值， 定时 1ms
	TL0=0X18;
	count++;
	//if(count>=100){
	
	
		if(t_flag==1){
			k=500;
		}
		else if(t_flag==2){
			k=1000;
		}
		else if(t_flag==3){
			k=1500;
		}
		else
			k=0;
		if(flag==1){
			OUT_1=1;
			delay(k);
			OUT_1=0;
			OUT_2=1;
			delay(k);
			OUT_2=0;
		}
		else if(flag==2){
			OUT_1=1;
			delay(k);
			OUT_1=0;
			OUT_2=1;
			delay(k);
			OUT_2=0;
			OUT_3=1;
			delay(k);
			OUT_3=0;
		}
		else if(flag==3){
			OUT_1=1;
			delay(k);
			OUT_1=0;
			OUT_2=1;
			delay(k);
			OUT_2=0;
			OUT_3=1;
			delay(k);
			OUT_3=0;
			OUT_4=1;
			delay(k);
			OUT_4=0;
		}
		else{
//			OUT_1=0;
//			OUT_2=0;
//			OUT_3=0;
//			OUT_4=0;
			OUT_1=0;
			OUT_2=0;
			OUT_3=0;
			OUT_4=0;
		}
//	}
//	beep=~beep;
}

```

{% endhideToggle %}


# 设计过程

## 原理图设计
修改历史
- 去掉按键处的上拉电阻和电压，直接`IO`口
  >调试时一按开关电压全拉低，单片机不供电。

- 加入`OLED`方便调试，船型开关改拨动开关
  >调试的时候才发现没有指示,真有够蠢的。硕大的船型开关和`7x9`的电路板格格不入...

- `PNP`三极管改`NPN`三极管
  >设计的是单片机供电输出高电平驱动继电器,集电极为继电器低，发射极为地，基极为`IO`口，b>e时ce导通。然而，使用`PNP`的结果是b>e时be导通。

    ⚠️⚠️封装和引脚映射一定要好好检查！！！被这个坑了好多次，要看技术手册上实际的引脚对应的极（不然就会出现需要三极管正反倒焊的骚操作）。

- 修改`RJ45`封装

## 元器件选型
原则：
所选的元器件要是被广泛使用验证过的，尽量少使用冷 门、偏门芯片，减少开发风险。

- 继电器
  >国产`HFD/5`信号继电器，一开始买成24V，白花一百多块钱！！(╯▔皿▔)╯

- 三极管
  >`SOT23`封装`S8015`

- 网口
  >`RJ45`淘宝任意款（不带灯）

- 按键
  >`6x6`贴片


## 电路板设计
修改历史
- 板子大小从10x10->7x9
  >开始对高压电路的特性不太熟悉便尽可能的把元件分地很开，但师父说没必要就改小了。

- 整体布局优化
  > 主要就是`MCU`的方向改变，让`IO`口尽量和输出对应，不用飞太远的线过去。


# 总结
- 绘制电路图的时候封装最好是自己画，用别人的也要和自己的元器件技术手册参数对照一下，免得犯和我一样的低级错误。
- 调试过程中出了很多设计时没想到的问题，用师父的话来说就是“大方向正确，小错误不断”。
- 很多错误都是粗心大意造成的，细节方面主要是技术手册还没看透，还有一些基本原理和常识没有，例如英制封装和公制封装的对应、51最小系统板原理图、三极管的运用等。
- 感谢师父和学长的耐心教导，瑞思拜。
- 项目完结后再补充终版。

