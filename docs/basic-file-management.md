# Unit 3: Unix File Management

This note assumes that you are familiar with navigation with the Unix directory
structure.

We will now learn some commands to help us deal with files.

Let's recreate the `workshop` directory in case you have already deleted it with
the `rmdir` at the end of the last unit.

```
$ mkdir -p workshop
$ cd workshop
$ ls
```

All of the above commands should complete successfully and `silently`. Let's
populate the directory with a new file. Cut-and-paste the command below into the
command prompt :

```
wget https://raw.githubusercontent.com/nus-unix-workshop/2021-s1/master/test.txt
```

You should see a file being downloaded and saved with an output similar to
below:

```
--2020-07-27 15:26:49--  https://raw.githubusercontent.com/nus-unix-workshop/2021-s1/master/test.txt
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.0.133, 151.101.64.133, 151.101.128.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.0.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64 [text/plain]
Saving to: ‘test.txt’

test.txt              100%[======================>]      64  --.-KB/s    in 0s

2020-07-27 15:26:50 (2.35 MB/s) - ‘test.txt’ saved [64/64]
```

Now run `ls`, and you should see that `ls` returns `test.txt` as the content of
the current working directory.

```
$ ls
test.txt
```

### `cp`: CoPy files

Now let's try to copy this file to another name.

```
$ cp test.txt foo.txt
$ ls
test.txt foo.txt
```

The command above copies the file `test.txt` into `foo.txt`.

If you want to copy the whole directory, use `-r` flag, where `r` stands for
copying recursively.

Now let's create another directory called `copy`.

```
$ cd ..
$ mkdir copy
$ cd copy
$ ls
```

Run `pwd` to double-check that you are in the directory called `copy` that is at
the same level as `workshop`.

Now, we are going to use `cp` with the `-r` flag, to copy recursively the whole
of `workshop` directory over.

```
$ cp -r ../workshop .
```

The command `cp` takes in two arguments, the first is the source, and the second
is the destination.

Note that we use `.` above to indicate that we wish to copy the whole sub-tree
of `workshop` over the current directory. The command should complete without
any message. Upon completion, you can run `ls` to double-check that the workshop
directory exists under `workshop`.

!!! Warning: `cp` Overwrites If there is an existing file with the same name,
`cp` will overwrite the existing file without warning.

### `mv`: MoVe or rename files

Now, let's change directory back to `workshop`.

```
$ cd ../workshop
```

and use the `mv` command to rename `foo.txt` into `bar.txt`.

```
$ ls
foo.txt test.txt
$ mv foo.txt bar.txt
$ ls
bar.txt test.txt
```

As you can see above, just like `cp`, `mv` takes in two arguments, the first is
the source and the second is the destination.

If the destination of `mv` is a directory, however, instead of renaming, the
`mv` commands move the source to the destination directory.

```bash
$ ls
bar.txt test.txt
$ mv ../copy/workshop/foo.txt .
$ ls
bar.txt foo.txt test.txt
```

Here, you can see that we have moved `foo.txt` over to the current directory.

!!! Warning: `mv` Overwrites If there is an existing file with the same name,
`mv` will overwrite the existing file without warning. `mv` comes with a `-i`
flag that interactively asks you if you are sure if you want to overwrite a
file. It is a good idea to always run `mv -i`. Hit ++y++ to continue overwriting
the existing file. We will see how to make `-i` the default tomorrow
([sneak peak here](shell.md)).

!!! tip "Use ++tab++ for Name Completion" If you have a very long file name, you
may use the `bash` auto-completion feature to reduce typing. For instance, you
may type: `$ mv t` and press the ++tab++ key, `bash` will complete the filename
for you if there is only one filename with the prefix "t". Otherwise, it will
fill up the filename to the point where you need to type in more characters for
disambiguation. The ++tab++ key can also complete the name of a command.

### `rm`: ReMove files

We can use `rm` to remove files. Be careful with this command -- files deleted
cannot be restored. There is no trash or recycled bin like in Mac or Windows.

```bash
$ ls
bar.txt foo.txt test.txt
$ rm foo.txt
$ ls
bar.txt test.txt
```

!!! warning "rm -rf " While the Unix command line provides lots of flexibility
and power, with great power comes great responsibility. Some of the commands are
extremely dangerous. `rm -rf *` is the most famous one. The notation `*` refers
to all files, and the flag `-f` means forceful deletion (no question asked!),
and `-r` means remove recursively everything under the current directory tree.
Accidentally running this command has ruined many lives.
[Read more here](https://www.quora.com/What-are-some-crazy-rm-rf-stories-you-have-heard-about)

`rm` comes with a `-i` flag that interactively asks you if you are sure if you
want to delete a file. It is a good idea to always run `rm -i`.

```
$ rm -i bar.txt
rm: remove regular file 'bar.txt'?
```

Type `y` or `n` to answer yes or no respectively.

### `cat`: CATenate file content to screen

To quickly take a look at the content of the file, use the `cat` command.

```bash
$ cat test.txt
This is a test file for learning Unix file management commands.
```

`less` is a variant of `cat` that includes features to read each page leisurely
and is useful for long files.

```bash
$ less test.txt
```

In `less`, use `<space>` to move down one page, `b` to move Back up one page,
and `q` to Quit.

### `man`: Online MANual

An online help facility is available in Unix via the `man` command (`man` stands
for MANual). To look for more information about any Unix command, for example,
`ls`, type `man ls`. Type `man man` and refer to Man Pages to find out more
about the facility. To exit `man`, press `q`.

## Other Useful Online Tools

- [explainshell](https://explainshell.com/) explain each shell command for you
