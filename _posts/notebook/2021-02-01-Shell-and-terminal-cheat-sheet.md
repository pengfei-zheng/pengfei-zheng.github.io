---
categories: Notebook
layout: single
classes: wide
title: Shell and Terminal Cheat Sheet
---

# 0.What is shell and terminal?

In unix terminology,  

 - terminal = tty = text input/output environment. For example, `Windows Terminal`, `iTerm2`  
 - console = physical terminal  
 - shell = command line interpreter. For example, `bash`, `zsh` and `fish`.  

# 1.Move cusor  

| Shortcut | Function                          |
| ---      | ---                               |
| CTRL + A | Move to the beginning of the line |
| CTRL + E | Move to the end of the line       |
| ALT  + B | Move one word backward = CTRL + ← |
| ALT  + F | Move one word forward  = CTRL + → |
| CTRL + B | Move one character backward       |
| CTRL + F | Move one character forward        |

# 2.Delete/cut  

| Shortcut | Function                                                                |
| ---      | ---                                                                     |
| CTRL + U | Cut/delete the entire line                                              |
| CTRL + K | Cut/delete the characters on the line after the current cursor position |
| CTRL + W | Cut/delete the word in front of the cursor                              |
| CTRL + H | Delete     the character in the front of the cursor = Backspace         |
| ALT  + D | Cut/delete the word after the cursor = Delete                           |
| CTRL + D | Delete     the character on the cursor position                         |

# 3.Paste  

| Shortcut | Function |
| ---      | ---      |
| CTRL + Y | Paste    |

# 4.Edit  

| Shortcut | Function                                                                |
| ---      | ---                                                                     |
| ALT  + T | Exchange two words in front of the cursor                               |
| CTRL + T | Exchange two characters in front of the cursor                          |
| ALT  + U | Transform the characters in the word after the cursor to capital letter |
| ALT  + I | Transform the characters in the word after the cursor to lower case     |
| CTRL + _ | Undo the last change                                                    |

# 5.Kill, Exit, Suspend

| Shortcut | Function                                                                                        |
| ---      | ---                                                                                             |
| CTRL + C | Kill current process                                                                            |
| CTRL + D | Exit shell                                                                                      |
| CTRL + Z | Suspend/stop current foreground process                                                         |
| fg       | Restore the process suspended. fg %jobsnumber: restore the process through jobsnumber           |
| bg       | Continue process in background bg %jobsnumber: hide the process to backgrund through jobsnumber |
| jobs     | Show the processes running in background                                                        |


# 6.Screen output  

| Shortcut | Function                                                |
| ---      | ---                                                     |
| Ctrl + L | Clear screen                                            |
| Ctrl + S | Stop output to screen                                   |
| Ctrl + Q | Re-enable screen output                                 |
| &        | Add at the command's end, execute command in background |

# 7.Command history  

| Shortcut | Function                                           |
| ---      | ---                                                |
| !!       | Execute last command in history                    |
| !abc     | Execute last command in history beginning with abc |
| !abc:p   | Print last command in history beginning with abc   |
| Ctrl + P | Execute previous command in history                |
| Ctrl + N | Execute next command in history                    |
| Ctrl + R | Search history                                     |
| CTRL + G | Escape from search mode                            |

# 8.Scroll screen (for Windows Terminal)  

| Shortcut            | Function                 |
| ---                 | ---                      |
| ctrl + shift + ↑    | scroll up                |
| ctrl + shift + ↓    | scroll down              |
| ctrl + shift + pgup | scroll up   a whole page |
| ctrl + shift + pgdn | scroll down a whole page |

