---
categories: Notebook
layout: single
classes: wide
title: Interaction between WSL and Windows
---

# 1.How to

- Offical How-to:  
<https://docs.microsoft.com/en-us/windows/wsl/interop>  


- Several ways to use or start windows application in WSL command line:  
Reference: <https://www.cnblogs.com/mushroom/p/8969338.html>  

<1> Use `application-name.exe` directly. `.exe` is necessary.  
Note: Please ensure that the installation path of application is in the Environment Variable.  
If don't want to add .exe and use the command like Linux, you can set alias in .bashrc or .zshrc. For example, `alias mspaint=mspaint.exe`. Or copy the `application-name.exe` and paste it into the same directory, then rename the pasted one as `application-name`.

<2> Let cmd.exe or powershell.exe to take over the command. Just using `application-name` is OK.  
Note: Please ensure that the installation path of application is in the Environment Variable.  
`command_not_found_handle` is function of bash 4.0+. This function will be called if the command is not found. Use cmd.exe or powershell.exe to run the command that is not found by bash.  

Add the following code into .bashrc(cmd.exe can be replaced with powershell.exe):  
```
command_not_found_handle() {
    if cmd.exe /c "(where $1 || (help $1 |findstr /V Try)) >nul 2>nul && ($* || exit 0)"; then
        return $?
    else
        if [ -x /usr/lib/command-not-found ]; then
           /usr/lib/command-not-found -- "$1"
           return $?
        elif [ -x /usr/share/command-not-found/command-not-found ]; then
           /usr/share/command-not-found/command-not-found -- "$1"
           return $?
        else
           printf "%s: command not found\n" "$1" >&2
           return 127
        fi
    fi
}
```

Or add the following code into .zshrc if you use zsh:  
```
command_not_found_handler() {
    if cmd.exe /c "(where $1 || (help $1 |findstr /V Try)) >nul 2>nul && ($* || exit 0)"; then
        return $?
    else
        [[ -x /usr/lib/command-not-found ]] || return 1
        /usr/lib/command-not-found --no-failure-msg -- ${1+"$1"} && :
    fi
}
```

<3> Link the application of Host to WSL.  
For example, `ln -sf /mnt/c/Program\ Files/application-name.exe /usr/bin/application-name`  


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
