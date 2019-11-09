---
layout: post
title:  "如何使用Github来搭建一个自用图床"
categories: 教程
tags: Github 图床
author: Small_tail
---

* content
{:toc}

## 什么是图床？ 
图床，是专门储存图片的空间，同时允许你为图片创建链接的网上空间,图床指储存图片的服务器。  
望文生义的话那就图片的床啦~想象一下，你写`markdown`的时候，要调用一张图片，你就可以把躺在床上的图片拿出来用（挺奇怪的比喻...）

## 免费的图床 
免费的图床还挺多的，比如[sm](sm.ms)。我测试页的island的图就是调用的sm里的。  
不过sm里的图片好像会公开，假如要使用一些不太好意思的图片可能有点难受，再加上  
> 免费图床仅供分享图片使用，我们保留随时删除图片并举报上传违规图片者的权利  

所以还挺不自在的...那既然博客都是用的Github，那图床也干脆用GitHub的得了，白嫖嫖到低嘛~~~~/cy~~  




## 搭建步骤 
1. 在GitHub新建一个新储存库，用来保存和调用图片  
仓库名场随意，个人认为短点方便，比如`img`。可以选择公开或者私密，这里得选择公开，不然之后链接直接会404。  
2. **这一步可以忽略**[^1] 创建完新的库之后，新建一个文件夹，用来区分图片。当然，GitHub上并没有新建文件夹的选项，你得点击新建文件  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img007.JPG)  
输入你所想的分类，这里我填的blog（被chrome自己翻译了..有时候编辑文件提交前记得把翻译关掉，不然文件可能会乱跑）  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img008.JPG)  
输入完了之后再加个斜杠`/`就行，现在就新建了一个名为`blog`的文件夹了。但是还まだまだ，继续再输入`1.md`。这时提交按钮才会变成绿色，即使你的1.md里什么也没有。  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img009.JPG)  
3. 这里要使用到一个小工具：`PicGo`这玩意也在GitHub上开源了，可以走下面那个链接去瞧瞧~  
- 下载[PicGO](https://github.com/Molunerfinn/PicGo)这里选择对应你自己系统的版本进行下载  
- 图床设置——Github图床设置  
- **仓库名**填`用户名/仓库`，比如我这个就是`small-tailqwq/img`这里的**github.com的域名不必填入**  
- **分支名**一般**不用管**，填`master`就行  
- **Token**的话需要到Github的账号设置里生成，步骤如下：  
* 右上角头像——设置 
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img001.JPG)
* 个人设置一栏找到最下方的开发人员设置。注意，这里需要输入你的密码确认身份  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img002.JPG)
* 开发人员设置一栏找到同样是位于最下的个人访问令牌  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img003.JPG)  
<p align="center">点击生成新令牌</p>

* 这里需要填写令牌的用途，当然，这是为了你自己以后能够分辨而填的~~可以随便填~~  
权限的话选择第一个`repo`就行，别的不用勾  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img004.JPG)
* 生成令牌  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img005.JPG)
* 点击复制——到PicGo里面粘贴就大功告成了  
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/img006.JPG)  
*这个已经被我`DEL`啦qwq*  
4. 3其实是我直接把我那图床自述文件搬过来了，毕竟懒得写~~ 
这里说一下为什么说2可以忽略，[^1] PicGo的GitHub图床设置里面有一个是设定指定路径，也就是说可以通过小工具创建文件夹。  
再说图床的话一般人都懒得分类吧？（可能只有我是懒狗？？）  
5. 万事大吉，直接把图片拖入上传区，支持多张上传。  
另外已经上传了的图片可以通过`相册`进行查看和复制链接。这东西复制好了就直接是markdown的格式，挺舒服的qwq  

**~~另外GitHub库的私密和公开好像不影响图床的使用（大概~~**已经确认了…私密不能外部访问，所以图片直接404…



