---
# type: docs 
title: Git基本使用教程（一）：入门及第一次基本完整操作
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
<meta name="referrer" content="no-referrer" /> <!--可以让img标签预加载网络图片-->
> git基本使用教程  
> [传送门：Git基本使用教程（二）：基本常用命令](https://blog.csdn.net/qq_35206244/article/details/97772285)  
> [官方文档：Git基础](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-Git-%E5%9F%BA%E7%A1%80)

带着以下问题阅读本文，相信会事半功倍。

*   什么是git？为什么用git而不是其他的版本控制工具，如svn？
*   什么是仓库？本地仓库与远程仓库，常用的远程仓库有哪些，如何建立？
*   怎么用git？如何用git管理文件，实现版本控制？

* * *

**2019年8月19日 15:59:48**  
git安装尽量避免中文路径，一般会因路径含中文出现以下问题：  
![1234](https://img-blog.csdnimg.cn/20190819160037459.png?w=200)


* * *

### 一、git简介

git是个[分布式](https://so.csdn.net/so/search?q=%E5%88%86%E5%B8%83%E5%BC%8F&spm=1001.2101.3001.7020)版本管理工具，与集中式版本管理工具svn相反。

### 二、下载git

**官网：** https://git-scm.com/downloads  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729233653855.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
官网速度较慢，腾讯软件中心就有，而且版本更新及时。  
https://pc.qq.com/detail/13/detail\_22693.html  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729233815391.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

### 三、安装git

**3.1安装位置**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729233937924.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.1

**3.2安装配置文件，根据需要选择**![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729234200143.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.2

**3.3启动文件夹设置（截图略）**  
**3.4设置默认编辑器，可自定义，点击Browse，添加第三方编辑器.exe即可，本文以NotePad++为例**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729234332235.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.4

**3.5选择path配置，提示都是见名知意，按需选择。**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729234722878.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.5

**3.6默认即可**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729234853473.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.6

**3.7 配置行结束标记，保持默认即可**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729234948226.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.7

**3.8选择git使用终端风格**![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235043508.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.8

**3.9额外配置，默认即可**![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235054858.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.9

**3.10 默认**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235140350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.10

**3.11 安装完成**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235211798.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.11

**3.12 打开git bash**  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730000059611.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.12

![在这里插入图片描述](https://img-blog.csdnimg.cn/201907300001189.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

图3.13

### 四、远程仓库配置

远程仓库有很多，比如github，国内的码云，局域网自建git服务器，托管在其他地方的服务器，本文以github为例  
\*\*网址：\*\*https://github.com  
**4.1注册账户：** 类似普通的网站新用户注册，使用邮箱注册即可。  
**4.2新建仓库：** 点击右上角，加号，new repository  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235714573.png)  
下一步  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235836900.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
如，我已经建立好的仓库：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190729235937334.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

### 五、生成（配置）SSH

git客户端安装后，如何和远程仓库，如github连接呢？本文使用SSH。  
**5.1 用户名**

```
git config --global user.name "注册名"
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730000857658.png)  
**5.2 邮箱**

```
git config --global user.email "注册邮箱"
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730000949953.png)  
**5.3 生成SSH（以有SSH可以跳过这一步）**

```
ssh-keygen -t rsa -C "自己的邮箱"
```

生成成功，如下图所示：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019073000112998.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
SSH文件存放在C:/User/用户/.ssh下，id\_rsa为私钥，id\_rsa.pub为公钥。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730001331166.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
**5.4 github配置SSH**  
打开id\_rsa.pub文件，全选，复制全文  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730001702732.png)  
github->账户->setting  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019073000180875.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
选择SSH and GPGkeys，New SSH key  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730001839805.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
自定义一个title，然后粘贴从公钥文件中拷贝的key  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730001953753.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
**5.5 测试SSH连接**

```
ssh -T git@github.com
```

按照提示输入yes，回车，提示successfully之类的就说明SSH连接正常，github上的钥匙也会变成绿色  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730002414433.png)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730002509244.png)  
至此，本地git客户端和远程github建立了联系。

### 六、推送文件至远程仓库

在把文件推送到远程仓库之前，先要了解本地仓库这个概念，此外还有add，commit，push等概念，本文不再赘述。  
**基本流程:add->commit->push**

#### 6.1建立本地仓库

新建一个文件夹  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730002808996.png)  
git bash中执行命令，将该文件夹初始化为一个仓库

```
git init
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730002923399.png)  
结束以后在文件夹下面会出现一个隐藏的文件夹.git，没有的话，设置一下文件夹选项，显示隐藏文件  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730003039575.png)

#### 6.2 推送文件至远程

**本文建议**，在远程建立好仓库，本地进行clone，然后再添加新文件，最后推送至远程。这样的步骤对新手比较友好。  
如：事先在github建立了仓库，bysj，并新建了README文件，此时远程仓库中只有这一个文件。  
**一、clone远程至本地**

```
git clone git@github.com:用户名/仓库名.git
```

将远程的bysj仓库及其中的README文件clone至本地  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730003552508.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730003650409.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
然后，向bysj文件夹中手动添加了doc，src，WebContent三个文件夹及其中的子文件夹和文件等。  
可以用ls命令查看bysj文件夹下的文件，可以看到有一个文件，三个文件夹，**使用命令进行add**  
**二、add**

```
git add 文件夹1/ 文件夹2/
```

注意:add有多种形式，可以add某个文件，某个文件夹，或直接add当前仓库下所有文件

```
git add 单个文件
git add 文件夹1/ 文件夹2/ ……多个文件夹之间空格隔开
git add .
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730004215755.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
**三、commit**

```
git commit -m “注释”
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730004625458.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
**四、push**

```
git push -u origin master
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730004926747.png)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730004802447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)  
成功推送至远程仓库bysj，三个文件夹，一个README文件。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190730005030739.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1MjA2MjQ0,size_16,color_FFFFFF,t_70)

* * *

#### 总结：如何推送文件至远程？

①建立本地仓库  
②与远程建立连接，测试

```
ssh -T git@github.com
```

③init命令初始化仓库

```
git init
```

④手动拷贝文件，并执行add命令

```
git add 文件夹1/ 文件夹2/
```

⑤commit命令

```
git commit -m “注释”
```

⑥push命令

```
git push -u origin master
```

> 后记：时间匆忙，难免有遗漏或不当之处，望大家批评指正！

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[Git技能树](https://edu.csdn.net/skill/git/git-62c30f9c31f64a1d96af732c47c93f04?utm_source=csdn_ai_skill_tree_blog)[Git入门](https://edu.csdn.net/skill/git/git-62c30f9c31f64a1d96af732c47c93f04?utm_source=csdn_ai_skill_tree_blog)[Git简介](https://edu.csdn.net/skill/git/git-62c30f9c31f64a1d96af732c47c93f04?utm_source=csdn_ai_skill_tree_blog)7467 人正在系统学习中

本文转自 <https://blog.csdn.net/qq_35206244/article/details/97698815>，如有侵权，请联系删除。