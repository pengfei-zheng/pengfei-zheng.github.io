---
categories: Notebook
layout: single
classes: wide
title: pip uses domestic source mirror
---

# 0.What is pip?

pip is the package installer for Python. You can use pip to install packages from the Python Package Index and other indexes.  

Offical website:  
<https://pypi.org/project/pip/>

# 1.Basic command of pip  

| Command                            | Function                                                         |
| ---                                | ---                                                              |
| pip --version                      | check pip version                                                |
| pip --help                         | get help                                                         |
| pip install -U pip                 | upgrade pip                                                      |
| pip install package-name           | install package                                                  |
| pip install package-name==1.0      | install specified version of package                             |
| pip install 'package-name>=1.0'    | install package whose version is above or equal to specified one |
| pip install --upgrade package-name | upgrade package                                                  |
| pip uninstall package-name         | uninstall package                                                |
| pip search package-name            | search package                                                   |
| pip show package-name              | show the inforamtion of package                                  |
| pip list                           | list all intalled package                                        |
| pip list -o                        | list the intalled package that can upgrade                       |


# 2.Domestic source mirror URL

Domestic source mirror:

| Organisation | URL                                        |
| ---          | ---                                        |
| Ali          | <http://mirrors.aliyun.com/pypi/simple/>   |
| douban       | <http://pypi.douban.com/simple/>           |
| Tsinghua     | <https://pypi.tuna.tsinghua.edu.cn/simple> |

# 3.Use domestic source mirror temporarily

Use domestic source mirror temporarily to speed up software downloading and installing process.  

`pip install package-name -i URL_of_source_mirror`

For example,  

`pip install package-name -i https://pypi.tuna.tsinghua.edu.cn/simple`

# 4.Set domestic source mirror as default source

`pip config set global.index-url URL_of_source_mirror`

For example:

`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`

Then pip will get the package from domestic source mirror when you use pip to manage package.
