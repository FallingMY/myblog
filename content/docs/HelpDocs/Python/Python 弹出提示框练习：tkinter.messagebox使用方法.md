---
# type: docs 
title: Python 弹出提示框练习：tkinter.messagebox使用方法
date: 2024-07-05T11:34:47+08:00
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
  - HelpDocs
categories:
tags: 
  - HelpDocs
  - Python
authors:
  - CSDN_user
images: []
--- 

导入tkinter模块

```python
>>>from tkinter import messagebox
```

##### 消息提示框

```python
>>>messagebox.showinfo('提示','你太帅了！')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200922235814142.png#pic_center)

##### 消息警告框

```python
>>>messagebox.showwarning('警告','您太帅了！')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200923000002322.png#pic_center)

##### 错误消息框

```python
>>>messagebox.showerror('错误','您帅出问题了')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200923000554630.png#pic_center)

##### 对话框

```python
>>>messagebox.askokcancel('提示', '要执行此操作吗')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200923000625670.png#pic_center)  
返回值true/false

```python
>>>messagebox.askquestion('提示', '要执行此操作吗')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200923000742637.png#pic_center)  
返回值yes/no

```python
>>>messagebox.askyesno('提示', '要执行此操作吗')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200923000956489.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1hyZXFjeG9LaXNz,size_16,color_FFFFFF,t_70#pic_center)  
返回值true/false

```python
>>>messagebox.askretrycancel('提示', '要执行此操作吗')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200923001038572.png#pic_center)

返回值true/false

##### 文件对话框

```python
import tkinter.filedialog
filename = tkinter.filedialog.asksaveasfilename() # 返回文件名
print(filename )
filename = tkinter.filedialog.asksaveasfile() # 会创建文件
print(filename )
filename =tkinter.filedialog.askopenfilename() # 返回文件名
print(filename )
filename = tkinter.filedialog.askopenfile() # 返回文件流对象
print(filename )
filename = tkinter.filedialog.askdirectory() # 返回目录名
print(filename )
filename = tkinter.filedialog.askopenfilenames() # 可以返回多个文件名
print(filename )
filename  =tkinter.filedialog.askopenfiles() # 多个文件流对象
print(filename )
```

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[Python入门技能树](https://edu.csdn.net/skill/python/python-3-174?utm_source=csdn_ai_skill_tree_blog)[桌面应用开发](https://edu.csdn.net/skill/python/python-3-174?utm_source=csdn_ai_skill_tree_blog)[Tkinter](https://edu.csdn.net/skill/python/python-3-174?utm_source=csdn_ai_skill_tree_blog)426662 人正在系统学习中

本文转自 <https://blog.csdn.net/XreqcxoKiss/article/details/108743930>，如有侵权，请联系删除。