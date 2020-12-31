---
categories: Notebook
layout: single
classes: wide
title: Advanced Package Tool (apt) of Ubuntu uses domestic source mirror
---

# 0.What is Apt?

Advanced Package Tool (or APT), the main command-line package manager for Debian and its derivatives. It provides command-line tools for searching, managing and querying information about packages, as well as low-level access to all features provided by the libapt-pkg and libapt-inst libraries which higher-level package managers can depend upon.

# 1.Basic command of apt:

- apt install [software]: Install software
- apt remove [software]:  Uninstall software
- apt update: Only check anything can update
- apt upgrade:  Update the software installed

# 2.Use domestic source mirror

Use domestic to speed up software downloading and installing process.

## 2.1.Backup Ubuntu offical source list.

`sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak`

## 2.2.About sources.list file.

`# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to newer versions of the distribution.`

#: Comments

`deb http://archive.ubuntu.com/ubuntu/ focal main`

|Part1 |Part2                              |Part3_1-Part3_2  |Part4 |
|---   |---                                |---              |---   |
|deb   |http://archive.ubuntu.com/ubuntu/  |focal-security   | main |

Part1  
deb: binary package repository  
deb-src: source package repository.  
  
Part2  
URL: URL of Ubuntu soure mirror  

Part3_1  
focal: Codename of Ubuntu. Use `lsb_release -sc` to check the codename.  
Part3_2  
```
security  - Important Security Updates.  
updates   - Recommended Updates.  
proposed  - Pre-released Updates.  
backports - Unsupported Updates.  
```

Part4  
main: Canonical-supported free and open-source software. Canonical is Ubuntu’s parent company, and they provide official support for all the software packages in Main.  
restricted: Officially Supported, Closed-Source Software  
universe: Community-Maintained, Open-Source Software  
multiverse: Unsupported, Closed-Source and Patent-Encumbered Software  

## 2.3.Change the URL of source mirror.

`sudo vim /etc/apt/sources.list`

Replace the all offical URL <http://us.archive.ubuntu.com/ubuntu/> with the URL of domestic source mirror.

Domestic source mirror:

|  Organisation     |  Url                                           |
|  ---              |  ---                                           |
|  Ali              | <http://mirrors.aliyun.com/ubuntu/>            |
|  Tsinghua         | <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> |
|  NetEase          | <http://mirrors.163.com/ubuntu/>               |
|  USTC             | <https://mirrors.ustc.edu.cn/ubuntu/>          |

For example,  

former source:
`deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted`

newer source:
`deb http://mirrors.aliyun.com/ubuntu/ focal main restricted`

# 3.Start using domestic source mirror.

`sudo apt update`
