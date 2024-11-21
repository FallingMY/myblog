---
# type: docs 
title: Java数据类型（八种基本数据类型 + 四种引用数据类型）
date: 2024-07-05T11:34:47+08:00
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
  - HelpDocs
categories:
tags: 
  - HelpDocs
  - Java
authors:
  - CSDN_user
images: []
--- 

1、位（bit）：  
又名 比特位，表示二进制位，是计算中内部数据储存的最小单位。一个二进制位只能表示0和1两种状态。

2、字节（byte）：  
是计算机中处理数据的基本单位。一个字节等于八位（1Byte = 8bit）

3、字（word）：  
计算机进行数据处理时，一次存取、加工和传送的数据长度。在常见的计算机编码格式下，一个字等于两个字节（十六位）（1word = 2Byte = 16bit）

##### 一、JAVA中的数据类型分为两大类：

1、基本数据类型：整型、[浮点型](https://so.csdn.net/so/search?q=%E6%B5%AE%E7%82%B9%E5%9E%8B&spm=1001.2101.3001.7020)、字符型、布尔型  
整数类型 —— byte、short、int、long,  
浮点类型 —— float、double  
字符类型 —— char  
布尔类型 —— boolean  
2、引用数据类型：接口（interface）、数组（\[ \]）、类（class）。

##### 1.基本数据类型(八种)：

###### 1.1 整数类型

| 整型 | 占用字节空间大小 | 取值范围 | 默认值 |
| --- | --- | --- | --- |
| byte | 1字节 | \-128 ~ 127 | 0 |
| short | 2字节 | \-32768 ~ 32767 | 0 |
| int | 4字节 | \-2^31 ~ （2^31） - 1 | 0 |
| long | 8字节 | \-2^63 ~ （2^63） - 1 | 0L |

###### 1.2 浮点类型（小数）

| 浮点型 | 占用字节空间大小 | 取值范围 | 默认值 |
| --- | --- | --- | --- |
| float | 4字节 | 10^38 | 0.0F |
| double | 8字节 | 10^308 | 0.0 |

###### 1.3 字符类型

| 字符型 | 占用字节空间大小 | 取值范围 | 默认值 |
| --- | --- | --- | --- |
| char | 2字节 | 0 ~ 65535 | ‘\\u0’ |

###### 1.4 布尔类型

| 布尔型 | 占用字节空间大小 | 取值范围 | 默认值 |
| --- | --- | --- | --- |
| boolean | 视情况而定 | true、false | false |

##### 2.引用数据类型（三种）：

引用数据类型是建立在八大基本数据类型基础之上，包括数组、接口、类。引用数据类型是由用户自定义，用来限制其他数据类型。简单的说，除八大基本类型之外的所有数据类型，都为引用数据类型。  
所有引用类型的默认值都为 null 。

#### 二、数据类型转换：

转化从低级到高级：byte,short,char（三者同级）—> int —> long—> float —> double  
1、低级转换高级：自动类型转换  
2、高级转换低级：强制类型转换

**注意事项**  
1、强制类型转换过程中可能造成数据丢失；  
2、强制类型转换时要在需要转换的数据类型前加上 ()。  
例如：

```
public class Demo1 {
	public static void main(String[] args) {
		int intNumber = 10;
		float floatNumber = 3.4F;
		double doubleNumber = 6.18;
		
		// 低优先级类型数据 + 高优先级类型数据 ——> 结果会自动转换为高优先级数据。
		System.out.println("int + float = " + (intNumber + floatNumber));
		System.out.println("int + double = " + (intNumber + doubleNumber));
		
		System.out.println();
		// 将 int + double 所得到的值进行强制转转换，为int类型数据，造成数据精度丢失
		System.out.println("(强制类型转换) int + double = " + (int)(intNumber + doubleNumber));
		System.out.println("(强制类型转换) double = " + (int)doubleNumber);
	}
}
```

输出结果：

```javascript
int + float = 13.4
int + double = 16.18

(强制类型转换) int + double = 16
(强制类型转换) double = 6
```

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[Java技能树](https://edu.csdn.net/skill/java/?utm_source=csdn_ai_skill_tree_blog)[首页](https://edu.csdn.net/skill/java/?utm_source=csdn_ai_skill_tree_blog)[概览](https://edu.csdn.net/skill/java/?utm_source=csdn_ai_skill_tree_blog)147466 人正在系统学习中

本文转自 <https://blog.csdn.net/weixin_42428778/article/details/109603769>，如有侵权，请联系删除。