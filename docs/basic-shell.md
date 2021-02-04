# Unit 1: Terminal and Shell

## What is a Shell?

The term CLI refers to a type of user interface. To realize this interface, Unix
computing environments rely on another type of program called _shell_.

A shell usually works closely with a terminal to get inputs from the users,
interpret the meaning of the inputs, execute the tasks (perhaps through the
invocation of other programs), and returned the output back to the user through
the terminal.

Note that a shell can run on its own without a terminal (it can read input from
a file, and write the output to a file, for instance).

## Command Prompt

A shell has a _command prompt_. It typically looks something like this, but will
be different depending on the default configuration on your machine:

```
name@pe111:~$
```

The prompt is where you type in a command for the shell to interpret and
execute.

In `bash`, the command prompt can be customized to include information such as
the username, hostname, time, current working directory, etc. It is customary to
use the `$` sign as the final character of the prompt. In our examples, we will
just show `$` to incidate the command prompt.

## Terminal Control Sequence

The following lists some of the most useful control sequences to know:

++control+d++ : signal the end of input to a program. This is also used to exit
from a shell (by telling the shell that you have no more input to send and you
are done with it).

++control+z++ : suspend the current running program. This _pauses_ the execution
of the program (but not terminating it). In the `bash` shell, the most recently
suspended program can resume executing in the background with the command `bg`
or brought back to execution in the foreground again with the command `fg`.

++control+c++ : terminate the current running program.

++control+s++ : freeze the terminal. This is a legacy control command that
pauses the output printing of a teletype machine. You shouldn't need to use this
control sequence.

++control+q++ : resume the terminal. This is a legacy control command that
resume the printing of a teletype machine. You shouldn't need to use this
control sequence, unless you accidentally hit ++control+s++

!!! note "++control+z++ vs. ++control+c++" A common mistake for new students is
to hit ++control+z++ frequently if something goes wrong with their program --
this behavior leads to large number of suspended programs (which still occupy
resources such as memory on the computer). The right sequence to use is
++control+c++ -- which terminates the program (and frees up the resources).

!!! note "++control+s++ accidents" Since ++control+s++ is used as the "save"
shortcut in non-Unix environment, many students accidentally hit this control
sequence, causing their terminal to freeze. Don't panic if this happens. Just
hit ++control+q++ and things will be back to normal.

## Windows Terminal (Sorry Mac users)

For windows, a great extension that all programmers should have is the Windows
Terminal.

Windows Terminal is a modern terminal application for users of command-line
tools and shells like Command Prompt, PowerShell, and Windows Subsystem for
Linux (WSL). Its main features include multiple tabs, panes, Unicode and UTF-8
character support, a GPU accelerated text rendering engine, and the ability to
create your own themes and customize text, colors, backgrounds, and shortcuts.

To download and get started with windows terminal, click and follow the
instructions on the following link:
https://docs.microsoft.com/en-us/windows/terminal/get-started
