# CheatSheet

This cheat sheet contains the commands that I use on a daily basis. Most of the
commands have been covered in the notes section.

## Terminal Commands

**==Ctrl + c==** - terminate the current running program

**==Ctrl + z==** - suspend the current running program

**==fg==** - bring back to foreground

**==bg==** - finish running in background

**==cd==** - change directory

**==ls==** - list content of a directory

**==pwd==** - print current working directory

**==rm -rf==** - delete directory (beware)

**==mkdir==** - make directory

**==mv==** - move or rename files

**==cp==** - copy files

**==cat==** - print content to screen

**==tmux==** - more explanation below

## Vim Commands (Basics not included)

All commands below are for normal mode.

### Global Commands

**==:q!==** - quit, don't save

**==:wq==** - write and quit

**==/word==** - find word

**==gg=G==** - format all lines

### Editing Commands

**==u==** - copy line

**==yy==** - copy line

**==dd==** - delete line (works as a "cut" also)

**==p==** - paste line

**==2yy==** - copy 2 lines (can change number for more lines & works with the
other commands above too)

### Movement Commands (h,j,k,l left, down, up, right)

**==0==** - jump to the start of the line

**==$==** - jump to the end of the line

**==gg==** - go to first line of document

**==5gg==** - go to line 5

### Multiple files

**==:e file==** - edit file in new buffer

**==:bn==** - next buffer

**==:bp==** -previous buffer

**==:bd==** - delete buffer

**==:ls==** - list all buffers

**==:sp file==** - open a file in a new buffer and split window

**==:vs file==** - open a file in a new buffer and vertically split window

**==Ctrl + wh==** - move cursor to the left window (vertical split)

**==Ctrl + wl==** - move cursor to the right window (vertical split)

**==Ctrl + wj==** - move cursor to the window below (horizontal split)

**==Ctrl + wk==** - move cursor to the window above (horizontal split)

Notice how changing the letter after **==Ctrl + w + (h, j, k, l)==** controls
the direction you move your cursor to.

## Tmux

**==tmux==** - to open tmux

All commands below are prefixed with `Ctrl + b` read the [guide](tmux.md) for
more details.

### Windows

**==c==** - create window

**==&==** - close window

**==p==** - previous window

**==n==** - next window

**==0 ... 9==** - select window by number

### Panes

**==%==** - split pane vertically

**=="==** - split pane horizontally

**==arrow keys==** - switch to pane to the direction

**==z==** - toggle pane zoom (fullscreen pane)

**==!==** - convert pane into a window

**==x==** - close current pane
