---
# type: docs 
title: Python 小甲鱼教程 Easygui 篇
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
终于有点实质性可以看到摸到的界面了，搜了一下虽然easygui用的不多，但是作为一个起步，先了解一下吧，毕竟道理想通。

下面按照小甲鱼的代码敲了一遍

  

import easygui as g  
import sys  
  
while 1:  
    g.msgbox('嗨，欢迎进入第一个界面小游戏')    #msgbox其实还可以设置第二个参数，第二个参数代表标题栏上面的文字，就如下面那个msgbox里面的 **'结果'**  
  
  
    msg='请问你希望在鱼C工作室学习到什么知识呢？'  
    title='小游戏互动'  
    choices=\['谈恋爱','编程','OOXX','琴棋书画'\]  
  
  
    choice=g.choicebox(msg,title,choices)     #还没看文档，不过这个choicebox这个函数应该是可以接受好几个参数的，包括顶栏的标题，选项内容，已经主语句  
  
  
    g.msgbox('你的选择是:' + str(choice),'**结果**')  
  
  
    msg ='你希望重新开始小游戏吗？'  
    title='请选择'  
  
  
    if g.ccbox(msg,title):  
        pass  
    else:  
        sys.exit(0)  

  

激活的界面如下：

![](https://img-blog.csdn.net/20160717175323828)  

  

  

![](https://img-blog.csdn.net/20160717175331847)  

  

  

  

![](https://img-blog.csdn.net/20160717175338660)  

  

  

  

  

  

![](https://img-blog.csdn.net/20160717175344219)  

  

\-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

  

这里就是说明了，easygui函数也可以接受关键字参数

  

  

![](https://img-blog.csdn.net/20160717184056069)  

  

  

  

然后，我们可以自行修改按钮的文本，ok\_button是原始参数的名字！！，但是注意每个参数的排列顺序，比如你要修改标题名字，就得把这一个参数写在ok\_button的前面

  

![](https://img-blog.csdn.net/20160717184850312)  

  

接下去是ccbox，cc表示continue 还是 cancel

他返回的是1和0，但是不代表True和False，但是在if里面还是可以用1和0，另外，选项后面还可以加，自己随意。

![](https://img-blog.csdn.net/20160717185515227)  

  

  

这里讲的是buttonbox，这个和choicebox功能有点像，但是区别是，choicebox是类似于下拉列表的，而button则是按键型的。

![](https://img-blog.csdn.net/20160717190528069)  

  

  

下面2个功能只是在返回值上有区别，没搞懂为什么要有这样的区别

![](https://img-blog.csdn.net/20160717190850050)  

  

  

  

下面是很重要的一环，是讲插入图片的，**但是easygui只接受gif格式的图片**，下面是教程和自己做的例子

  

  

  

![](https://img-blog.csdn.net/20160717191940774)  

![](https://img-blog.csdn.net/20160717191946103)  

  

  

  

  

  

下面讲choicebox的，**他适用于什么情况呢？就是选项太多，导致用buttonbox的话会把界面拉太大**

  

下面是教程和自己做的例子

![](https://img-blog.csdn.net/20160717194044476)  

  

![](https://img-blog.csdn.net/20160717193944298)  

  

**接下来一节是比较重要的，就是让用户输入内容，教程和测试如下：**

![](https://img-blog.csdn.net/20160717194620520)  

![](https://img-blog.csdn.net/20160717194517473)  

  

  

一章节比一章节重要，下面是一个多项填写功能的函数，multenterbox,具体教程和试验如下：

![](https://img-blog.csdn.net/20160717200027604)  

![](https://img-blog.csdn.net/20160717195954151)  

  

  

  

下面是passwordbox函数，可以将输入的函数表示为星号

![](https://img-blog.csdn.net/20160717204618345)  

![](https://img-blog.csdn.net/20160717204541750)  

  

**然后这个是多重条目的函数，可以有多重选项可以输入**

  

![](https://img-blog.csdn.net/20160717204953164)  

  

  

**接下来一段是用于显示文本内容的函数,  textbox**

  

![](https://img-blog.csdn.net/20160717205442442)  

![](https://img-blog.csdn.net/20160717205446982)  

  

  

  

  

接着是关于浏览文件夹的功能函数  diropenbox

教程和试验如下

![](https://img-blog.csdn.net/20160717215208671)  

![](https://img-blog.csdn.net/20160717215215249)  

  

  

接下来是打开文件的代码，教程和试验如下：

![](https://img-blog.csdn.net/20160717220229528)  

![](https://img-blog.csdn.net/20160717220219674)  

  

然后是保存文件的函数  filesavebox，教程和试验如下

  

  

![](https://img-blog.csdn.net/20160717221909849)  

![](https://img-blog.csdn.net/20160717221914509)  

  

  

最后，是一个捕获异常的，相对简单，只要写一句exceptionbox就可以用一个弹出框来显示错误内容

![](https://img-blog.csdn.net/20160717223602454)  

![](https://img-blog.csdn.net/20160717223608154)  

  

文章知识点与官方知识档案匹配，可进一步学习相关知识

[Python入门技能树](https://edu.csdn.net/skill/python/?utm_source=csdn_ai_skill_tree_blog)[首页](https://edu.csdn.net/skill/python/?utm_source=csdn_ai_skill_tree_blog)[概览](https://edu.csdn.net/skill/python/?utm_source=csdn_ai_skill_tree_blog)426662 人正在系统学习中

本文转自 <https://blog.csdn.net/bestallen/article/details/51933427?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7EPaidSort-1-51933427-blog-139477688.235%5Ev43%5Epc_blog_bottom_relevance_base6&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7EPaidSort-1-51933427-blog-139477688.235%5Ev43%5Epc_blog_bottom_relevance_base6&utm_relevant_index=1>，如有侵权，请联系删除。