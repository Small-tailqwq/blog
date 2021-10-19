---
layout: post  
title: Real-ESRGAN脚本
categories: 笔记
tags: 图像处理
author: ko_teiru
---


* content
{:toc}

> 前段时间在群里看见有人聊这玩意，说是比wifu2x还牛，就上GitHub看了看。






前段时间在群里看见有人聊这玩意，说是比wifu2x还牛，就上GitHub看了看。发现直接下下来解压一下就能用，可惜没有图形化界面，只能自己一行一行敲cmd指令，还是比较麻烦的，特别是处理图片还得复制路径啥的。  

于是自己就写了个bat脚本，直接把图片拖脚本图标上打开就行。你也可以给脚本创建一个 `桌面快捷方式` ，一样可以直接拖上去打开。  

说一下要注意的吧，Real-ESRGAN 其实原本就是支持批量处理的，只要一个文件夹内存放需要处理的图片，把这个文件夹的路径当作 `i` 输入即可，`o`的话也得是一个已经存在的文件夹。

我这个脚本支持图片与文件夹输入，只要把图片或者文件夹拖上去，没有问题的话会在原文件所在路径生成 `文件名+所选模型` 命名的图片或者文件夹。另外图片或文件夹名称中含有特殊符号和空格也支持处理，这个问题处理了一会，还找了不少资料，主要是bat这东西没有别的语言来得方便（单纯我菜不会用）。

目前应该算是2.5的版本了，感谢口几口大师的指导。以下是源码，复制粘贴到新建文本文档把后缀名改成 `.bat` **并且**把文件放至 `Real-ESRGAN` 根目录即可。目前可选的设置为GPU与数据模型，默认GPU为0，模型为动漫模型。 

```bash
@echo off
title 这里是标题daze~
echo ==============================================================
echo =               目前支持直接拖入.JPG与.PNG的文件               =
echo =          或者直接拖入一个包含图像文件的文件夹                 =
echo =            脚本会自动创建一个文件夹存放输出文件               =
echo =      如果你是拖入的文件，则会在源文件下新建一个文件            =
echo =               随便写的，并不是很懂bat文件                    =
echo =    源码仓库————》 https://github.com/xinntao/Real-ESRGAN    =
echo =               by：blog.hayasa.xyz                          =
echo ==============================================================
set file=%1
rem 检测文明名是否有空格，如果文件名存在空格，则%1会自动添加""，如果没有，则不会
if %file% neq %file: =% (
    set s1=包含空格
) else (
    set file="%file%"
    set s1=不包含空格
)

rem echo %file%
rem pause
set /p g=请输入GPU设备编号:
if "%g%"=="" (
   echo [信息] 使用默认设备
   set g=0
) else (
    set g=%g%
)
rem 《--------------模型开始-------------》
echo 请输入模型，默认为realesrgan-x4plus-anime
echo 1.realesrgan-x4plus	2.realesrgan-x4plus-anime
set /p n= 
if "%n%"=="1" (
   set n=realesrgan-x4plus
) else (
    echo [信息] 使用realesrgan-x4plus-anime
    set n=realesrgan-x4plus-anime
)
rem 《--------------模型结束-------------》
rem 判断输入文件为文件夹还是文件
if exist %file%\* (
	goto folder
) else if exist %file% (
	goto file
) else (
	goto exit
)

:folder
rem echo [信息] 输入为目录
set s2=目录
set o=%file:~0,-1%-%n%"

rem echo 输入路径为：%file%
rem echo 输出路径为：%o%
echo [信息] 目标是%s1%的%s2%，输入路径为：%file%，输出路径为：%o%
pause
md %o%
.\realesrgan-ncnn-vulkan.exe -i %file% -o %o% -g %g% -n %n%
goto exit


:file
set s2=文件
set o=%file:~0,-5%
set tpye=%file:~-5,5%
set o=%o%-%n%%tpye%
rem echo 输入路径为：%file%
rem echo 输出路径为：%o%
echo [信息] 目标是%s1%的%s2%，输入路径为：%file%，输出路径为：%o%
pause
.\realesrgan-ncnn-vulkan.exe -i %file% -o %o% -g %g% -n %n%

goto exit

:exit
echo 输出路径为%o%
echo 退出


pause

```



目前的问题：

- 不能重复处理，建议处理完第一次图片后不直接关闭，整体写一个循环，后续处理直接把图片往cmd窗口拖就直接处理
- 未对输入值进行排查，例如选择GPU时，如果输入了错误的值，将导致程序报错
- 原程序进度显示百分比，是否可以采用=======这种可视化
- 想不到了，也许可以换语言重构，不过最近也没时间了，感觉自己脑子还是不适合敲代码  
