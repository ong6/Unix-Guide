# TMUX

## What is tmux

tmux’s authors describe it as a terminal multiplexer. Behind this fancy term
hides a simple concept: Within one terminal window you can open multiple windows
and split-views (called “panes” in tmux lingo). Each pane will contain its own,
independently running terminal instance. This allows you to have multiple
terminal commands and applications running visually next to each other without
the need to open multiple terminal emulator windows.

On top of that tmux keeps these windows and panes in a session. You can exit a
session at any point. This is called “detaching”. tmux will keep this session
alive until you kill the tmux server (e.g. when you reboot). This is incredibly
useful because at any later point in time you can pick that session up exactly
from where you left it by simply “attaching” to that session.

## Getting Started

This hands-on guide will get you up and running with tmux pretty quickly. It
will only cover the basic features which should be more than enough to get
started and be productive with tmux. Simply open your terminal and follow the
instructions.

### Installation

Fortunately installing tmux is pretty straightforward on most distributions a
simple `sudo apt-get install tmux` (Ubuntu and derivatives) or
`brew install tmux` (Mac) should be sufficient.

### Starting your tmux Session

I recommend you follow along for this guide as it is very visual. For your first
session simply start tmux with a new session:

```
$ tmux
```

This will create a new tmux session with a nice all-green status bar at the
bottom.

## Splitting Panes

Now that we’ve created our first session we can get a feeling for panes. When
you create a new session, tmux will by default start with one window and a
single panel inside. We want a nice split-screen, so let’s split this bad boy.

All commands in tmux are triggered by a prefix key followed by a command key. By
default, tmux uses `C-b` as prefix key. This notation might read a little weird
if you’re not used to it. In this emacs notation `C-` means “press and hold the
`Ctrl` key". Thus `C-b` simply means press the `Ctrl` and `b` keys at the same
time.

The shortcut to split panes into a left and a right pane is `C-b %`. Remembering
what I’ve just told you about tmux’s sequence of prefix and command key this
means to split your single pane into a left and a right pane you press
`Ctrl + b` at the same time, release both, and then type the `%` key. Voilà!
You’ve just invoked your first tmux command and split your pane in two.

Where there’s a split into left and right, there’s also a split into top and
bottom pane. To split a pane into top and bottom panes use the `C-b "` shortcut.

## Navigating Panes

Right now we’re trapped in the newly created pane. But we really really want to
go back to the left one. Easy peasy: Switching to a different pane uses the
`C-b arrow key` shortcut, where arrow key is the arrow key pointing to the pane
you want to switch to. In our case we want to switch to the panel on the left so
it’s `C-b left` for us. Just once more, so that we fully understand this: This
means you press Ctrl and b (your prefix) followed by the left arrow key to get
to the pane on the left.

You can now go ahead and split each of your new panels even further. Feel free
to experiment and split your panes like a maniac to get a feeling for it.

## Closing Panes

Closing a pane is as simple as closing a regular terminal session. Either type
`exit` or hit `Ctrl-d` and it’s gone.

## Creating Windows

Creating new windows is as easy as typing `C-b c` (one last time: that’s Ctrl
and b at once, then c). The new window will then be presented to you in tmux’s
status bar.

You can now divide the pane in your new window as you like. Or don’t. That’s up
to you.

To switch to the previous window (according to the order in your status bar) use
`C-b p`, to switch to the next window use `C-b n`. If you’ve created many
windows you might find it useful to go to a window directly by typing its number
(the status bar will tell you which window has which number), just use
`C-b <number>` where `<number>` is the number in front of the window’s name in
your status bar.

## Some Additional Commands

If you’re curious now to learn what else tmux can do that’s a great thing. And
luckily most of the stuff is quite simple to discover. Just type `C-b ?` to see
a list of all available commands and start experimenting.

Some of the commands that I’m using myself quite often are:

- `C-b z`: make a pane go full screen. Hit `C-b z` again to shrink it back to
  its previous size
- `C-b C-<arrow key>`: Resize pane in direction of `<arrow key>`
- `C-b` ,: Rename the current window
