---
# type: docs 
title: 贪心算法和回溯
date: 2025-03-15T13:51:29+08:00
featured: false
draft: true
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

# 贪心算法

贪心算法是一种在每一步选择中都采取在当前状态下最好或最优（即最有利）的选择，从而希望导致结果是全局最好或最优的算法策略。  它不从整体最优上加以考虑，所做出的是在某种意义上的局部最优解。

贪心选择：在每一步选择中，都选择当前状态下最优的选择，即贪心选择。

最优子结构：问题的最优解包含子问题的最优解。

贪心算法的基本框架：

```c
function greedyAlgorithm(problem):
solution = {}  // 初始化解
while (not isSolutionComplete(solution) and hasAvailableChoices(problem)):
    choice = selectBestChoice(problem)  // 根据贪心策略选择当前最优选择
    if (isChoiceFeasible(choice, solution)):  // 检查选择是否可行
        solution = applyChoice(choice, solution)  // 将选择应用到解中
        problem = updateProblem(problem, choice)  // 更新问题状态
    else:
        removeChoiceFromAvailableChoices(problem, choice)  // 如果选择不可行，从可用选择中移除
if (isSolutionComplete(solution)):
    return solution  // 返回解
else:
    return "No solution found"  // 没有找到解
```

# 回溯算法

一个复杂问题的解决方案是由一系列的决策组成的。回溯算法是一种通过穷举所有可能的决策来找到问题解的算法。它通过递归地尝试所有可能的决策，直到找到问题的解或尝试完所有可能的决策。

解空间：解空间是问题的解的集合，它是一个树状结构，其中每个节点表示一个可能的解。

应用回溯算法解决问题时，应首先明确问题的解空间。解空间中满足约束条件的解称为可行解。

问题的解由一个不等长或等长的解向量 $x=(x_1,x_2,…,x_n)$ 表示。其中 $x_i$ 表示第 i 布的操作。

所有满足约束条件的解向量构成问题的解空间。

问题的解空间一般用树来表示。
