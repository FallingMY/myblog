---
# type: docs 
title: 队列
date: 2024-11-23T09:56:09+08:00
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

# 定义

与栈不同，队列的两端都允许插入和删除操作。

**队列(Queue)** 是只允许一端进行插入操作，而另一端进行删除操作的线性表。  

> 相关术语  
> 队头：允许删除的一端  
> 队尾：允许插入的一端  
> 空队列：无元素  

> 特点：先进先出  

## 基本操作

- InitQueue(&Q) 初始化队列, 构造一个空队列Q
- DestroyQueue(&Q) 销毁队列, 释放Q占用的内存空间
- EnQueue(&Q, x) 入队, 若队列Q未满, 则将x加入, 使之成为新的队尾
- DeQueue(&Q, &x) 出队, 若队列Q非空, 则删除Q的队头元素, 并用x返回
- GetHead(Q, &x) 读队头元素, 若队列Q非空, 则将队头元素赋值给x
- QueueEmpty(Q) 判断队列是否为空, 若队列Q为空, 则返回true, 否则返回false

## 队列的顺序实现

```C
//Power by Marscode
#include <stdio.h>
#include <stdlib.h>
#define MAXSIZE 10


typedef struct{
    ElemType data[MAXSIZE];
    int front, rear;//队头指针和队尾指针
}SqQueue;

//使用
void testQueue(){
    SqQueue Q;
    //.......
}

//初始化时，队头和队尾指针都指向0
void InitQueue(SqQueue &Q){
    Q.front = Q.rear = 0;
}

//销毁
void DestroyQueue(SqQueue &Q){
    free(Q.data);
    Q.front = Q.rear = 0;
}

bool GetHead(SqQueue Q, ElemType &x){
    if(Q.front == Q.rear){
        return false;
    }//队空，报错
    
    x = Q.data[Q.front];//出队
    return true;
}

//入队
bool EnQueue(SqQueue &Q, ElemType x){
    if ((Q.rear + 1) % MAXSIZE == Q.front){
        return false;
    }//队满，报错

    Q.data[Q.rear] = x;//入队
    Q.rear = (Q.rear + 1) % MAXSIZE;//队尾指针加1
    return true;
}

//出队
bool DeQueue(SqQueue &Q, ElemType &x){
    if(Q.front == Q.rear){
        return false;
    }//队空，报错

    x = Q.data[Q.front];//出队
    Q.front = (Q.front + 1) % MAXSIZE;//队头指针加1
    //和栈的出栈相似，不需要真的删除元素，只需要逻辑上的出队
    return true;
}
```

## 循环队列

```C
Q.data[Q.rear] = x;//入队
Q.rear = (Q.rear + 1) % MAXSIZE;//队尾指针加1
```

## 链式队列

链式队列分为两种：带头指针和不带头指针。
- 带头指针的链式队列，头指针指向头结点，头结点的指针指向队头元素，尾结点的指针指向队尾元素。
- 不带头指针的链式队列，头指针和尾指针都指向队头元素。

```C
//Power by Marscode
#include <stdio.h>
#include <stdlib.h>
#define MAXSIZE 100 

typedef struct LinkNode{
    ElemType data;
    struct LinkNode *next;
}LinkNode;

typedef struct{
    LinkNode *front, *rear;//队头指针和队尾指针
}LinkQueue;

//初始化
void InitQueue(LinkQueue &Q){
    Q.front = Q.rear = (LinkNode *)malloc(sizeof(LinkNode));
    Q.front->next = NULL;
}

void EnQueue(LinkQueue &Q, ElemType x){
    //申请新结点
    LinkNode *s = (LinkNode *)malloc(sizeof(LinkNode));
    s->data = x;
    s->next = NULL;

    Q.rear->next = s;//新结点插入到队尾
    Q.rear = s;//队尾指针指向新结点
    return true;
}

//出队
bool DeQueue(LinkQueue &Q, ElemType &x){
    if(Q.front == Q.rear){
        return false;
    }//队空，报错

    LinkNode *p = Q.front->next;//p指向队头元素

    x = p->data;//出队

    Q.front->next = p->next;//头结点的指针指向队头元素的下一个元素

    if(Q.rear == p){//如果队头元素是队尾元素
        Q.rear = Q.front;//队尾指针指向头结点
    }
    free(p);
    return true;
}

//销毁
void DestroyQueue(LinkQueue &Q){
    while(Q.front!= NULL){
        Q.rear = Q.front->next;//队尾指针指向头结点的下一个元素
        free(Q.front);//释放头结点
        Q.front = Q.rear;//队头指针指向队尾指针
    }
}
```

