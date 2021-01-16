---
categories: Notebook
layout: single
classes: wide
title: Compiling and install tesseract-ocr engine and training tools
---

# 0.What is tesseract-ocr?

- Offical introduction:

<https://github.com/tesseract-ocr/tesseract>

# 1.Compilation guide:

<https://tesseract-ocr.github.io/tessdoc/Compiling.html>

Only clone one tag that you want to use is OK:  
`git clone --branch tag-name --depth 1 https://github.com/tesseract-ocr/tesseract.git`

![tag-name](https://pengfei-zheng.github.io/assets/images/notebook/tag-name.png)  

# 2.Running Tesseract

Basic [command line usage](https://tesseract-ocr.github.io/tessdoc/Command-Line-Usage.html):  

`tesseract imagename outputbase [-l lang] [--oem ocrenginemode] [--psm pagesegmode] [configfiles...]`

The text result is in outputbase file in current folder.  

For more information about the various command line options use tesseract --help or man tesseract.

Examples can be found in the [documentation](https://tesseract-ocr.github.io/tessdoc/Command-Line-Usage.html#simplest-invocation-to-ocr-an-image).
