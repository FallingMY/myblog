---
# type: docs 
title: 计算几何
date: 2025-03-22T13:47:27+08:00
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

# 计算几何基础

## 1.1 向量基本运算

- 向量的表示：$\vec v = (x, y)$
- 向量的加法：$\vec v + \vec w = (x + x', y + y')$
- 向量的减法：$\vec v - \vec w = (x - x', y - y')$
- 向量的数乘：$k \vec v = (kx, ky)$
- 向量的模：$\|\vec v\| = \sqrt{x^2 + y^2}$

## 1.2 向量的点积

- 向量的点积：$\vec v \cdot \vec w = x \cdot x' + y \cdot y'$
- 向量的点积的几何意义：$\vec v \cdot \vec w = \|\vec v\| \cdot \|\vec w\| \cdot \cos \theta$
- 两个向量的夹角：$\theta = \cos^{-1} \frac{\vec v \cdot \vec w}{\|\vec v\| \cdot \|\vec w\|}$
- 判断两个向量是否垂直：$\vec v \cdot \vec w = 0$

## 1.3 向量的叉积

- 向量的叉积：$\vec v \times \vec w = x \cdot y' - x' \cdot y$

# 计算几何基本位置关系简介

# 多边形几何算法

## 1. 多边形的表示

## 2. 多边形的面积

计算简单多边形的面积常用Shoelace公式。该公式通过顶点坐标计算多边形的面积。适用于顶点按顺时针或逆时针排列的简单多边形。

Shoelace公式：
$$
S = \frac{1}{2} \sum_{i=1}^{n} (x_i y_{i+1} - x_{i+1} y_i)
$$