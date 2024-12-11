---
# type: docs 
title: 指针
date: 2024-11-18T08:08:06+08:00
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series: '课堂笔记'
categories: []
tags: []
images: []
---

> C语言能处理一类非常特殊的数据——内存地址（常量）  

如果这篇文章有帮到你的话，不妨点个赞吧  
{{< emoji-button >}}

## 引入

计算机内部有很多储存单元，每个储存单位都用唯一的地址编号（表示为一个整数加以区别），简称为**地址**  

或者说  

内存中每个字节都有一个编号——**地址**

指针使程序的不同部分能共享数据（**地址唯一性**）  

## 指针

指针自身的是一个变量，内容为地址变量。指针自身被称为指针变量（也作指针）。  
指针变量指向目标变量。  

```C
char *p,x;
x = "A";
p = &x;
```

`*`为取目标运算  
`&`为取地址运算  

### 空指针

```C
int *p = 0;
int p = null;
```

定义了一个空指针  
指向的目标变量为*null*  

#### 作用

> 任何变量一旦定义就有值  

在不知道指针的指向时，将其定义为空指针  

### 无类型指针

```C
void *p;
```

void意思为该指针的目标类型当前未知  
在知道目标类型之后，可用强制类型转换将空类型指针转为整形指针或字符型指针  

```C
(int*) p;
(char*) p;
```

## 例

### 数字交换

```C
#include<stdio.h>

void swap(int *p1,int *p2){
    int tmp;
    tmp = *p1;//储存p1目标变量值[a]
    *p1 = *p2;//将p2的目标变量值[b]赋值给p1
    *p2 = tmp;//将p1的原目标值[a]赋值给p2
}//将a,b地址的变量进行交换操作

int main (){
    int a, b;
    scanf("%d %d", &a, &b);
    swap(&a, &b);
    printf("%d %d\n", a, b);
}
```
## 指针与函数

指针可以是函数的参数也可以是函数的返回值  

如果返回值是地址/指针的话，函数声明时也要加上`*`
```C
int *fun(int *x, int *y);
```

> 注意：应当注意当函数返回地址时，地址对应的空间是否被释放  

### 数组指针作函数参数

```C
int max(int x[], int n);
//其中x[]传入的实际上是指针，也可以写作下面这样
int max(int *x, int n);
```
数组指针作为函数参数中实参和形参的对应关系：  
> 若`int a[3][4]; int (*p1)[4]=a; int *p2=a[0]`

|形参|实参|
|-|-|
|数组定义`int x[][4]`|数组名`a`|
|指针变量`int (*q)[4]`|数组名`a`|
|数组定义`int x[][4]`|指针变量`p1`|
|指针变量`int (*q)[4]`|指针变量`p1`|
|指针变量`int *q`|指针变量`p2`|

> 题外话：**二维数组定义时第二个参数不可省略**
> `a[n][m]`,`a[][m]`都是正确的  
> `a[][]`,`a[n][]`是错误的  
> 原因是我们应该告诉程序行指针每一行有多少数字，每次移动应该跨越多少  

## 指针和数组

**数组名**就是数组在内存存储区域的首地址（常称为数组的指针），并且为常量  

指针变量可以用于存储变量的地址，也可存放数组的指针或数组元素的指针  

由于数组是连续占用内存，所以可以使用指针+位移来访问整个数组  

用一个指针变量来存储这个数组的首地址；数组和数组元素的引用，也可以通过使用指针的方式进行间接访问  

```C
int arr[10];
int* p;
p = a;//等价于p = &a[0]

```
### 指针间接访问数组元素  
- `p+i`和`a+i`都可以表示数组元素`a[i]`的**地址**  
- 间接访问`*(p+i)`和`*(a+i)`就表示为数组的各元素即等效于`a[i]`  
- `*(p+i)`$\lrArr$`p[i]`$\lrArr$`a[i]`$\lrArr$`*(a+i)`  

### 指针移动注意事项  
- 必须指向连续储存空间  
- 移动到的储存区域必须有意义  

## 指针和二维数组

二维数组在内存当中其实是一维的  
拆分地来看，对于一个二维数组，可以用一维数组代替地理解。  
不同的拆分方法诞生了不同的访问方法  

###  列地址

> +1跨过一列

例如：`a[0][0]`可以视为一维数组`a[0]`的第1个值  
`a[i]+j`$\lrArr$`&a[i][0]+j`$\lrArr$`&a[i][j]`  

故可以使用`*(a[i]+j)`访问`a[i][j]`  

### 行地址

> +1跨过一整行

如果将行看作一个数列，则可以先通过行进行访问  

**思考过程如下：**

假设我们要访问二维数组`arr[N][N]`中的某个元素`arr[i][j]`  
-  首先我们要取到指定行
   -  将行看为一个一维数组`arr[N]`
   -  取到第i个元素的地址`arr+i`
   -  取第i个元素，即到达第i行`*(arr+i)`$\lrArr$`arr[i]`$\lrArr$`&arr[i][0]`(二级指针)
   -  此时也正好为第i行的第一个元素的地址
-  接下来开始取到指定元素
   -  进行列指针位移`*(arr+i)+j`
   -  取元素`*(*(arr+i)+j)`$\lrArr$`arr[i][j]`

### 二维数组的行指针

变量声明：`数组的数据类型 (*指针变量名)[m];`  
意义：声明指针指向m列的二维数组，或指向有m个元素的一维数组  
（可以理解为m表示了指针每次移动的步长）  

```C
int a[3][4];
int (*p)[4];

//赋值
p=a;
p=&a[0];//等价
```

## 指针与字符数组

实现字符串引用有两种办法：
- 字符数组
- 指向字符串的指针

其余的感觉和数组差不多…………  
注意一下`\0`就好了

### 字符数组和字符指针处理字符串的比较

- 储存上的区别
  - 字符数组由若干元素组成，每个元素储存一个字符
  - 字符指针变量中储存的是字符串的首地址
- 传递上的区别
  - 字符数组名作为函数参数时，传递的是整个数组
  - 字符指针变量作为函数参数时，传递的是字符串的首地址

```C
//使用数组形式
char str[] = "Hello World!";//不定义数组长度
char str[13] = "Hello World!";//定义数组长度
//使用指针形式
char *p = "Hello World!";
```

## 指针数组

数组元素是指针的数组

### 定义形式
类型标识 *数组名[数组长度]
```C
char *p[10];
```
由于[]的优先级高于*，所以先和p结合，形成一个数组形式  再由char*说明这是一个指针数组，它有10个指针类型的数组元素。这里执行`p+1`时，p要跨过10个`char*`的长度。

注意区分：
`char *p[10]`表示这是一个指针数组，它有10个指针类型的数组元素，其首元素的地址为`p[0]`，类型为`char *`即是一个字符指针。  
`char (*p)[10]`表示这是一个数组指针，它指向一个一维数组，这个一维数组的长度为10，类型为`char *`，即一个字符指针。  

指针数组用的最多的是“字符串型指针数组”，利用字符指针数组可以指向多个长度不同的字符串，使字符串的处理更加方便灵活，节省空间。  

使用指针数组排序时不需要移动字符串，只需要移动指针  

```C
//对已排好序的字符指针数组进行指定字符串的查找
//二分查找
#include<stdio.h>
#include<string.h>
#include<stdlib.h>

/*
测试数据：
Amanda
Bob
Chris
Follow
Jill
William

Follow
*/

int bianrysearch(char *p[],char *x,int n){
    //p为字符串指针数组，x为要查找的字符串，n为数组长度
    int mid,low=0,high=n-1;
    while(low<=high)
    {
        mid = (low+high)/2;
        if(strcmp(p[mid],x)==0)
            return mid;
        else if(strcmp(p[mid],x)>0)
            high = mid-1;
        else
            low = mid+1;
    }
    return -1;
}
int main(){
    //char *name[]={"Amanda","Bob","Chris","Follow","Jill","William"};
    char *name[6];
    for(int i=0;i<6;i++)
        name[i] = (char *)malloc(10*sizeof(char));
    printf("请输入6个字符串：\n");
    for(int i=0;i<6;i++)
        gets(name[i]);
    int i,index;
    char findname[10];
    printf("请输入要查找的内容：\n");
    gets(findname);
    index = bianrysearch(name,findname,6);
    if(index==-1)
        printf("没有找到\n");
    else
        printf("在第%d个位置\n",index+1);
    for(int i=0;i<6;i++)
        free(name[i]);//释放内存空间
    return 0;
}


```

## 指针的地址分配

当定义指针变量时，系统会自动分配一个地址给指针变量  

在stdlib.h中提供了两个函数malloc()和free()用来分配和释放内存  
函数原型为：
```C
void *malloc(unsigned int size);
void free(void *p);
```

`malloc()`用以向操作系统申请size个字节的内存空间，并返回该内存空间的首地址。需要注意的是，size的值应和要指向的变量类型的字节数一致。  
`free()`用来释放malloc()函数所申请的内存空间。  

例：
```C
//两个字符串的交换
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
    char *p1,*p2;
    p1 = (char *)malloc(100);
    p2 = (char *)malloc(100);
    gets(p1);
    gets(p2);
    printf("交换前：\n");
    printf("p1=%s\np2=%s\n",p1,p2);
    char *temp;
    temp = (char *)malloc(100);
    strcpy(temp,p1);
    strcpy(p1,p2);
    strcpy(p2,temp);
    printf("交换后：\n");
    printf("p1=%s\np2=%s\n",p1,p2);
    free(p1);
    free(p2);
    free(temp);
    return 0;
}

```

## 指向指针的指针变量

> 概念：
> 如果一个指针变量存放的又是另一个指针变量的地址，则称这个指针变量为指向指针的指针变量。  
> 这个指针也被称为二级指针变量。

例如：
```C
int a = 100;
int *p = &a;//p存放a的地址
int **pp = &p;//pp存放p的地址
printf("%d\n",**pp);//输出100
printf("%d\n",*pp);//输出p的地址
```

## 指向函数的指针变量

