---
# type: docs 
title: 掌握计算机自动化：PyAutoGUI库详细教程（最全使用方法，每行代码都有注释，帮你解决与之有关的所有问题）-CSDN博客
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

#### 文章目录

- [一、pyAutoGUI 概括](#一pyautogui-概括)
- [二、pyAutoGUI 库安装](#二pyautogui-库安装)
- [三、pyAutoGUI 操作前置知识](#三pyautogui-操作前置知识)
  - [1.屏幕分辨率与尺寸](#1屏幕分辨率与尺寸)
  - [2.暂停操作](#2暂停操作)
  - [3.故障保护功能](#3故障保护功能)
- [四、鼠标操作](#四鼠标操作)
  - [1.鼠标移动操作](#1鼠标移动操作)
  - [2.获取鼠标位置的坐标值](#2获取鼠标位置的坐标值)
  - [3.鼠标拖拽操作](#3鼠标拖拽操作)
  - [4.鼠标点击操作](#4鼠标点击操作)
  - [5.鼠标单击分布操作](#5鼠标单击分布操作)
- [五、键盘操作](#五键盘操作)
  - [1.输入字符](#1输入字符)
  - [2.按键操作](#2按键操作)
  - [3.热键操作（组合键）](#3热键操作组合键)
- [六，消息框](#六消息框)
  - [1.可以设置一个button](#1可以设置一个button)
  - [2.可以设置多个button](#2可以设置多个button)
  - [3.自带文本输入框的消息框](#3自带文本输入框的消息框)
  - [4.自带密码的文本输入框的消息框](#4自带密码的文本输入框的消息框)
- [七、屏幕截图](#七屏幕截图)
  - [1.截全屏](#1截全屏)
  - [2.指定区域内截屏](#2指定区域内截屏)
  - [3.图片定位](#3图片定位)

  
这篇博客主要介绍了如何使用Python库pyAutoGUI进行计算机自动化行为操作。文章首先介绍了pyAutoGUI库的概括和安装方法。接下来，详细讲解了操作前需要了解的屏幕分辨率与尺寸，暂停操作，以及故障保护功能的使用方法。在鼠标操作部分，详细解析了鼠标的移动、获取位置、拖拽、点击以及单击分布操作。键盘操作部分，讨论了如何进行输入字符、按键以及热键操作。此外，文章还提到了使用消息框显示信息，可设置一个或多个按钮，及带有文本输入框和密码输入框的消息框使用方法。最后，文章详述了如何进行屏幕截图并在指定区域内截屏，以及图片定位的方法。整篇文章旨在帮助读者理解和掌握使用pyAutoGUI库进行计算机自动化操作的方法。

一、pyAutoGUI 概括
--------------

pyAutoGUI是一个用于自动化计算机行为的Python库。它可以用来操作鼠标和键盘，模拟人类的输入方式，比如移动鼠标、点击按钮、输入文本等。pyAutoGUI还可以用来开发自动化工具，比如自动回复聊天机器人、自动游戏挂机等。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/27a228ed1d424a2caa13eca135ae1329.png)

二、pyAutoGUI 库安装
---------------

pyAutoGUI的下载代码如下：  
打开命令行窗口输入以下代码即可

```c
pip install pyautogui
```

或者，你可以直接从PyCharm上下载，教程如下：[Python基础第八篇（Python异常处理，模块与包）](https://blog.csdn.net/Du_XiaoNan/article/details/135757080)

三、pyAutoGUI 操作前置知识
------------------

### 1.屏幕分辨率与尺寸

![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/e0e5ef8df6a04d1d8fd43dde39753b74.png#pic_center)  
为方便编写代码，pyautogui 接口用起了别名“pg”

```c
import pyautogui as pg
import time

# 获取屏幕尺寸
# 元组类型的返回值
screen_width, screen_height = pg.size()
# 获取屏幕宽高
print("屏幕宽度:", screen_width)
print("屏幕高度:", screen_height)
```

### 2.暂停操作

```c
#暂停操作，全局暂停，局部暂停
#全局暂停是指在程序中暂停所有操作（进行一行改代码，停一次，一般写在接口下面先执行），局部暂停是指在程序中暂停某个操作

#--------全局暂停--------
#默认是0.1  浮点型  单位是秒
pg.PAUSE = 1.0

#--------局部暂停--------
#默认是0  浮点型  单位是秒
time.sleep(2)
```

### 3.故障保护功能

pyAutoGUI 有一个名为“故障保护”的功能，当鼠标或键盘操作失败时，这个功能可以防止程序崩溃。要启用故障保护功能，可以在使用pyAutoGUI之前导入pyautogui.PAUSE：  
插入

```c
import pyautogui as pg
pg.PAUSE = 1
```

这样，当pyAutoGUI遇到错误时，它会等待1秒后再尝试执行操作。你可以根据需要调整PAUSE的值。

或者在pyAutoGUI程序执行过程中想要停止，可以快速将鼠标移动到屏幕的四个角以中止程序，默认存在的。不想用可在pyAutoGUI代码执行之前插入

```c
pg.failsafe=false
```

四、鼠标操作
------

### 1.鼠标移动操作

```c
#移动鼠标到指定位置
#duration是指所用时间，默认是0.25  浮点型  单位是秒
pg.moveTo(100, 100, duration=1)
#移动鼠标到相对位置
pg.move(100, -100, duration=1)
```

### 2.获取鼠标位置的坐标值

```c
# 获取鼠标位置的坐标值
mouse_x, mouse_y = pg.position()
print("鼠标位置的坐标值:", mouse_x, mouse_y)
#检测指定坐标是否在屏幕上
print("(100, 100)坐标是否在屏幕上:", pg.onScreen(100, 100))
```

### 3.鼠标拖拽操作

```c
#鼠标拖拽操作
#默认左键，左键 left，右键 right,中键 middle
#绝对拖拽，指拖拽到那个位置
pg.dragTo(x=100, y=-100, duration=0.5, button='left')
#相对拖拽，相对于当前位置拖拽
pg.drag(xOffset=100, yOffset=100, duration=0.5, button='right')
```

### 4.鼠标点击操作

```c
#鼠标点击操作
#单击
#button:默认左键，左键 left，右键 right,中键 middle
#clicks:点击次数，默认是1次
#interval:每次点击间隔时间，默认是0
#duration:持续时间，默认是0
pg.click(x=90, y=100,clicks=2,interval=0,duration=0, button='left')
# 双击
#button:默认左键，左键 left，右键 right,中键 middle
pg.doubleClick(x=90, y=100, duration=0, button='left')
```

### 5.鼠标单击分布操作

```c
#单击分布操作
#按下鼠标键位
pg.mouseDown(button='left')
#释放鼠标键位
pg.mouseUp(button='left')
```

五、键盘操作
------

### 1.输入字符

```c
# 键盘操作
#输入字符
#messge:想要输入的字符
#interval:每次输入间隔时间，默认是0
#不能直接输入中文，需要使用unicode编码
#输入时应先使输入框获取焦点，否则无法输入（可以先单击一下）
pg.write("Hello, World!",interval=0.2)
```

### 2.按键操作

```c
#按键操作
#presses:按键的次数，默认是1次
#interval:每次按键间隔时间，默认是0
pg.press('enter',presses=2,interval=0.2)
```

### 3.热键操作（组合键）

```c
#热键操作
#interval:每次按键间隔时间，默认是0
pg.hotkey('ctrl','a',interval=0.2)
```

**常用按键**

```c
# 所有按键的字符串标识如下
print(pyautogui.KEYBOARD_KEYS)
# 输出:
[
'\t', '\n', '\r', ' ', '!', '"', '#', '$', '%', '&', "'", '(', ')', '*', '+', ',', '-', '.', '/', '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', ':', ';', '<', '=', '>', '?', '@', '[', '\\', ']', '^', '_', '`', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 
'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', '{', '|', '}', '~', 'accept', 'add', 'alt', 'altleft', 'altright', 'apps', 
'backspace', 'browserback', 'browserfavorites', 'browserforward', 'browserhome', 'browserrefresh', 'browsersearch', 'browserstop', 'capslock', 'clear', 'convert', 'ctrl', 'ctrlleft', 'ctrlright', 'decimal', 'del', 'delete', 'divide', 'down', 'end', 'enter', 'esc', 'escape', 'execute', 'f1', 'f10', 'f11', 'f12', 'f13', 'f14', 'f15', 'f16', 'f17', 'f18', 'f19', 'f2', 'f20', 'f21', 'f22', 'f23', 'f24', 'f3', 'f4', 'f5', 'f6', 'f7', 'f8', 'f9', 'final', 'fn', 'hanguel', 'hangul', 'hanja', 'help', 'home', 'insert', 'junja', 'kana', 'kanji', 'launchapp1', 'launchapp2', 'launchmail', 'launchmediaselect', 'left', 'modechange', 'multiply', 'nexttrack', 'nonconvert', 'num0', 'num1', 'num2', 'num3', 'num4', 'num5', 'num6', 'num7', 'num8', 'num9', 'numlock', 'pagedown', 'pageup', 'pause', 'pgdn', 'pgup', 'playpause', 'prevtrack', 'print', 'printscreen', 'prntscrn', 'prtsc', 'prtscr', 'return', 'right', 'scrolllock', 'select', 'separator', 'shift', 'shiftleft', 'shiftright', 'sleep', 'space', 'stop', 'subtract', 'tab', 'up', 'volumedown', 'volumemute', 'volumeup', 'win', 'winleft', 'winright', 'yen', 'command', 'option', 'optionleft', 'optionright'
]
+ 'Add' - 加号键（"+"）通常用于添加或增加操作。
+ 'Alt' - 通常与键盘上的 "Alt" 键相对应，它是一种常用的快捷键，可以用于访问特殊功能或菜单。
+ 'Altleft' - 这个单词通常与键盘上的 "Alt" 键左边的部分相对应，也是用于访问特殊功能或菜单。
+ 'Altright' - 这个单词通常与键盘上的 "Alt" 键右边的部分相对应，也是用于访问特殊功能或菜单。
+ 'Apps' - 右键菜单
+ 'Backspace' - 这个单词通常与键盘上的 "Backspace" 键相对应，用于删除前一个字符或命令。
+ 'Browserback' - 这个单词通常与浏览器相关的快捷键相对应，用于返回浏览器的上一个页面。
+ 'Browserfavorites' - 这个单词通常与浏览器相关的快捷键相对应，用于访问浏览器的收藏夹。
+ 'Browserforward' - 这个单词通常与浏览器相关的快捷键相对应，用于前进到浏览器的一个页面。
+ 'Browserhome' - 这个单词通常与浏览器相关的快捷键相对应，用于导航到浏览器的首页。
+ 'Browserrefresh' - 这个单词通常与浏览器相关的快捷键相对应，用于刷新当前页面。
+ 'Browsersearch' - 这个单词通常与浏览器相关的快捷键相对应，用于在浏览器中执行搜索操作。
+ 'Browserstop' - 这个单词通常与浏览器相关的快捷键相对应，用于停止加载当前页面。
+ 'Capslock' - 这个单词通常与键盘上的 "Capslock" 键相对应，用于锁定或解锁大写字母输入。
+ 'Ctrl' - 这个单词通常与键盘上的 "Ctrl" 键相对应，用于执行各种控制命令或组合键操作。
+ 'Ctrlleft' - 这个单词通常与键盘上的 "Ctrl" 键左边的部分相对应，也是用于执行各种控制命令或组合键操作。
+ 'Ctrlright' - 这个单词通常与键盘上的 "Ctrl" 键右边的部分相对应，也是用于执行各种控制命令或组合键操作。
+ 'Decimal' - 这个单词通常与键盘上的 "Decimal" 或 "." 键相对应，用于输入小数点或十进制数字。
+ 'fn' - "fn" 是一个特殊的键盘功能键，通常在笔记本电脑和一些特定的键盘布局中找到。它用于配合其他按键使用，以实现一些特定的功能，如调节亮度、音量等。
+ 'home' - "home" 对应的按键是键盘上的 "Home" 键，通常用于快速导航到页面的顶部或文本的开头。
+ 'insert' - "insert" 对应的按键是键盘上的 "Insert" 键，用于插入文本或数据。
+ 'left', 'right', 'up', 'down' - 这些方向键对应的按键分别是 "Left Arrow"、"Right Arrow"、"Up Arrow" 和 "Down Arrow"。它们通常用于控制光标的位置。
+ 'num0' 到 'num9' - 这些数字键对应的按键是从 "0" 到 "9"。它们用于输入数字和进行数学运算。
+ 'numlock', 'scrolllock', 'select', 'separator', 'tab' - 这些都是特殊的锁定键或其他功能键，通常用于控制光标移动、滚动页面、选择文本等操作。
+ 'space', 'return' - "Space" 键对应的按键是空格键，用于在文本中插入空格。"Return" 键对应的按键是回车键，用于换行或确认输入。
+ 'win', 'winleft', 'winright' - 这些是特定的功能键，通常用于操作系统中的窗口控制和菜单操作。"Win" 键对应的按键通常是 Windows 徽标键（通常是带有 Windows 标志的按键）。"Winleft" 和 "Winright" 是左右 Windows 功能键的称呼，但它们并不对应键盘上的标准按键
```

六，消息框
-----

### 1.可以设置一个button

```c
#消息框
#title:标题
#text:文本
# button:按钮，默认是OK
#返回值：默认是OK
arr1 = pg.alert(title='Hello, World!',text='没钱只能当牛马',button='ok')
print(arr1)

```

### 2.可以设置多个button

```c
#可以设置多个button
#返回值：返回用户点击的按钮
arr2 = pg.confirm(title='Hello, World!',text='没钱只能当牛马',buttons=['ok','cancel'])
print(arr2)

```

### 3.自带文本输入框的消息框

```c
#自带文本输入框的消息框
#返回值：返回用户输入的内容
#文本输入框没字返回：None
arr3=pg.prompt(title='Hello, World!',text='没钱只能当牛马',default='请您输入：')
print("您输入的内容是："+arr3)
```

### 4.自带密码的文本输入框的消息框

```c
#自带密码的文本输入框的消息框
#返回值：返回用户输入的密码
#密码没字返回：None
arr4=pg.password(title='Hello, World!',text='没钱只能当牛马',default='请您输入：',mask='*')
print("您输入的密码是："+arr4)
```

七、屏幕截图
------

### 1.截全屏

```c
#屏幕截图
#imageformat:截图保存的格式，默认是png
#region:截图的范围，默认是整个屏幕
# 截取全屏 在1920 x 1080屏幕上，screenshot（）函数大约需要100毫秒-不快但不慢。
# 截取全屏，并以图片保存
pg.screenshot("E:\\pythonDemo\\python_2024\\all.png")
```

### 2.指定区域内截屏

```c
#指定区域内截屏
#region:截图的范围，默认是整个屏幕 : [开始位置x,开始位置y,x扩展的分辨率,y扩展的分辨率]
pg.screenshot("E:\\pythonDemo\\python_2024\\all2.png",region=[100,100,500,500])
```

### 3.图片定位

```c
#图片定位
#定位到的图片的坐标（从左到右，从上到下）
#image:图片路径
#confidence:定位精度，默认是0.8
#count:定位到的图片数量，默认是1
#返回图片中心点

pg.locateCenterOnScreen("E:\\pythonDemo\\python_2024\\Google_tubiao.png",confidence=0.1)
```

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[云原生入门技能树](https://edu.csdn.net/skill/cloud_native/?utm_source=csdn_ai_skill_tree_blog)[首页](https://edu.csdn.net/skill/cloud_native/?utm_source=csdn_ai_skill_tree_blog)[概览](https://edu.csdn.net/skill/cloud_native/?utm_source=csdn_ai_skill_tree_blog)18885 人正在系统学习中

本文转自 <https://blog.csdn.net/Du_XiaoNan/article/details/136197235>，如有侵权，请联系删除。