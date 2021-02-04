## Unit 4: Terminal-based Editor: `vim`

The above examples show us how we can create a simple, one-line, shell script.
Shell scripts can be fairly complex -- `bash` supports a full-blown programming
language.

To edit shell scripts, programs, or text files, we need a proper editor.
Remember that we want to keep our hands on the keyboard and keep ourselves "in
the zone" with only the terminal, the keyboard, and ourselves, so we will use a
terminal-based editor: no windows, no mouse, no arrow keys, no function keys.

There are only two respectable, widely available text editors in Unix -- `vim`
and `emacs`, which one is better has been an ongoing religious war, but for us
in SoC, we use `vim`.

You will get to practice using `vim` in the next session, but for a start, I
will go through the key ideas of `vim`.

### 1. Minimizing Hand Movements

`vim`, like the shell, aims to minimize hand movements. Frequently used commands
are positioned in convenient places on the keyboard. Let me give you a few
examples.

- To exit vim, type ++shift+z+z++. Notice that this is located at the bottom
  left corner of your keyboard. For normal typing, your left hand is supposed to
  be placed over the keys ++a++ ++s++ ++d++ ++f++, so you just need move
  slightly your left pinky to ++shift++ and left ring finger to ++z++ and hit
  them.

- To move the cursor, instead of using the arrow keys, `vim` uses ++h++ to move
  left, ++l++ to move right, ++j++ to move down, and ++k++ to move up. For
  normal typing, you right hand is supposed to be placed on ++j++ ++k++ ++l++
  ++semicolon++, so these arrow keys alternatives are located very near to where
  your right hand should be!

I have a few more things to say about using ++h++ ++j++ ++k++ ++l++ to replace
the arrow keys:

- It is not uncommon for applications to re-map other keys for movement. Many
  first-person shooting games uses ++w++ ++a++ ++s++ ++d++ for movement, for the
  same reason as `vim` -- it is close to the resting position of the left hand
  on the keyboard.

- The use of ++h++ ++j++ ++k++ ++l++ for movement is more ubiquitous than you
  think. In the Web-version of Facebook and Reddit, for instance, you can use
  ++j++ and ++k++ to move up and down across posts. On this website, you can use
  ++h++ and ++l++ to go to the previous page and the next page respectively.

### 2. Multi-modal Editor

`vim` is a multi-modal editor. While for most other editors makes no distinction
between reading and editing, `vim` makes an explicit distinction between the
two. `vim` has two basic modes:

- `NORMAL` mode: where you read, navigate and manipulate the text.
- `INSERT` mode: where you insert the text

As a programmer, having a different `NORMAL` modes makes sense since we spend
much time reading and navigating around source code. Thus, allowing the editing
commands to optimized.

In the `NORMAL` mode, you can use any of these keys ++i++ ++s++ ++a++ ++o++
(with or without ++shift++) to switch to `INSERT` mode. To go back to `NORMAL`
mode, press ++esc++. The keys ++i++ ++s++ ++a++ ++o++ have different meanings,
which you will learn later.

Note that most of the time you will be in `NORMAL` mode. So a habitual `vim`
users would insert some text and immediately switch back to normal mode by
hitting ++esc++.

### 3. Tell `vim` What You Want To Do; Don't Do It Yourself

In `NORMAL` mode, you can manipulate text in `vim` by issuing commands to `vim`.
These commands are like a programming language. It is also not unlike the Unix
commands, in that each command does a small thing but can be composed together
to perform complex text manipulation.

Let me give an example here. Suppose you have a sentence:

```
Wherever there is light, there is also a shadow.
```

You want to remove `also a` from the sentence.

What would you do in a typical text editor? You can use move your hand away from
the keyboard, find your mouse, move your mouse cursor to highlight the text, and
then hit ++delete++. Or you could move the cursor (by mouse or by repeatedly
hitting the keyboard) to place the cursor after `a`, and then press ++delete++
six times.

In addition to being tedious, this is error-prone. You might highlight one
additional or one less space, or hit ++delete++ one too many times.

What we are used to do is to perform the action of deleting the words ourselves.
For `vim`, we do it differently. We need to look for the word `also` and delete
two words. This translate to the command ++slash++ ++a++ ++l++ ++s++ ++o++
++enter++ ++d++ ++2++ ++w++.

- ++slash++ triggers a search. This is an almost universal command -- try
  ++slash++ on Facebook (web) or on this page.
- ++a++ ++l++ ++s++ ++o++ ++enter++ tells `vim` what you want to search. After
  enter, your cursor should be placed at the beginning of `also`.
- ++d++ ++2++ ++w++ tell `vim` to "delete two words".

Instead of worrying about the actual actions to perform the deletion, we issue
higher-level commands to describe what we want to do. This is powerful since
this is how our brain thinks -- "I need to insert this here, change this word to
that, remove two lines, etc" All these maps into commands in `vim`. As a result,
once you master `vim` basics, you can type as fast as you think[^3]!

A common pattern for `vim` command consists of three parts: (i) place the
cursor; (ii) performance an action; (iii) move to the new placement of the
cursor. In the example above, ++slash++ ++a++ ++l++ ++s++ ++o++ ++enter++ places
the cursor, ++d++ is the action (delete), and ++2++ ++w++ is the movement (move
the cursor forward by two words).

Another common command that students used is ++g++ ++g++ ++equal++ ++shift+g++.
This command is used to indent the source code in the current file. ++g++ ++g++
is the command to place the cursor at the top of the file. ++equal++ is the the
action (indent), and ++shift+g++ is the command to place the cursor on the last
line of the file.

### 4. Be A Good Unix Citizen

Not only the basic commands `vim` adhere to the Unix principles of
composability, `vim` plays well with Unix shells, which add additional power to
the `vim`. For instance, if you want to have the standard output from a command
paste into the file you are editing, you can run:

```
:r! <command>
```

++colon++ triggers the `vim` command line. ++r++ ask `vim` to read something and
paste it into the current cursor location. At this point, you can pass in, for
instance, another file name. But here, we enter ++exclam++, which tells `vim` to
run a shell. We then pass the `command` to the shell. Whatever the command
writes to the standard output, will be read and inserted into `vim`.

Want to insert today's date?

```
:r! date
```

Want to insert a mini calendar?

```
:r! cal
```

Want to insert the list of all JPG pictures?

```
:r! ls *jpg
```

You can even pass a chunk of text from `vim` to the standard input of another
program, and replace it with what is printed to the standard output by that
program.

## Other Reasons To Learn `vim`

Besides enabling you to type as fast as you think with as few hand movements as
possible, there are other reasons to use `vim`:

- `vim` is installed by default in almost any Unix environment. Imagine if you
  get called to a client-side to debug a Linux server and you need to edit
  something -- you can rest assure that `vim` is there.

- `vim` is the only source code editor you need to learn and master. It works
  for almost any programming language. If you use IDE, you have to learn
  IntelliJ for Java, IDLE for Python, Visual Studio C++ for C++, etc.

- `vim` is extensible and programmable. It has been around for almost 30 years,
  and tons of plugins have been written. Whatever feature you need, there is
  likely a native `vim` command or a `vim` plugin for that.

The only downside to using `vim` is that it is text-only (some considers it
ugly) and the steep learning curve.

[^3]:
    The book _Practical Vim_ by Drew Neil has the subtitle "Edit text at the
    speed of thought".
