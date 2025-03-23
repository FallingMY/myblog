---
# type: docs 
title: 分治策略
date: 2025-03-15T13:54:17+08:00
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

在学习排序算法的过程中，我们接触到了快速排序。

而快速排序的核心思想就是分治法。

# 分治法概述

## 设计思想

对于一个规模为n的问题，若该问题可以容易地解决（比如说规模n较小）则直接解决，否则将其分解为k个规模较小的子问题，这些子问题互相独立且与原问题形式相同，**递归地解**这些子问题，然后将各子问题的解合并得到原问题的解。这种算法设计策略叫做分治法。

分治法能解决的问题的主要特征：

1. 该问题的规模缩小到一定的程度就可以容易地解决。
2. 该问题可以分解为若干个规模较小的相同问题，即该问题具有最优子结构性质。
3. 利用该问题分解出的子问题的解可以合并为该问题的解。
4. 该问题所分解出的**各个子问题是相互独立**的，即子问题之间不包含公共的子问题。

## 基本步骤

分治法通常采用递归算法设计技术，在每一层递归上都有三个步骤：

1. 分解：将原问题分解为若干个规模较小，相互独立，与原问题形式相同的子问题。
2. 求解子问题：若子问题规模较小而容易被解决则直接解，否则递归地解各个子问题。
3. 合并：将各个子问题的解合并为原问题的解。

## 算法框架

```c
// 函数：解决问题
ResultType solve(ProblemType problem) {
    // 基本情况：问题足够小，直接解决
    if (is_small(problem)) {
        return direct_solution(problem);
    }

    // 分解：将问题分解为子问题
    SubproblemType subproblems[MAX_SUBPROBLEMS];
    int num_subproblems = divide(problem, subproblems);

    // 解决：递归地解决子问题
    ResultType subsolutions[MAX_SUBPROBLEMS];
    for (int i = 0; i < num_subproblems; i++) {
        subsolutions[i] = solve(subproblems[i]);
    }

    // 合并：将子问题的解合并成原问题的解
    return combine(subsolutions, num_subproblems);
}
```

---

在实际的应用中人们发现，把问题分解成若干个规模较小的问题时，每个子问题的规模相同时，分治法的效率是最高的。

# 求解排序问题

## 快速排序

### 基本思想

在待排序的n个记录中任取一个记录，以该记录的关键字为标准，将所有关键字小于该记录的记录排列在前，所有关键字大于该记录的记录排列在后，然后分别对前后两个子序列重复上述过程，直到所有记录都排好序为止。

### 算法

```c
int Partition(int a[], int low, int high) {
    int pivot = a[low];// 枢轴记录
    while (low < high) {
        while (low < high && a[high] >= pivot) {
            high--;
        }
        a[low] = a[high];// 比枢轴小的元素移动到左端
        while (low < high && a[low] <= pivot) {
            low++;
        }
        a[high] = a[low];// 比枢轴大的元素移动到右端
    } 
    a[low] = pivot;// 枢轴元素放到最终位置
    return low;// 返回枢轴所在位置;实际上此时不论返回low还是high都是一样的
}
void QuickSort(int a[], int low, int high) {
    if (low < high) {
        int pivotpos = Partition(a, low, high);// 划分
        QuickSort(a, low, pivotpos - 1);// 递归求解
        QuickSort(a, pivotpos + 1, high);// 递归求解
    } 
}
int main() {
    int a[10] = {5, 2, 4, 6, 1, 3, 9, 8, 7, 0};
    QuickSort(a, 0, 9);
    for (int i = 0; i < 10; i++) {
        printf("%d ", a[i]);
    }
    return 0;
}
```