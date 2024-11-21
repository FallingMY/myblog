---
# type: docs 
title: anaconda的安装和使用（管理python环境看这一篇就够了）-CSDN博客
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

#### [anaconda](https://so.csdn.net/so/search?q=anaconda&spm=1001.2101.3001.7020)的安装和使用（管理python环境看这一篇就够了）

- [前言](#前言)
- [一、Anaconda是什么？](#一anaconda是什么)
- [二、Anaconda安装](#二anaconda安装)
- [三、Anaconda使用教程](#三anaconda使用教程)
- [四、pycharm使用anaconda创建的虚拟环境](#四pycharm使用anaconda创建的虚拟环境)
- [总结](#总结)

* * *

前言
--

以前写python，一个电脑上就一个python环境和pycharm就够了，现在遇到项目需求为不同的python环境，如打包为32位的可执行文件、openopc只有python2.7\_32位才能使用等。第一个办法是在电脑上安装多个python环境，使其同时存在，但这样过于麻烦而且容易搞混淆，因此本篇文章就来介绍下anaconda的安装和使用。

一、Anaconda是什么？
--------------

就是可以便捷获取包且对包能够进行管理，同时对环境可以统一管理的发行版本。Anaconda包含了conda、Python在内的超过180个科学包及其依赖项。即它可以在你的电脑上创建多个你想要的python环境，并为每个python环境安装不同的包，不同环境相互切换，操作简单，使用方便！

二、Anaconda安装
------------

下载地址：[https://www.anaconda.com/download/](https://www.anaconda.com/download/)  
百度网盘链接：[https://pan.baidu.com/s/1ccqr833QKsxI5qkW97LCJg](https://pan.baidu.com/s/1ccqr833QKsxI5qkW97LCJg)  
提取码：o09u  
打开下载好的 Anaconda.exe文件，出现如下界面。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020100311451581.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)

点击 Next 即可。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020100311453186.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)

用户协议，点击 I Agree。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003131709804.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
选All Users 点Next  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003114604158.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)

接下来选择安装路径，这里不建议装在C盘，安装完大概3个G左右，现在都是固态硬盘了，安装到固态硬盘就好，路径要知道自己安到了哪里（后续使用不同环境的时候会用到这个安装路径）。选择好了之后点击Next  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003120122654.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)

接下来是重中之重，第一个选项是添加环境变量，默认是没有勾选的，请务必勾选上，如果这里不勾选，后续安装完成后想要自行添加环境变量会非常麻烦。勾选完后点击 Install 安装。如果忘了勾选可以卸载重装。  
![第七步](https://img-blog.csdnimg.cn/20201003120058607.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)

这里是pycharm的一个推广没有需求的话可以不用管，最后一步了，继续点Next。  
![第八步](https://img-blog.csdnimg.cn/20201003120030145.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)

Finish完成。（那两个 √ 可以取消。）  
安装完成后在开始菜单会多出一个快捷方式，也就是Anaconda下的子程序：  
开始菜单  
![![在这里插入图片描述](https://img-blog.csdnimg.cn/2020100311341376.png#pic_center](https://img-blog.csdnimg.cn/20201003113633980.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
1.修改为清华源  
直接打开cmd输入以下命令  
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/  
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/  
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud//pytorch/  
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/  
conda config --set show\_channel\_urls yes  
2.移除清华源  
输入：conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/  
这个命令是为了移除之前conda config --show channels显示的清华源。

三、Anaconda使用教程
--------------

主要用的两个为Anaconda Prompt 和Anaconda Navigator  
Anaconda Prompt 就是我们的cmd，打开后如下：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003114721662.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
以后的创建环境和环境切换，和pip安装各种包全在这里，  
介绍几个常用的快捷键：  
1.conda info 查看当前环境的信息  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003120322562.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
2.conda info -e 查看已经创建的所有[虚拟环境](https://so.csdn.net/so/search?q=%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83&spm=1001.2101.3001.7020)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003120359929.png#pic_center)  
目前我创建的3个不同的虚拟环境，分别32位python2.7、32位python3.6和64位python3.7  
3.conda activate xx 切换到xx虚拟环境  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003121417717.png#pic_center)

现在即切换到了64位python3.7环境  
4.set CONDA\_FORCE\_32BIT=1 # 切换到32位  
set CONDA\_FORCE\_32BIT=0 # 切换到64位  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003122028205.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
表示已经切换到32位

5.conda create -n xxx python=2.7 创建一个python2.7 名为xxx的虚拟环境，如要创建32位的python环境，先设置为32位在创建环境，这样创建好的环境即为32位的Python环境，先切换到创建好的环境中  
然后输入python 检查下是否为32位的python2.7版本，这样即创好了  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003123938137.png#pic_center)

6.conda remove -n env\_name --all 移除环境，也可在Anaconda Navigator中移除

Anaconda Navigator为可视化管理软件  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020100312533629.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003125356826.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
这是我们添加的清华源，加快包的下载速度，  
我们创建的环境和环境里的安装的包可以在Environments里查看  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020100312550622.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
也可以在这里创建虚拟环境和移除虚拟环境，还可为每个独立的环境安装需要的包

四、pycharm使用anaconda创建的虚拟环境
--------------------------

1.进入项目设置里的Project Interpreter  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130144371.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
然后点击show all  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130218580.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
然后点击添加  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130305742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
接着选Existing environment  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130352941.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130528878.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
选择自己在anaconda里创建的虚拟环境，路径在anaconda的安装路径里的envs里  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130631305.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130652161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
最后点确定应用即可。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003130749884.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RxbGlzbm8x,size_16,color_FFFFFF,t_70#pic_center)  
至此pycharm使用该环境已完毕。

总结
--

anaconda是一款强大的软件也是python程序员必备的软件，尽量达到每个项目单独一个虚拟环境，因为后面使用pyinstaller打包的项目成为可执行文件的时候，会打包环境里所有安装的包，该环境下每个包都是我们项目用到才安装的，非常干净，这样会加快文件的运行速度也减小文件的大小。便于我们管理和维护！

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[Python入门技能树](https://edu.csdn.net/skill/python/python-3-4?utm_source=csdn_ai_skill_tree_blog)[预备知识](https://edu.csdn.net/skill/python/python-3-4?utm_source=csdn_ai_skill_tree_blog)[常用开发工具](https://edu.csdn.net/skill/python/python-3-4?utm_source=csdn_ai_skill_tree_blog)426640 人正在系统学习中

本文转自 <https://blog.csdn.net/tqlisno1/article/details/108908775>，如有侵权，请联系删除。