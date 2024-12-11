---
# type: docs 
title: 结构体与共用体
date: 2024-12-11T09:54:05+08:00
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

## 结构体

> 为什么要使用结构体？  
> 变量：内置数据类型，但是相对独立，缺乏联系  
> 数组：可以存储多个变量，但是变量类型必须一致  
> 想要存储类型不同但是互相之间关联的数据  

### 结构体的声明

```c
struct student{
    char name[20];
    char sex;
    int age;
    char job[40];
    char address[40];
};
```
#### 结构体声明的一般形式：
```c
struct 结构体名{  
    数据类型 成员变量名1;  
    ...
};
```
#### 结构体变量声明的一般形式：
```c
struct 结构体名 变量名;
```
#### 也可以结合结构体声明和变量声明：
```c
struct student{
    char name[20];
    char sex;
    ...
}stu1, stu2;
```
stu1的内存大小是其所有成员变量的总大小，stu2的内存大小也是其所有成员变量的总大小。  
并且stu1和stu2是两个结构体变量，它们在内存中是独立的。

#### 结构体类型的嵌套定义：
```c
// birthday是student的成员变量
struct student{
    char name[20];
    char sex;
    struct birthday{
        int year;
        int month;
        int day;
    };
};

//先声明birthday，再声明student
struct birthday{
    int year;
    int month;
    int day;
};
struct student{
    char name[20];
    char sex;
    struct birthday birthday;
};

//结构体的自引用
struct student{
    char name[20];
    char sex;
    struct student *next;//指向下一个结点的指针
};
```
### 结构体变量的赋值
```c
struct student{
    char name[20];
    char sex;
    int age;
    char job[40];
    long num;
    char address[40];
};

//方法1:程序内赋值
int main(){
    struct student stu;
    strcpy(stu.name,"张三");
    stu.sex='男';
    stu.age=20;
    strcpy(stu.job,"学生");
    stu.num=123456789;
    strcpy(stu.address,"北京");
}

//方法2:从键盘输入
int main(){
    struct student stu;
    printf("请输入姓名:");
    scanf("%s",stu.name);
    printf("请输入性别:");
    scanf(" %c",&stu.sex);
    printf("请输入年龄:");
    scanf("%d",&stu.age);
    printf("请输入工作:");
    scanf("%s",stu.job);
    printf("请输入学号:");
    scanf("%d",&stu.num);
    printf("请输入家庭住址:");
    scanf("%s",stu.address);
}
```
同时，`stu1=stu2`是合法的，其结果是将`stu2`中所有元素的值赋给`stu1`  

需要注意的是，结构体变量之间不能直接比较，只能比较其元素  

### 结构体数组

结构体数组的定义的形式：
```c
struct student{
    char name[20];
    int num;
    char address[20];
    ...
};
struct student stu[5];
for (int i = 0; i < 5; i++){
    scanf("%s %d %s",stu[i].name,&stu[i].num,stu[i].address);
}
```

*~~似乎少了什么东西……~~*

### 指向结构体变量的指针

指针变量指向任一与指针变量类型一致的变量存储区域，同样可以定义指针变量来指向结构体变量  

定义指针变量p1,p2，可用如下方式指向结构体类型变量：  
`p1=&stu1;`  
`p2=`  

指向结构体变量的指针访问结构体成员：
`结构体指针变量名 -> 成员变量名`：  
`p1 -> name`  
或  
`(*结构体指针变量名).成员变量名`：  
`(*p1).name`  

### 结构体与函数

C语言允许使用结构体作为函数的参数，将结构体成员逐个复制到形参中  

将实参结构体变量成员的值赋给形参结构体变量的成员，是单向的值传递。后续对形参的修改，不会影响实参。  

函数的返回值也可以是结构体类型  

指向结构体的指针变量作为函数参数，是将实参结构体数组或结构体变量的起始地址传递给形参指针变量，这样可以提高函数的效率。