---
# type: docs 
title: 树与二叉树
date: 2024-11-30T08:28:26+08:00
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
categories: []
tags: []
images: []
---

树是一种数据结构。

# 树的概念

## 树的定义

树是n个结点的有限集合（记为T）。

形式化定义（二元组）  

树：$T=(D,R)$。  
$D$ 是包含n个结点的有限集合 $n>0$ 。  
> 当n=0时，称该树为空树。
> 当n>0时，这n个结点中存在一个唯一结点作为树的根结点，其余结点可分为m个互不相交的有限集 $T_1,T_2,...,T_m$ ，其中每个集合本身又是一棵树，称为根的子树。

$R$ 是D上的一个关系，$R\subset D\times D$ 。

## 树的表示

### 逻辑表示法

即我们平时常见的树形图

### 文氏图表示法

### 凹入表示法

### 括号表示法

例如：

> A(B(D,E),C(F,G))

## 树的基本术语

### 结点的度和树的度

树中一个**结点的子树的个数**称为该**结点的度**。  
树中各个结点的度的**最大值**称为**树的度**，通常若树的度为m，称该树为**m叉树**。

### 分支结点与叶结点

度不为0的结点称为非终端结点，也称为**分支结点**。  
度为0的结点称为终端结点，也称为**叶结点**。  

### 路径与路径长度

两个结点$d_i$和$d_j$之间的路径为从$d_i$到$d_j$的结点序列。  
路径的长度为路径上的结点个数减一。  

### 孩子结点、双亲结点和兄弟结点

每个结点的后继结点称为该结点的**孩子结点**。  
该结点被称为孩子结点的**双亲结点**。  
具有相同双亲结点的结点称为**兄弟结点**。  

> **深度优先搜索**
> 从根结点出发，沿着一条路径搜索，直到到达一个叶子结点，然后回溯，继续沿着另一条路径搜索，直到到达另一个叶子结点，以此类推。  
> 一般采用递归的方式实现。

> **广度优先搜索**
> 从根结点出发，先访问所有的兄弟结点，再访问所有的孩子结点，以此类推。  
> 一般采用队列的方式实现。

### 子孙结点和祖先结点

子孙结点：从根结点到该结点的路径上的所有结点称为该结点的子孙结点。  
祖先结点：从该结点到根结点的路径上的所有结点称为该结点的祖先结点。

### 结点的层次和高度

- [ ] 待补充

### 有序树和无序树

若树中各结点的子树从左到右是有次序的，且相对次序是不能随意变换的，称该树为有序树。否则，称该树为无序树。  

### 森林

n个互不相交的树的集合称为森林。

给m棵独立的树加一个根结点，则森林就变成了一棵树。

## 树的性质

- 树中的结点数等于所有结点的度数加1。（加1是加上根结点）
- 度为m的树的其他重要特性：
  - 结点个数为n，$n=n_0+n_1+n_2+...+n_m$，其中$n_0$为度数为0的结点数，$n_1$为度数为1的结点数，$n_2$为度数为2的结点数，以此类推。
  - 所有结点度之和=$n_1+2n_2+3n_3+...+mn_m=n-1$。
- 度为m的树中第i层上至多有$m^{i-1}$个结点。
- 高度为h的m叉树至多有$\frac {m^h-1}{m-1}$个结点。
- 具有n个结点的m叉树的最小高度为$\lceil log_m(n(m-1)+1) \rceil$，最大高度为$n-m+1$。

## 树的基本运算

树的遍历运算是指按某种方式访问树中的每个结点，且每个结点仅被访问一次。

主要的遍历方法：
- 先根遍历
  - 先访问根结点，再依次先根遍历各子树。
- 后根遍历
  - 先依次后根遍历各子树，再访问根结点。
- 层次遍历
  - 从第一层（根结点）开始，从上到下逐层遍历，在同一层中，按从左到右的顺序对结点逐个访问。

注意：先根遍历和后根遍历都是使用递归实现的。

## 树的储存结构

### 双亲储存结构

```C
typedef struct{
    ElemType data;//结点的值
    int parent;//指向双亲结点的伪指针
}PTree[MaxSize];
```

### 孩子储存结构

```C
typedef struct{
    ElemType data;//结点的值
    struct node *sons[MaxSons];//指向孩子结点的指针
}TSonNode;
```

### 孩子兄弟储存结构

```C
typedef struct{
    ElemType data;//结点的值
    struct node *firstson;//指向第一个孩子结点的指针
    struct node *nextbrother;//指向右兄弟结点的指针
}TSBNode;
```

使用链表实现

# 二叉树

## 二叉树的定义

二叉树是

- 满二叉树
  - 所有结点都有两个孩子结点。
  - 所有叶子结点都在同一层。

> **满二叉树的性质**
> 高度为h的满二叉树的结点个数为$2^h-1$。

- 完全二叉树
  - 只有最下面两层有叶子结点。
  - 最下面一层的叶子结点都集中在最左边。

## 二叉树的性质

- 非空二叉树上叶结点数等于双分支结点数加1。即：$n_0=n_2+1$。

> 求解一般二叉树结点个数方法
> 度之和=$n-1$。
> $n=n_0+n_1+n_2$。
> 又:$n_0=n_2+1$。
> 得：$n=n_1+2n_2+1$。

- 非空二叉树上第i层上至多有$2^{i-1}$个结点。
- 完全二叉树的性质
  - $n_1=0$或$n_1=1$，由n的奇偶性决定，n为奇数时$n_1=1$，n为偶数时$n_1=0$。
  - 若一个结点的编号为i，则该结点的左孩子的编号为$2i$，右孩子的编号为$2i+1$。

# 并查集

并查集是一种树形的数据结构，用于处理**不相交集合(Disjoint Sets)** 的合并与查询问题。它特别适合解决动态连通性问题，比如判断两个元素是否属于同一个集合，或将两个集合合并。  

并查集的数据结构记录了一组动态集合