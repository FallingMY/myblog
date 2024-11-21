---
# type: docs 
title: Git的使用（易懂+巨无比详细+新手必看）
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

Git是用来干什么的呢？  
是用来管理代码文件的，具体是啥自行百度就行，其实你点进来你多少会对他有点了解，知道他是干嘛的~

提示：**照着本文，敲一下指令就能掌握，底层原理了解即可，主要是会用！**

### 01 | 下载软件

软件官网  
[Git官网进口](https://git-scm.com/)  
下载好了可以输入  
`git --version`  
![在这里插入图片描述](https://img-blog.csdnimg.cn/bae43ae0be2c449b88a5f7e83c9d8eed.png)  
这里可以看到git的版本，这就说明git安装成功了！

### 02 | Git的命令–开发需要

首先需要熟悉linux常用基本命令！

![在这里插入图片描述](https://img-blog.csdnimg.cn/df84f44ad2ad40c1b2a030e1e595981d.png)  
而常用的Git也就无非这么几个  
![在这里插入图片描述](https://img-blog.csdnimg.cn/52e7f3c3938e48f188f1e4c16282166f.png)  
只要把[linux命令](https://so.csdn.net/so/search?q=linux%E5%91%BD%E4%BB%A4&spm=1001.2101.3001.7020)，配合git命令（红色的记住），就能实现大部分开发需求了！  
`git init`:初始化  
`git status`：查看状态  
`git add <文件名>`：追踪文件，添加到暂存区  
`git commit -m '备注' <文件名>`：提交文件到本地库  
`git reflog / git log`：查看日志  
`git reset --hard 版本号`：版本切换  
`git rm --cached <file>`：丢弃工作目录中对文件的修改，将其还原为最近一次提交的状态。  
`git restore <file>`：用于取消暂存区中对文件的修改，将其还原为最近一次提交的状态，并保留工作目录中的修改  
`git restore --staged <file>`：用于停止跟踪某个文件，将其从暂存区中移除，但保留在工作目录中。

### 03 | 实操

#### 3.1 | 设置用户签名和密码

![在这里插入图片描述](https://img-blog.csdnimg.cn/9c5d8489bc814a08a70778c85a93815b.png)  
这里的用户签名和其他地方任何的账号密码都没有关系，这个只是作为你提交代码的一个标识，你在本机上提交代码，提交代码的人就是你设置的签名**Layne**，这只是一个标识。

#### 3.2 | 初始化本地库

> 在桌面新建一个文件`git-demo`,在这个文件里面又新建一个文件`git_space`

![在这里插入图片描述](https://img-blog.csdnimg.cn/efb8f6dbf0694484b5b142dcc1abe230.png)

> 接着在这个路径下，启动git bash窗口，输入`git init`命令

![在这里插入图片描述](https://img-blog.csdnimg.cn/860fe743d1c0418ebff4b90cbdc989f0.png)

> 可以看到，该目录下创建了一个`.git`的文件，这个文件放的东西就是用来进行版本控制的。  
> 在window里可以看到如下的文件结构，把**隐藏**的文件**打钩**

![在这里插入图片描述](https://img-blog.csdnimg.cn/22d9f380e9e3435fb4117294ec0e3913.png)

#### 3.3 | 查看本地库状态

> 输入命令`git status`

![在这里插入图片描述](https://img-blog.csdnimg.cn/46af4236b7ca480b9cfd5ec3f03d4aff.png)

> 下面来分析一下这三行输出的文字所代表的意思

![在这里插入图片描述](https://img-blog.csdnimg.cn/cfef0ab2932a43fd91d2fd8e5199c7dc.png)

> 现在在`git_space`下执行下面代码

![在这里插入图片描述](https://img-blog.csdnimg.cn/af4ceead388f4a05bd3b69207ad4ed5f.png)

> 可以看到创建了一个`hello.txt`的文件，里面编写了一些内容。  
> 这时候我们再来看`git status`

![在这里插入图片描述](https://img-blog.csdnimg.cn/b1b134538e7946e7af10ccbba1f0e60f.png)

> 1、前两行文本没有变化，  
> 2、第三行有了改变，意思是，存在没有追踪的文件，下面括号也说了，（使用`git add <文件>`这个这个命令去添加它，然后准备提交），  
> 3、红色的`hello.txt`说明该文件只存在而已，但是没有被追踪。  
> 4、最后一行说了，没有可以添加去提交的东西，但是呢，存在没有追踪的文件（使用`git add`命令去追踪它）

#### 3.4 | 添加文件到暂存区

> 那么我们就使用`git add <filename>`这个命令，添加到暂存区吧~，也就是追踪这个文件。  
> 再使用`git status`命名查看一下状态。

![在这里插入图片描述](https://img-blog.csdnimg.cn/402846a37f7649539140431939eb370d.png)

> 再来分析一下输出的文本  
> 1、没有变化，在master分支上  
> 2、没有提交过东西  
> 3、提交这个改变，可以看到这个`hello.txt`文件变成了绿色，说明我们已经把这个文件添加到暂存区了，已经被追踪了。括号里面写（使用`git rm --cached <file>`命令去取消上一步操作

> 那我们就按照他的提示操作一下吧`git rm --cached hello.txt`  
> 再查看一下状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/0fbc2e0ad3d447928b8673c3294da43a.png)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/4da04b1e903b4dc5ad632862ddb130cd.png)

> *   可以看到，`hello.txt`回到了没有被追踪的状态，可以理解为把这个`hello.txt`文件从暂存区拿出来
> *   这个告诉我们，暂存区的数据既然可以被**添加**，也可以被**删除**（只是移出暂存区）
> *   现在我们重新把`hello.txt`文件添加回去

![在这里插入图片描述](https://img-blog.csdnimg.cn/a91b5140925448029b52ce3a0a5f0e38.png)

#### 3.5 | 提交本地库（赠：查看日志）

这个的意义就是，将**暂存区**的文件添加到**本地库**，形成一个**历史**版本  
基本语法：`git commit -m “备注” <文件名>`

![在这里插入图片描述](https://img-blog.csdnimg.cn/850b8eb457774b51b9df006a0504f91b.png)

> 再来进行查看一下状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/fa4f4bbf2190419cae2b9458ea0435ff.png)

> *   发现这次输出只有两行文本  
>     1、在master分支，这个没变  
>     2、没有可以去提交的东西，工作区已经清空了  
>     对比一下之前的三个文本![在这里插入图片描述](https://img-blog.csdnimg.cn/f702a171a26a4213a5ed912cbe3a54d8.png)  
>     少了No commits yet，这句话说的是“还没有提交过东西”，而现在我们已经提交东西了，所以他就不显示了。

> 这里我们可以使用一个查看版本提交的命名`git reflog`

![在这里插入图片描述](https://img-blog.csdnimg.cn/534753239313428ea248de0fcb076df2.png)

> 解释一下：
> 
> *   0759d50 ：表示提交版本号，由Git自动生成，通常用哈希值表示
> *   (HEAD -> master) ： 表示HEAD这个指针，指向master，也就是我们现在在master这个分支上
> *   HEAD@{0} ： 表示HEAD的一个偏移量，而这个偏移量是{0}，在这个位置进行的提交
> *   commit (initial): first commit ： 你之前提交的时候，输入的备注信息

> 可以再使用`git log`命令，这个命令是查看完整版的日志的

![在这里插入图片描述](https://img-blog.csdnimg.cn/12f2114e1ba04cf58341290340263286.png)

> 解释一下：
> 
> *   commit 操作的一个版本号（这个是一个完整的，而`git reflog`只是截取了一部分的哈希值）,HEAD指针指着master分支
> *   作者：用户名 邮箱 （也就是一开始设置的东西）
> *   提交的日期： 巴拉巴拉
> *   提交的备注信息

#### 3.6 | 文件的修改

> 在`hello.txt`文件中插入修改一下，添加了‘123456’

![在这里插入图片描述](https://img-blog.csdnimg.cn/a882882c9df847dea1c05dc1887e1100.png)

> 再次查看本地库的状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/ec395b9b7ffe493c89453d76a49f34db.png)

> 解释一下：
> 
> *   在master分支
> *   意思是‘更改没有提交到**暂存区**’，也就是没有被追踪  
>     （使用`git add <file>`命令去更新将要被提交的内容）  
>     （使用`git restore <file>`命令去放弃更改在工作目录中）
> *   更改的文件：`hello.txt`，可以看到这个文件变成了红色，说明没有添加到暂存区里
> *   没有添加要提交的更改（使用`git add`或者`git commit -a`）

> 使用`git restore <file>`命令

![在这里插入图片描述](https://img-blog.csdnimg.cn/5fa2b5de3898490d8840dd26ccafe6cc.png)

> 查看状态发现，他提示说，没有东西可以提交，工作区是空的，也就是没有执行过任何操作  
> 再看文件内容，这个‘123456’也给我撤回去

好了~，我们把文件还原吧，把‘123456’重新输入进去，回到执行`git restore`前的状态吧，再进行下面的操作

> 使用`git add`命令添加到暂存区，再看看状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/e4e51e565f65491e940ed093c88388e5.png)

> 意思是，在master分支上，将要提交的更改：  
> （使用`git restore --staged <file>`命令，把文件移出暂存区）  
> 修改了文件：`hello.txt`

> 输入一下命令`git restore --staged <file>`

![在这里插入图片描述](https://img-blog.csdnimg.cn/577bd6cd5ab649069a4902d22d4a589c.png)

> 不知道你有没有发现，回到了之前的使用`git add`的时候

> 对文件进行commit一下吧

![在这里插入图片描述](https://img-blog.csdnimg.cn/a0a47893801a4dac9308e1aeb7ca8e20.png)

> 解释一下：
> 
> *   【master分支， 版本号（哈希值截取）】，备注信息
> *   一个文件修改了，一行添加，一行删除  
>     （Git里面是对行进行处理的，所以你的修改操作，它表示为删除一行，然后新增一行）  
>     \=========================
> *   再次查看状态，这个时候已经没有东西提交啦，而且工作区也干净了

> 执行一下`git reflog`和`git log`查看日志信息

![在这里插入图片描述](https://img-blog.csdnimg.cn/6999097888b343d7936e4a05c0c20e47.png)

> 解析一下：
> 
> *   可以看到第一行的备注信息为上一次提交，也就是第二次提交，HEAD的偏移量为0，而上一次的偏移量为1了，同时也可以看出，这个HEAD指针指向master分支的同时，指向第二个提交版本

#### 3.7 | 历史版本和版本穿梭

> 先再进行一个文件修改，然后提交

![在这里插入图片描述](https://img-blog.csdnimg.cn/e95558b38c7b48779d020c471c6860c0.png)

> 此时有三个被提交的版本了

![在这里插入图片描述](https://img-blog.csdnimg.cn/bab1fc21e2404f6892520ba22a4af25a.png)

> 文件改了之后，我想要回到任何一个提交的版本怎么办呢？  
> 可以使用`git reset --hard <版本号>`

![在这里插入图片描述](https://img-blog.csdnimg.cn/c358892b10c846b0b9e87073f2660a3c.png)

> 解释一下：
> 
> *   文本输出，这个HEAD指针现在指向了我们输入的版本号，备注是第二次提交
> *   查看一下日志
> *   HEAD指针指向了master分支，然后是第二次提交的版本

> 再看一下文件内容，已经是回到了之前的状态了

![在这里插入图片描述](https://img-blog.csdnimg.cn/fdc02a215e7b4ba6abce3cab89d85d75.png)

> 其实你想要切换到哪里都可以，只需要带上版本号就行  
> 底层其实是指针的移动操作

![在这里插入图片描述](https://img-blog.csdnimg.cn/8c3b447f9df64731ac05702cdb2f9e0b.png)

> 图说明了，这三个版本同时存在，只要master指向哪里，就是哪个版本。

持续更新中。。。。，你的支持是作者的动力噢~

 

文章知识点与官方知识档案匹配，可进一步学习相关知识

[算法技能树](https://edu.csdn.net/skill/algorithm/?utm_source=csdn_ai_skill_tree_blog)[首页](https://edu.csdn.net/skill/algorithm/?utm_source=csdn_ai_skill_tree_blog)[概览](https://edu.csdn.net/skill/algorithm/?utm_source=csdn_ai_skill_tree_blog)62043 人正在系统学习中

本文转自 <https://blog.csdn.net/weixin_49113403/article/details/131733580>，如有侵权，请联系删除。