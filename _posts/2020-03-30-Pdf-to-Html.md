---
layout:     post
title: "pdf2htmlEX 使用方法"
subtitle:   " \"高保真PDF至HTML转换\""
date: 2020-03-30 14:00:00 +0800
author:   "Yummy"
category: pdf2htmlEX 
catalog: true
tags:
    - pdf2htmlEX 
    - Yummy
---

本文参考:

[Pdf2html ：高保真PDF至HTML转换](http://wangying.sinaapp.com/archives/2352)[windows系统下的 pdf2html （pdf 转html）开源工具 pdf2htmlEX 使用方法](https://blog.csdn.net/weixin_44603744/article/details/86596082)

# pdf2htmlEX介绍

传统pdf2html有两种：
一种相当于pdf2text加一些比较弱的格式，基本跟pdf2text也差不了多少
另一种是把所有渲染成图片然后嵌到一个html,结果是文字信息都丢失（不能选择，拷贝），生成的文件还巨大。
pdf2htmlEX结合二者优点，既保留了文字，又保留了格式。
具体来说有如下特性
1.从pdf提取字体
2.保证渲染准确性，针对web进行优化（包括减少文件大小，文字行合并，（为HTML文字选择）字体重编码等等）
3.其他内容用图片显示
4.单文件输出，一个HTML搞定一切
[pdf2htmlEX开源主页地址](https://github.com/coolwanglu/pdf2htmlEX)、[详细介绍](https://github.com/coolwanglu/pdf2htmlEX#-pdf2htmlex)、[中文讨论组](https://groups.google.com/forum/#!forum/pdf2htmlex-cn)、[windows系统可执行版下载地址](http://soft.rubypdf.com/software/pdf2htmlex-windows-version)

**Download**

- [pdf2htmlEX-win32-0.14.6-upx-with-poppler-data.zip](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-win32-0.14.6-upx-with-poppler-data.zip) (pdf2htmlEx.exe is packed with **[UPX ](http://upx.sourceforge.net/))**
- [pdf2htmlEX-win32-0.14.6-with-poppler-data.zip](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-win32-0.14.6-with-poppler-data.zip)
- [pdf2htmlEX-win32-0.13.6](http://soft.rubypdf.com/wp-content/uploads/2013/08/pdf2htmlEX-win32-0.13.6.zip)
- [pdf2htmlEX v0.12-win32-static](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-0.12-win32-static-with-poppler-data.zip)
- pdf2htmlEX v0.11 (bases on [v0.11](https://github.com/coolwanglu/pdf2htmlEX/releases/tag/v0.11) release version)
  [pdf2htmlEX-v0.11-win32-static(without poppler encoding data)](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-0.11-win32-static.zip)
- [pdf2htmlEX-v0.11-win32-static-with-poppler-data](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-0.11-win32-static-with-poppler-data.zip)
  ~~[pdf2htmlEX-v0.11-win32-static(without poppler encoding data)](http://soft.rubypdf.com/wp-content/uploads/2013/08/pdf2htmlEX-v0.11-win32-static.zip)~~
- [pdf2htmlEX-v0.11-win32-static-with-poppler-data](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-v0.11-win32-static-with-poppler-data.zip)
- ~~[pdf2htmlEX-v1.0-win32-static](http://soft.rubypdf.com/software/pdf2htmlex-windows-version/attachment/pdf2htmlex-v1-0-win32-static)~~
- ~~[pdf2htmlEX-v0.9-win32-static](http://soft.rubypdf.com/software/pdf2htmlex-windows-verion/attachment/pdf2htmlex-v0-9-win32-static)~~

P.S.

作者是 [Lu Wang](https://github.com/coolwanglu)，原始项目和源代码是 [pdf2htmlEX](https://github.com/coolwanglu/pdf2htmlEX)，

我只是做了一些修改并针对Windows进行了编译，修改后的源代码在[这里](https://github.com/witwall/pdf2htmlEX) 。

# 使用方法

因为这里编译过程比较复杂，可以参考：[Pdf2html ：高保真PDF至HTML转换](http://wangying.sinaapp.com/archives/2352)

**解压**

我选择了直接解压安装包

下载：[pdf2htmlEX-win32-0.14.6-upx-with-poppler-data.zip](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-win32-0.14.6-upx-with-poppler-data.zip) 

或者：[pdf2htmlEX-win32-0.14.6-with-poppler-data.zip](http://soft.rubypdf.com/download/pdf2htmlex/pdf2htmlEX-win32-0.14.6-with-poppler-data.zip)

将其解压(解压的目录一定不要包含中文路径！)

**放置Pdf**

将需要转换的pdf文件放入pdf2htmlEX的解压目录

- data
- test
- **`abc.pdf`**
- AUTHORS
- ChangeLog
- LICENSE
- LICENSE_GPLv3
- pdf2htmlEx.exe
- README.md

**运行pdf2htmlEX**

使用[命令提示符](https://baike.baidu.com/item/CMD命令/9684689?fr=aladdin)进入pdf2htmlEX的解压目录

```powershell
cd d:\pdfex
d:
```

执行cmd命令调用pdf2htmlex进行转换：

```powershell
pdf2htmlex --zoom 1.8 abc.pdf
```

执行完毕后，会在同目录下生成与pdf同名的html文件

```powershell
D:\pdfex>pdf2htmlex --zoom 1.8 abc.pdf
Preprocessing: 750/750
Working: 3/750

```

最后会在目录下生成：

**`abc.html`**

# 简单的脚本

为了方便使用，我尝试了使用批处理脚本语言来完成这个工作，不用每次手动打开CMD窗口。

~~~bash
# test.bat
```bash
cd /d %~dp0

@echo off

set /P htmltname=Please input your file path : 

:: echo "%htmltname%"

set /P c=Choose the mode (1/2) ?  
if /I "%c%" EQU "1" goto one
if /I "%c%" EQU "2" goto two


:one
pdf2htmlEX.exe --zoom 1.8   "%htmltname%"
echo Generate one finished!
goto end

:two
pdf2htmlEX.exe --embed cfijo --dest-dir out "%htmltname%"
echo  Generate two finished!
:end

@echo Please open file path
start /min "" "%~dp0"

pause

```
cd /d %~dp0

@echo off

set /P htmltname=Please input your file path : 

:: echo "%htmltname%"

set /P c=Choose the mode (1/2) ?  
if /I "%c%" EQU "1" goto one
if /I "%c%" EQU "2" goto two


:one
pdf2htmlEX.exe --zoom 1.8   "%htmltname%"
echo Generate one finished!
goto end

:two
pdf2htmlEX.exe --embed cfijo --dest-dir out "%htmltname%"
echo  Generate two finished!
:end

@echo Please open file path
start /min "" "%~dp0"

pause

~~~

使用方法如下：

```powershell
E:\Github\pdf2html>cd /d E:\Github\pdf2html\
Please input your file path : svg_background_with_page_rotation_issue402.pdf
Choose the mode (1/2) ?  1
Preprocessing: 1/1
Working: 1/1

Generate one finished!
Please open file path
请按任意键继续. . .
```

1. 将pdf文件拷贝至`E:\Github\pdf2html`（视个人情况而定）
2. 点击后只需要将你想要的pdf文件名复制进去
3. 选择模式：`生成一个单独的html文件`、`生成 一个文件夹里面包含html 的元素`





注意：其中还是存在bug，我并未提及。我遇见的是生成比较大的pdf会提示：

```powershell
E:\Github\pdf2html>cd /d E:\Github\pdf2html\
Please input your file path : test.pdf
Choose the mode (1/2) ?  1
Preprocessing: 189/189
Lookup 'mark' Mark Positioning in Arabic lookup 1 has an
offset bigger than 65535 bytes. This means
FontForge must use an extension lookup to output it.
Not all applications support extension lookups.
Lookup 'mark' Mark Positioning in Arabic lookup 0 has an
offset bigger than 65535 bytes. This means
FontForge must use an extension lookup to output it.
Not all applications support extension lookups.
Lookup 'mark' Mark Positioning in Arabic lookup 1 has an
offset bigger than 65535 bytes. This means
FontForge must use an extension lookup to output it.
Not all applications support extension lookups.
Lookup 'mark' Mark Positioning in Arabic lookup 0 has an
offset bigger than 65535 bytes. This means
FontForge must use an extension lookup to output it.
Not all applications support extension lookups.
Lookup 'mark' Mark Positioning in Arabic lookup 1 has an
offset bigger than 65535 bytes. This means
FontForge must use an extension lookup to output it.
Not all applications support extension lookups.
^C终止批处理操作吗(Y/N)?
```

以后有机会再仔细研究。

