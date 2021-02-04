# Unit 5: Getting Started with `vim`

## Setting Up Your `vim` Environment

Like many other Unix programs, you can configure your preferences by creating an
`rc` (run commands) file in your home directory. These `rc` files will be read
by the corresponding programs and executed line-by-line as if the text is
entered into the program through a keyboard. You can view these `rc` as a script
that will be executed automatically whenever a program starts.

For `vim`, the `rc` file is called `.vimrc`. The `.` in the front of the file
name carries a special meaning in Unix. It means that this file is hidden -- you
won't see it when you `ls`. Hiding the run command files prevent your home
directory from being cluttered. To tell `ls` to show the hidden files, use the
`-a` flag

```
$ ls -a
```

We have created a `.vimrc` file, with reasonable defaults, for your use. Note
that different modules may choose to use a different coding convention and so a
different setting. But this `.vimrc` file suffices for now.

To get this file,

```
$ cd
$ mv .vimrc .vimrc.bak
$ mkdir .backup
$ wget https://raw.githubusercontent.com/nus-unix-workshop/2021-s1/master/.vimrc
```

The first line changes your working directory to your home. The second line
creates a backup `.vimrc`, if one exists. If it does not, `mv` will give you an
error, which is fine. The third line creates a hidden backup directory for
`vim`. The last line downloads our `.vimrc` into your home directory.

Our default `.vimrc` set up `vim` such that it creates a backup copy of the file
you are editing every time and store it in `~/.backup`. This feature has saved
me from pulling my hair out countless times. It is highly recommended that you
set this up whenever you `vim`.

## Lesson 1: Navigation

Now, you can stay in your home directory or go back to your workshop directory.

Download the following file for practice using `vim` in this session.

```
$ wget https://raw.githubusercontent.com/nus-unix-workshop/2021-s1/master/jfk.txt
```

The file named `jfk.txt` should be downloaded. Now let's start your first `vim`
session.

```
$ vim jfk.txt
```

When you start, you will be in `NORMAL` mode. For now, just move around the
cursor with ++h++ ++j++ ++k++ ++l++. Get comfortable with using the keys.

Next, try ++parenthesis-left++ and ++parenthesis-right++ to move forward and
backward, sentence-by-sentence.

Next, try ++brace-left++ and ++brace-right++ to move forward and backward,
paragraph-by-paragraph.

Use ++0++ to jump to the beginning of the line, and ++dollar++ to jump to the
end of the line.

Use ++g+g++ to jump to the beginning of the file, and ++shift+g++ (`G`) to jump
to the last line of the file.

Now try ++slash++, type in any word (or prefix of a word) and ++enter++. This
should move the cursor to the beginning of the word. You can use ++n++ and
++shift+n++ to move to the next match and the previous match.

When you are comfortable with moving around, you can ++shift+z+z++ to exit.

Congratulations, you have just completed your first session in `vim`!

## Lesson 2: Manipulating Text

Now, we are going to open up the same file again and try to manipulate the text.
We are going to stay in the `NORMAL` mode still.

```
$ vim jfk.txt
```

### Deletion

Try ++0++ ++d++ ++3++ ++w++ to move the cursor to the beginning of the line and
delete three words.

Press ++u++ to undo. This is another lifesaver that you should remember.

In `vim`, repeating the same command twice usually means applying it to the
whole line. So ++d++ ++d++ deletes the current line. Try that.

Pairing a command with ++shift++ (or the capital letter version) usually means
applying the action until the end of the line. So ++shift+d++ deletes from the
current cursor until the end of the line.

### Copy Pasting

Hit ++p++ to paste back what you just deleted. Try moving the cursor to
somewhere else and paste.

To copy (or yank) the current line, hit ++y++ ++y++.

Remember that all these commands can be composed using the
movement-action-movement pattern. For instance, ++shift+9++ ++y++ ++shift+0++,
which corresponds to: move to the beginning of the sentence, yank, and until the
end of the sentence, basically copy the current sentence.

As you have seen in the ++d++ ++2++ ++w++ example, you can preceed an action
with a number to repeat an action multiple times.

Try ++y++ ++y++ ++9++ ++p++. You should be able to understand what just
happened!

### Deleting a Character

The ++x++ command deletes the current character.

Try this exercise: At the end of the file `jfk.txt`, there are some typos:

```
libertyi. liberty.
```

Change `libertyi. liberty.` to `libtery.` by positioning the cursor on the
second `i` and delete it. Then use ++shift+d++ to delete the extra `liberty.` at
the end of the sentence.

### Visual Mode

In addition to the `INSERT` and `NORMAL` modes, `vim` has the third mode, the
`VISUAL` mode. You can enter the `VISUAL` mode by hitting ++v++. Once in visual
mode, you can move your cursor to select the text and perform some actions on it
(e.g., ++d++ or ++x++ to delete, ++y++ to yank).

Hitting ++shift+v++ will allow you to select line-by-line.

The `VISUAL` mode allows us to pipe the selected text to another Unix command,
and replace it with the result of that command.

Go ahead and try to select a paragraph in `jfk.txt`, and hit ++colon++. You will
see that

```
:'<,'>
```

appears in the last line of the terminal. At this point, you can type in actions
that you want to perform on the selected text. For instance,

```
:'<,'>w john.txt
```

will write it to a file named `john.txt`.

But, let's try the following:

```
:'<,'>!fmt
```

`!fmt` tells `vim` to invoke the shell and run `fmt`. `fmt` is another simple
small Unix utility that takes in a text (from standard input) and spew out
formatted text in the standard output. You will see that the width of the text
has changed to the default of 65.

You can try something that we have seen before. Reselect the text, and hit

```
:'<,'>!wc
```

The selected text will be replaced with the output from `wc`.

### The `:` command

You have seen examples of `:` commands for writing to a file or piping selected
text to an external command.

The `:` command also opens up a large number of actions you can do in `vim`.
Here are a few essential yet simple commands.

- To jump to a line, hit ++colon++ followed by the line number.
- To open another file, hit ++colon++ and then type in `e <filename>`
- To find help on a topic, hit ++colon++ and then type in `help <keyword>`

Other advanced features such as search-and-replace, changing preferences,
splitting windows, opening new tabs, are also accessible from the `:` command.

The `:` command prompt supports ++control+p++ and ++control+n++ for navigating
back and forth your command history, just like `bash`. It also supports ++tab++
for auto-completion.

## Lesson 3: Insert mode!

Finally, we are going to try inserting some text. Remember, to use `INSERT`
mode, we always start with a command ++i++ ++a++ ++o++ or ++s++ (may paired with
++shift++) followed by the text that you want to insert, followed by ++esc++.

Let's try ++i++ (insert). Place your cursor anywhere, hit ++i++, and start
typing, when you are done. Hit ++esc++.

You just added some text to the file.

Place your cursor anywhere, hit ++a++ (append), and start typing, when you are
done. Hit ++esc++. ++a++ appends the text to the end of the current line.

Hit ++o++ (open) and start typing, when you are done. Hit ++esc++. ++o++ opens
up a new line for the your text.

Hit ++s++ (substitute) and start typing, when you are done. Hit ++esc++. ++s++
substitute the current character with your text.

Now try it with ++shift++ and see the difference in behavior.

## Learning More

There is only so much we can cover in 30 minutes. This workshop only covers the
tip of the iceberg. To learn more about `vim`, we suggest that you run
`vimtutor` on the command line and follow through the tutorials.

Once you are comfortable, you can soup up your `vim` with various plugins and
learn how to use advanced commands (such as search and replace, jumping between
files, recording macros, folding, auto-completion) that are invaluable for
programming.

There are also many video tutorials and resources online. Some interesting ones
are:

- [Vim: Precision Editing at the Speed of Thought](https://vimeo.com/53144573):
  A talk by Drew Neil
- [Vim Adventure](https://www.vim-adventures.com): An adventure game for
  learning `vim`
- [Vim Casts](http://vimcasts.org/episodes/archive/): Videos and articles for
  teaching `vim`
- [Vim Video Tutorials](http://derekwyatt.org/vim/tutorials/) by Derek Wyatt
- [Vim Awesome](https://vimawesome.com/): Directory of plugins.
