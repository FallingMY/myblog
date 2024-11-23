---
# type: docs 
title: 串
date: 2024-11-23T11:39:07+08:00
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

串，及字符串，是由零个或多个字符组成的有限序列。一般记为：
$$ S = 'a_1a_2a_3...a_n' (n>0)$$

串是一种特殊的线性表，数据元素之间呈线性关系。
串的数据对象是**字符**的有限序列。

## 串的基本操作

- StrAssign(&T, chars) 赋值操作，把串T赋值为chars
- StrCopy(&T, S) 复制操作，把串S复制给串T
- StrEmpty(S) 判空操作，若S为空串，则返回true，否则返回false
- StrLength(S) 求串长，返回串S的元素个数
- ClearString(&S) 清空操作，将S清空
- DestroyString(&S) 销毁串，将串S销毁
- Concat(&T, S1, S2) 串联接，用T返回由S1和S2联接而成的新串
- SubString(&Sub, S, pos, len) 求子串，用Sub返回串S的第pos个字符起长度为len的子串
- Index(S, T, pos) 定位操作，若主串S中存在与串T值相同的子串，则返回它在主串S中第pos个字符之后第一次出现的位置，否则函数值为0
- StrCompare(S, T) 比较操作，若S>T，则返回值>0，若S=T，则返回值=0，若S<T，则返回值<0

## 串的存储结构

### 串的顺序存储结构

顺序存储都是一个字符串数组+串长度，分为
- 静态数组实现（定长顺序存储）： 栈区，数组长度固定
- 动态数组实现（堆分配存储）： 堆区，数组长度可变

char[0]一般不使用，从char[1]开始存储。
因为在C语言中，字符串是以'\0'结尾的，所以char[0]存储的是字符串的长度。

```C
//Power by Marscode
//静态数组实现：按预定义MAXLEN在栈区开辟储存区
#define MAXSIZE 255
typedef struct{
    char ch[MAXSIZE];
    int length;
}StringNode;
```
```C
//Power by Marscode
//动态数组实现：按串场在堆区开辟储存区，ch指向串的基地址，用完需要手动删除指针
typedef struct{
    char *ch;
    int length;
}HString;
HString S;
S.ch = new char[MAXSIZE];//在堆区开辟空间, 用完需要手动删除指针
S.length = 0;
```

### 串的链式存储结构

```C
//Power by Marscode
//结点结构和串结构：每个节点存多个字符
typedef struct StringNode{
    char ch[4];
    struct StringNode* next;
}StringNode, *String;
```

### 串基本操作的实现

```C
//求子串
bool SubString(StringNode &Sub, StringNode S, int pos, int len){
    if(pos + len - 1 > S.length){
        return false;
    }//子串范围越界

    for(int i = pos; i < pos + len; i++){
        Sub.ch[i - pos + 1] = S.ch[i];
    }//子串赋值
    Sub.length = len;
    return true;
}

//定位操作
int Index(StringNode S, StringNode T, int pos){
    int i = pos;
    int j = 1;
    while(i <= S.length && j <= T.length){
        if(S.ch[i] == T.ch[j]){
            ++i;
            ++j;
        }else{
            i = i - j + 2;
            j = 1;
        }
    }
    if(j > T.length){
        return i - T.length;
    }else{
        return 0;
    }
}

```
## 字符串模式匹配

### 朴素模式匹配算法

一旦发现不匹配的字符，就回溯到主串的下一个字符，从模式串的第一个字符重新开始匹配。

#### 优化思路

- 对于模式串`T="abaabc"`, 主串`S="ababaabc"`，当匹配到`S[5]`和`T[5]`不匹配时，我们可以直接将模式串T向右移动3个字符，从`T[3]`开始匹配。
- ……

### KMP算法

思路：KMP算法的核心是利用已经部分匹配的结果，避免主串的指针回溯。详细的说就是，当匹配到`S[i]`和`T[j]`不匹配时，我们可以直接将模式串T向右移动`j-next[j]`个字符，从`T[next[j]]`开始匹配。  
这样可以有效的减少匹配的次数，降低时间复杂度。最坏时间复杂度：`O(m+n)`

- [ ] 待完善