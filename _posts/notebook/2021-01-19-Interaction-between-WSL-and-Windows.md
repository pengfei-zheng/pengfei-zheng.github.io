---
categories: Notebook
layout: single
classes: wide
title: Interaction between WSL and Windows
---

# 1.How to

- Offical How-to:

<https://docs.microsoft.com/en-us/windows/wsl/interop>

# 2.WSL+Windows Terminal+Vim

## 2.1.Use the content yanked from vim in widows:
```vim
"WSL yank support
let s:clip = '/mnt/c/Windows/System32/clip.exe'
if executable(s:clip)
    augroup WSLYank
        autocmd!
        autocmd TextYankPost * if v:event.operator ==# 'y' | call system(s:clip, @0) | endif
    augroup END
endif
```

## 2.2.Select the content in clipboard of windows and paste the selected one into vim of WSL:  
(1)Change the shortcut for paste in windows terminal:  
```json
    "keybindings":
    [
        // Copy and paste are bound to Ctrl+Shift+C and Ctrl+Shift+V in your defaults.json.
        // These two lines additionally bind them to Ctrl+C and Ctrl+V.
        // To learn more about selection, visit https://aka.ms/terminal-selection
        //{ "command": {"action": "copy", "singleLine": false }, "keys": "ctrl+c" },
        { "command": "paste", "keys": "ctrl+v" }
    ]
```
(2)Press "win+v" to show the history of copy and select the appropriate one to paste into vim.  
![CopyHitory](https://pengfei-zheng.github.io/assets/images/notebook/vim-uses-clipboard-of-windows.png)  
(3)The shortcut of vim's block selection will be changed as "ctrl+alt+v" in windows terminal by default.  

# 3.Convert the file path to let the exe of windows to open the file normally in WSL's command line  
```shell
#!/bin/bash
wslpath=$1
starter1=${wslpath:0:1}
starter2=${wslpath:0:2}

if [ "$wslpath" != "" ]
then
  # Only filename.
  if [ $starter1 != \. -a $starter1 != \/ -a $starter1 != \~ ]
  then
    filepath=$wslpath
  fi
  
  # File path is Relative Path.
  if [ $starter2 = \.\/ -o $starter2 = \.. ]
  then
    filepath=$wslpath
  fi
  
  # Path is started wiht Home path "~".
  if [ $starter2 = \~\/ ]
  then
    filepath=\/\/wsl$\/Ubuntu-20.04\/home\/oppenheimer\/$wslpath
  fi
  
  # Path is started with "/mnt".
  if [ $starter1 = \/ -a ${wslpath:0:4} = \/mnt ]
  then
    deletemnt="${wslpath#\/mnt\/}"
    filepath="${deletemnt:0:1}:${deletemnt:1:#deletemnt}"
  fi
  
  # Path is absolute path and not started with "/mnt/"
  if [ $starter1 = \/ -a ${wslpath:0:4} != \/mnt ]
  then
    filepath=\/\/wsl$\/Ubuntu-20.04$wslpath
  fi
  
  echo $filepath
fi
```
