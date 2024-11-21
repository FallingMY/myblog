---
# type: docs 
title: Git基本使用教程（二）：获取更新与推送更新
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
  - Git
authors:
  - CSDN_user
images: []
---

[传送门：Git基本使用教程（一）:入门及第一次基本完整操作](https://blog.csdn.net/qq_35206244/article/details/97698815)  
[官方文档：Git基础](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-Git-%E5%9F%BA%E7%A1%80)

* * *

提示：直接使用Ctrl+F全文检索关键字，更容易找到相应命令

* * *

##### ①查看远程仓库:切换至某一目录，执行命令

```
git remote show origin
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730130434873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
如图所示，我在Git目录下（包含两个仓库，dywhml，bysj）执行命令，将显示config文件中配置的仓库地址。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730130547706.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
切换目录至bysj，再看下效果  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730130714586.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

##### ②修改工作区文件，进行add,status,diff,commit,push

*   工作目录内容track了才能用git diff
*   git diff 是工作区(work dict)和暂存区(stage)的比较
*   git diff –-cached 是暂存区(stage)和版本库（repository）的比较  
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730132951833.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
    如图，在bysj下执行了对某个文件的修改（README.md），执行add，然后执行status，可以看到提示，modified:README.md。

```
git diff --cached
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730133147398.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
接着，执行diff，就是上面提到的，直接diff和diff --cached的含义不一样。  
**注意：**

*   git diff 是工作区(work dict)和暂存区(stage)的比较
*   git diff –-cached 是暂存区(stage)和版本库（repository）的比较

##### ③commit提交

```
git commit -m “注释内容”
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/201907301338301.png)

##### ④push到远程仓库

```
git push origin
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730140156319.png)

##### ⑤从远程获取更新fetch，pull

获取更新有两种，fetch和pull。

*   fetch只是从远程获取最新到本地，不会自动merge，需要手动合并，比较安全。

```
方法一：
　1、git fetch orgin master #将远程仓库的master分支下载到本地当前branch中

　2、git log -p master  ..origin/master #比较本地的master分支和origin/master分支的差别

　3、git merge origin/master #进行合并
```

**1、fetch:**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730142322790.png)  
**2、对比差异：**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730142350890.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
**3、确认后，合并：**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730142411317.png)

```
方法二：
1、git fetch origin master:tmp #从远程仓库master分支获取最新，并在本地建立tmp分支

2、git diff tmp #将当前分支和tmp对比

3、git merge tmp #合并tmp分支到当前分支
```

*   pull从远程获取最新版本并merge到本地

```
git pull origin master
```

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[Git技能树](https://edu.csdn.net/skill/git/?utm_source=csdn_ai_skill_tree_blog)[首页](https://edu.csdn.net/skill/git/?utm_source=csdn_ai_skill_tree_blog)[概览](https://edu.csdn.net/skill/git/?utm_source=csdn_ai_skill_tree_blog)7467 人正在系统学习中

本文转自 <https://blog.csdn.net/qq_35206244/article/details/97772285>，如有侵权，请联系删除。