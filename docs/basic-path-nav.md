# Unit 2: Unix Directory Structure and Navigation

### Root Directory

The root directory is the directory at the top of the directory tree[^1]. It is
simply referred to as `/`, without any name. Under the root directory are many
other systems directory, which a casual user does not normally need to (and have
no permission to) modify.

[^1]:
    In computing, trees are upside down with the root at the top and leaves at
    the bottom!

### Home Directory

Each user has his/her own _home_ directory. The above figure shows where the
home directory of the user `ooiwt` resides in the directory tree. The user
`ooiwt` may create files or directories in his/her home directory, but not
elsewhere unless permission is given.

The home directory is referred to with the symbol `~` in `bash`. Sometimes we
add the username behind `~` to indicate the home directory of the other user.
E.g., `~bob` means the home directory of a user named `bob`.

### Current Working Directory

A user can navigate around the directory tree. The _current working directory_
is the directory that the user is currently in. In contrast to the root and home
directory, which are fixed[^2], the current working directory changes as the
user moves around. Knowing the current working directory is important since this
is the default location in the directory tree a command executes. As such, many
systems by default display the current working directory as part of the `bash`
command prompt.

The current working directory is referred to with the symbol `.` in `bash`.

[^2]:
    Not exactly true -- since Unix is designed to be flexible, even the root and
    the home directory can be changed! But let's not worry about that for now
    since there is no good reason to do that as a beginner.

### Parent Directory

The _parent directory_ is directory one layer up from the current directory.

The parent directory is referred to with the symbol `..` in `bash`.

To summarize, here are the short form representations:

| Symbol | Meaning                       |
| ------ | ----------------------------- |
| `/`    | the root directory            |
| `~`    | the home directory            |
| `.`    | the current working directory |
| `..`   | the parent directory          |

## Directory-related Commands

Now, let's take a look at some basic commands available in `bash` that deals
with navigation and directories.

### `pwd`: Print Current Working directory

`pwd` shows you which directory you are currently in.  
Type `pwd` into the command prompt, and it will print the absolute path to your
current working directory. For instance, Suppose you are in `/home/o/ooiwt`,
entering

```Bash
pwd
```

will give the output

```Bash
/home/o/ooiwt
```

### `ls`: LiSt content of a directory

The `ls` list the content in the current working directory.

!!! note "Rule of Silence" Unix follows the economical _rule of silence_:
programs should not print unnecessary output, to allow other programs and users
to easily parse the output from one program. So, if `ls` has nothing to list, it
will list nothing (as opposed to, say, printing "This is an empty directory.")

### `mkdir`: MaKe a subDIRectory

The `mkdir` command creates a subdirectory with the given name in the current
directory.

In the example below, we assume that we start with an empty directory.

```bash
$ ls
$ mkdir workshop
$ ls
workshop
$ ls -F
workshop/
```

Here, we create a directory called `workshop`. Now, when we `ls`, you can see
the directory listed.

You may also use `ls -F` for more information (`-F` is one of the many
_options_/_flags_ available for the `ls` command. To see a complete list of the
options, refer to the man pages, i.e., `man ls`.)

The slash `/` beside the filename tells you that the file is a directory. A
normal file does not have a slash beside its name when "ls -F" is used.

You may also use the `ls -l` command (hyphen el, not hyphen one) to display
almost all the file information, include the size of the file and the date of
modification.

!!! tip "Use Up Arrow for Command History" `bash` maintains a history of your
previously executed commands, and you may use the ++control+p++ (previous) and
++control+n++ (next) to go through it. Press the ++control+p++ until you find a
previously executed command. You may then press ++enter++ to execute it or edit
the command before executing it. This is handy when you need to repeatedly
execute a long `bash` command.

### `cd`: Change Directory

To navigate in the directory tree, changing the current working directory from
one to another, we use the `cd` command.

```Bash
$ pwd
/home/o/ooiwt
$ cd workshop
$ pwd
/home/o/ooiwt/workshop
```

Suppose our starting working directory is `/home/o/ooiwt`, after we `cd` into
`workshop`, the current working directory becomes `/home/o/ooiwt/workshop`. Note
that `cd` can take in either an absolute path or a relative path. The example
above takes in a relative path as the argument.

As mentioned in the [Introduction to Shell](shell.md) unit, it is common to
include the current working directory into the shell's prompt. So, you may see
your command prompt updated to include the new working directory.

Entering `cd` alone (without argument) brings you back to your home directory.

### `rmdir`: ReMove a subDIRectory

`rmdir` removes a subDIRectory in the current directory -- note that a directory
must be empty before it can be removed.

The command

```
$ rmdir workshop
```

will remove the directory that you just created.
