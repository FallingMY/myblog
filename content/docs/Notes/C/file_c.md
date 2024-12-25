---
# type: docs 
title: 文件
date: 2024-12-23T08:55:34+08:00
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
author: 'Falling_MY'
images: []
---

C语言文件有两种储存类型  

文本文件
> 储存量大
> 读写慢
> 便于对字符操作
> 存储格式：ASCII

二进制文件
> 储存小
> 速度快
> 便于存储中间结果
> 存储格式：二进制

## 文件系统

C语言中使用的磁盘文件系统有两大类  

### 缓冲文件系统

特点是系统自动将文件的一部分内容读入内存，再由内存对文件进行操作。

### 非缓冲文件系统

特点是系统直接对文件进行操作。

## 文件的使用

在使用文件前，必须包含头文件`<stdio.h>`

ANSI C为正在使用的每个文件分配了一个文件系统，该文件系统包含文件的有关信息。

类型为`FILE`的变量称为文件指针变量。

文件结构体如下：
```c
typedef struct{
    short level;//缓冲区的当前级别
    unsigned flags;//文件状态标志
    char fd;//文件描述符
    unsigned char hold;//未使用
    short bsize;//缓冲区的大小
    unsigned char *buffer;//数据传输缓冲区的位置
    unsigned ar;//文件的当前读写位置
    unsigned istemp;//临时文件指示器
    short token;//用于有效性检查
}FILE;
```

文件使用示例：
```c    
FILE *fp = fopen("path\\file.txt", "w");
if (fp == NULL) {
    printf("文件打开失败\n");
} else {
    printf("文件打开成功\n");
    fprintf(fp, "Hello, world!\n");
    fclose(fp);
}
```

文件打开时使用的路径可以使用相对路径或绝对路径。  
相对路径：从当前工作目录开始的路径。灵活，可移植性好  
绝对路径：从根目录开始的路径。方便，可移植性差  

### 文件打开模式

| 模式 | 功能 |
| --- | --- |
| r | 打开一个已有的文本文件，允许读取文件 |
| w | 打开一个文本文件，允许写入文件。如果文件不存在，则会创建一个新文件。如果文件已存在，则会截断文件，即删除文件中的所有内容 |
| a | 打开一个文本文件，以追加模式写入文件。如果文件不存在，则会创建一个新文件。如果文件已存在，则会将写入的数据追加到文件的末尾 |
| r+ | 打开一个文本文件，允许读写文件 |
| w+ | 打开一个文本文件，允许读写文件。如果文件不存在，则会创建一个新文件。如果文件已存在，则会截断文件，即删除文件中的所有内容 |
| a+ | 打开一个文本文件，允许读写文件。如果文件不存在，则会创建一个新文件。如果文件已存在，则会将写入的数据追加到文件的末尾 |
| rb | 打开一个二进制文件，允许读取文件 |

### 文件操作

| 函数 | 功能 |
| --- | --- |
| fopen | 打开一个文件 |
| fclose | 关闭一个文件 |
| fgetc | 从文件中读取一个字符 |
| fputc | 向文件中写入一个字符 |
| fgets | 从文件中读取一个字符串 |
| fputs | 向文件中写入一个字符串 |
| fprintf | 向文件中格式化写入数据 |
| fscanf | 从文件中格式化读取数据 |
| feof | 检测文件是否到达末尾 |

#### fgets函数
`fgets`函数的原型如下：

```c
char *fgets(char *str, int n, FILE *stream);
```

`fgets`函数的作用是从指定的文件中读取至多n-1个字符，并将其存储在指定的字符数组中。读取字符直到遇见回车符或者EOF为止。

#### fputs函数
`fputs`函数的原型如下：

```c
int fputs(char *str, FILE *stream);
```

`fputs`函数的作用是将指定的字符串写入指定的文件中。

#### fread函数
`fread`函数的原型如下：
```c
size_t fread(void *ptr, size_t size, size_t count, FILE *stream);
```
`fread`函数的作用是从指定的文件中读取指定数量的数据块，并将其存储在指定的内存地址中。

#### fwrite函数
`fwrite`函数的原型如下：
```c
size_t fwrite(void *ptr, size_t size, size_t count, FILE *stream);
```
`fwrite`函数的作用是将指定的数据块写入指定的文件中。


#### fgets,fputs和fread,fwrite的区别

`fgets`和`fputs`函数用于处理文本文件，而`fread`和`fwrite`函数用于处理二进制文件。

`fgets`和`fputs`函数每次处理一个字符，而`fread`和`fwrite`函数每次处理一个数据块。

- 数据块：数据块是指一组连续的内存单元，它们的大小由`size`参数指定。

`fgets`和`fputs`函数每次处理一个字符时，需要手动添加换行符，而`fread`和`fwrite`函数每次处理一个数据块时，不需要手动添加换行符。



---
现在我们可以来解释一些程序中main函数的参数设计了
```c
int main(int argc, char *argv[]) {
    // 程序代码
    return 0;
}
``` 
`argc`是一个整数，它表示命令行参数的数量。`argv`是一个指向字符串的指针数组，它包含了命令行参数的值。

例如，假设我们在命令行中输入了以下命令：
```bash
./program arg1 -i arg2 --v arg3
```
那么，`argc`的值将为4，`argv`的值将为：
```c
{
    "program",
    "arg1",
    "-i",
    "arg2",
    "--v",
    "arg3",
    NULL
}
```
### 文件指针的定位

stdio.h库中提供了用于文件指针定位的函数，它们的作用是将文件指针移动到指定的位置。函数如下：
| 函数 | 功能 | 函数原型 |
| --- | --- | --- |
| fseek | 将文件指针移动到指定的位置 | int fseek(FILE *stream, long offset, int whence); |
| ftell | 获取文件指针当前的位置 | long ftell(FILE *stream); |
| rewind | 将文件指针移动到文件的开头 | void rewind(FILE *stream); |

#### fseek函数
`fseek`函数的作用是将文件指针移动到指定的位置。

`fseek`函数的whence参数有以下取值：
- 0 SEEK_SET：将文件指针移动到文件的开头，然后向文件的末尾移动offset个字节
- 1 SEEK_CUR：将文件指针移动到当前位置，然后向文件的末尾移动offset个字节
- 2 SEEK_END：将文件指针移动到文件的末尾，然后向文件的开头移动offset个字节