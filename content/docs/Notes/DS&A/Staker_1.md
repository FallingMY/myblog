---
# type: docs 
title: 栈
date: 2024-11-23T08:27:33+08:00
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series: 竞赛培训课笔记
categories: []
tags: []
images: []
authors:
  - Falling_MY
---

2024.11.23
这里是大一的我。
自己目前还不是很能理解栈和队列的相关知识，只是简单的做一下竞赛课程的笔记。  
不是很了解，所以我就先把我目前学到的东西记录下来，以后再慢慢补充。  
我们在以后的数据结构再见吧！  

由于老师上课的速度很快，所以难免笔记会有疏漏，并且代码大部分由Marscode生成。
如果你发现有什么问题或者有什么建议，欢迎在评论区留言。  

Btw，如果你觉的这篇文章对你有帮助，不妨点个赞吧⬇️
{{< emoji-button >}}

---

# 栈(stack)

## 定义

线性表是具有相同数据结构的n个元素的有限序列  

栈是只允许一段进行插入或删除操作的线性表  

> 相关术语
> 栈顶：允许插入和删除的一段
> 栈底：不允许操作的一段
> 空栈：无元素

特点：先进后出  

## 基本操作

### 线性表

- 初始化 构造一个空的线性表，分配内存空间
- 销毁 释放线性表所占用的内存空间
- 插入 在指定位置插入元素
- 删除 删除指定位置的元素，并返回值
- 按值查找 查找具有给定关键字值的元素
- 按位查找 

### 栈

- 初始化
- 销毁
- 进栈 Push(&s, x) 
- 出栈 Pull(&s, &x) 
- 查 获取栈顶元素

## 顺序栈的实现

### 定义

```C
//Powered By Marscode
#define MAXSIZE 10
typedef struct{
    ElemType data[MAXSIZE];
    int top;//栈顶指针，指向栈顶元素
}SqStack;

//使用
void testStack(){
    SqStack Q;
    //.......
}

void Init(SqStack &s){
    s.top = -1;
}// 初始化

bool Push(SqStack &s, ElemType &x){
    if(s.top == MAXSIZE - 1){
        return false;
    }//栈满，报错

    s.data[++s.top] = x;//指针先加1，再入栈
    return true;
}// 入栈

bool Pop(SqStack &s, ElemType &x){
    if(s.top == -1){
        return false;
    }//栈空，报错
    //考虑算法的时候要首先考虑异常情况

    x = s.data[s.top--];//先出栈，指针再减1
    //只需要逻辑上的出栈，无需真的删除元素
    //函数运行结束之后会自动释放内存空间
    return true;
}// 出栈

bool GetTop(SqStack &s, ElemType &x){
    if(s.top == -1){
        return false;
    }//栈空，报错

    x = s.data[s.top];
    return true;
}// 取栈顶元素

bool StackEmpty(SqStack &s){
    if(s.top == -1){
        return true;
    }else{
        return false;
    }
}// 判断栈是否为空
```
### 栈的链式存储

```C
//链栈的结点结构、栈类型定义
typedef struct StackNode{
    ElemType data;
    struct StackNode *next;
}StackNode, *LinkStack;
```

---

## 例题1

> 题目描述：
> 给定一个长度为N的整数数列，输出每个数左边第一个比它小的数，如果不存在则输出-1。
> 输入格式：
> 第一行包含整数N，表示数列长度。
> 第二行包含N个整数，表示整数数列。
> 输出格式：
> 共一行，包含N个整数，其中第i个数表示第i个数的左边第一个比它小的数，如果不存在则输出-1。
> 输入样例：
> 5
> 3 4 2 7 5
> 输出样例：
> -1 3 -1 2 2
 
### 思路: 
- 从前往后遍历数组
- 用栈维护一个单调递增的序列
- 如果栈顶元素大于当前元素，则弹出栈顶元素，直到栈顶元素小于当前元素或者栈为空
- 如果栈为空，则当前元素左边没有比它小的元素，输出-1
- 如果栈不为空，则栈顶元素就是当前元素左边第一个比它小的元素，输出栈顶元素
- 将当前元素入栈

```C
// Powered By Marscode
//参考代码
#include <stdio.h>
#define MAXN 1000010
int n, top, stk[MAXN]; // 定义变量 n 表示数列长度，top 表示栈顶指针，stk 数组用于存储栈中的元素
int main(){
    scanf("%d", &n); // 读入数列长度
    for(int i = 0; i < n; i++){
        int x;
        scanf("%d", &x); // 读入当前数
        while(top && stk[top] >= x){ // 如果栈顶元素大于等于当前数，弹出栈顶元素
            top--;
        }
        if(top){ // 如果栈不为空
            printf("%d ", stk[top]); // 输出栈顶元素，即当前数左边第一个比它小的数
        }else{
            printf("-1 "); // 如果栈为空，输出 -1
        }
        stk[++top] = x; // 将当前数入栈
    }
    return 0;
}

```

## 例题2

> 题目描述：
> 斐波那契数(通常用F(n)表示)形成的序列称为斐波那契数列，该数列由0和1开始，后面的每一项数字都是前面两项数字的和。也就是：
> F(0) = 0，F(1) = 1
> F(n) = F(n - 1) + F(n - 2)，其中n > 1
> 给定一个整数n，请计算F(n)。

### 思路：
如果我们不使用递归的方式，直接使用栈，那又该如何求解呢？  

思路非常的简单。比如说我们求F(4),我们需要一个栈来存储F(1)和F(2)。然后我们依次取出栈顶元素，计算F(3)，然后将F(3)入栈。以此类推，直到我们计算出F(4)为止。  

```C
// Powered By Marscode
// 参考代码
#include <stdio.h>
#define MAXN 1000010
int n, top, stk[MAXN]; // 定义变量 n 表示数列长度，top 表示栈顶指针，stk 数组用于存储栈中的元素
int main(){
    scanf("%d", &n); // 读入数列长度
    if (n <= 0){
        printf("0\n"); // 如果 n <= 0，输出 0
    }
    if (n == 1 || n == 2){
        printf("1\n"); // 如果 n == 1，输出 1
    }
    top = 0; // 初始化栈顶指针
    stk[++top] = 1; // 将 F(1) 入栈
    stk[++top] = 1; // 将 F(2) 入栈
    for(int i = 3; i <= n; i++){ // 从 F(3) 开始计算
        int a = stk[top - 1]; // 取出栈顶元素
        int b = stk[top]; // 取出栈顶元素
        stk[++top] = a + b; // 将 F(i) 入栈
    }
    printf("%d\n", stk[top]); // 输出栈顶元素，即 F(n)
    return 0;
}
```

## 例题3

> 题目描述：
> 在编程当中，我们经常需要处理括号匹配的问题。例如，在编写一个编译器的时候，我们需要检查括号是否匹配。括号匹配指的是，对于一个给定的括号序列，其中的括号必须是成对出现的，并且每个右括号都必须与其对应的左括号匹配。
> 样例输入：
> {([])}
> 样例输出：
> YES

### 思路

如果字符是左括号，则入栈；如果字符是右括号，则出栈。如果出栈的字符不是对应的左括号，则不匹配。如果栈为空，则匹配。
```C
// Powered By Marscode
// 参考代码
#include <stdio.h>
#include <string.h>
#define MAXN 1000010
int n, top, stk[MAXN]; // 定义变量 n 表示数列长度，top 表示栈顶指针，stk 数组用于存储栈中的元素
int main(){
    char s[MAXN]; // 定义字符串 s
    scanf("%s", s); // 读入字符串
    n = strlen(s); // 计算字符串长度
    top = 0; // 初始化栈顶指针
    for(int i = 0; i < n; i++){ // 遍历字符串
        if(s[i] == '(' || s[i] == '[' || s[i] == '{'){ // 如果是左括号
            stk[++top] = s[i]; // 将左括号入栈
        }else{ // 如果是右括号
            if(top == 0){ // 如果栈为空
                printf("NO\n"); // 输出 NO
                return 0; // 结束程序
            }
            char c = stk[top--]; // 取出栈顶元素
            if(s[i] == ')' && c!= '('){ // 如果右括号和左括号不匹配
                printf("NO\n"); // 输出 NO
                return 0; // 结束程序
            }
            if(s[i] == ']' && c!= '['){ // 如果右括号和左括号不匹配
                printf("NO\n"); // 输出 NO
                return 0; // 结束程序
            }
            if(s[i] == '}' && c!= '{'){ // 如果右括号和左括号不匹配
                printf("NO\n"); // 输出 NO
                return 0; // 结束程序
            }
        }
    }
    if(top == 0){ // 如果栈为空
        printf("YES\n"); // 输出 YES
    }else{ // 如果栈不为空
        printf("NO\n"); // 输出 NO
    }
    return 0;
}
```

