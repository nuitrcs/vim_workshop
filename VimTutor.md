# The very basics

### Introduction

1. What is Vim?
    - Vim stands for "**Vi Improved**". It's a clone of the text
    editor "vi".
    - Vim is included as "vi" with most UNIX systems and with Apple OS X.
2. Why Vim?
    - Vim is free and open source. It also a charityware that gives
    support to poor children in Uganda!
    - Vim is available for many platforms. Vim has a graphic user
    interface, with menus and support for the mouse, while it also
    supports textmode in terminals， which is perfect for remote
    access/administration (like Quest).
    - Vim is perfect for programming. Vim supports all great features
    for code editors: auto-completion, syntax highlighting, screen
    split, and so on.
    - Vim is highly configurable. With some extra plugins, it works
    just like an IDE (Integrated Development Environment, such as
    visual studio), but much faster!

### Different Modes in Vim

One of the most important concepts in Vim is modes. This is the major
difference between Vim and other text editors like Notepad in Windows
and gedit in Linux. Here is a short overview of each mode available
in vim:

- Normal mode: For navigation and manipulation of text. This is the
default mode when you start Vim. Press `<ESC>` to exit back to normal
mode from other modes.
- Insert mode: For inserting new text. Insert mode can be reached in
several ways, e.g., pressing `i` when in normal mode.
- Command-line mode: For entering editor commands, such as help, search,
 save, quit. Press `:` when in normal mode to enter command-line mode.
- Visual mode: For navigation and manipulation of text selections.
This mode allows you to perform most normal commands, and a few extra
commands, on selected text. Press `v` when in normal mode to enter
visual mode.

**Example I:** Navigation in Vim with `hjkl`.

In Vim normal mode, commands `h`, `j`, `k`, `l` are used to move cursor
left, right, up or down. Arrow keys can also be used to move cursor,
however, using `hjkl` will allow you to navigate faster once you get
used to it.

- Open *introduction.txt* using vim from the terminal
```bash
vim introduction.txt
```
- Make sure you are in normal mode by hitting `ESC`.
- Press `h`, `j`, `k`, `l` to move your cursor around until you feel
comfortable with that.

**Example II:** Insert text in Line 2 of *introduction.txt*.

- Open *introduction.txt* and make sure you are in normal mode by
hitting `ESC`.
- Navigate to Line 2 (empty) with `j`.
- Press `i`, and you should notice the bottom left shows "-- INSERT --",
which indicates you have switched to insert mode. Now you can type new
text as you like.
- Exit back to normal mode by hitting `ESC`. Leave it open for next
example.

Command `i` is used to insert text right before the cursor. There are
many other similar commands that allow you to switch to insert mode,
but in different positions. E.g.,

- Command `a` is used to insert text AFTER the cursor.
- Command `A` is used to insert text after the end of the line.
- Command `o` is used to open a line BELOW the cursor and start insert
mode.
- Command `O` is used to open a line ABOVE the cursor.

You can also try them in Example II.

**Example III:** Quit with/without saving in Vim

- In the opened *introduction.txt*, type `:q!` and hit `ENTER` to exit
WITHOUT saving the changes.
- Reopen *introduction.txt*, insert some text with commands `o` or `a`.
Type `:wq` and hit `ENTER` to exit WITH saving the changes.

--------------

# More on Text Editing

Let's discuss about Vim text edit techniques in details. For these
exercises we will use *editing.txt*.

### 1. Deletion Command

Command `x` is used to delete the character under the cursor.

**Example I:** Correct the text lines marked by -->.

- Open *editing.txt* and navigate to Example I. Make sure you are in
normal mode by hitting `ESC`.
- Move your cursor to the character you want to delete, hit `x`
- Repeat until all lines marked by --> are corrected.

Command `d` is also for deletion. It can be combined with a motion
command. E.g. `dw` is used to delete a word, and `d$` is used to delete
to the end of the line.

**Example II:** Correct the text lines marked by -->.

- Open *editing.txt* and navigate to Example II. Make sure you are in
normal mode by hitting `ESC`.
- Move your cursor to the beginning of the word you want to delete,
hit `dw`.
- Repeat until all lines marked by --> are corrected.

**Example III:** Correct the text lines marked by -->.

- Open *editing.txt* and navigate to Example III. Make sure you are in
normal mode by hitting `ESC`.
- Move your cursor to character "&", hit `d$`.
- Repeat until all lines marked by --> are corrected.

A **count** can be inserted before the motion to delete more. E.g.,
`d2w` is used to two words at one time.

**Example IV:** Delete all UPCASE words marked by -->.

- Open *editing.txt* and navigate to Example IV. Make sure you are in
normal mode by hitting `ESC`.
- Move your the first "MEOW", hit `d3w` to delete "MEOW MEOW MEOW".
- Repeat until all lines marked by --> are corrected.

In addition to those mentioned above, command `dd` can be used to delete
 a whole line. Note here to delete multiple lines with count, use `3dd`,
 rather than `d3d`.

**Example V:** Delete all lines marked by -->

- Open *editing.txt* and navigate to Example V. Make sure you are in
normal mode by hitting `ESC`.
- Move your the cursor to anywhere of a line marked by -->, and hit `dd`
- Repeat until all lines marked by --> are deleted. You can also try
use `3dd` to delete three lines together.

### 2. Put Command

The text deleted last time is stored and can be put back with command
`p`. This works just like cut & paste in other editors like notepad.

**Example VI:** Correct the text lines marked by -->.

- Open *editing.txt* and navigate to Example VI. Make sure you are in
normal mode by hitting `ESC`.
- Move your the cursor to the beginning of word "some", and hit `dw`.
- Move your the cursor to the space behind word "are", and hit `p`. You
should have moved word some to the correct position.
- Repeat until all lines marked by --> are deleted.

### 3. Replace Command

Command `r` is to replace one character at the cursor with new character
you input. The command capital `R` is used to replace more than one
character.

**Example VII:** Correct the text lines marked by -->.

- Open *editing.txt* and navigate to Example VII. Make sure you are in
normal mode by hitting `ESC`.
- Move your the cursor to the character "u" in word "sume", and hit
`ro`. You should have corrected character "u" by "o". It also
automatically switches back to normal mode.
- Move your the cursor to the character "q" in word "misqhdsi", and hit
`Rtake`. You should have corrected the word "misqhdsi" by "mistake". Hit
`ESC` to switch back to normal mode.

### 4. Change Command

The change command `c` works very similarly as command `d`. It removes
the text corresponding to the motion, and switches you to insert mode.
E.g., command `cw` removes the word and switches to insert mode so that
you can type anything you wish to replace the original content.

**Example VIII:** Correct the text lines marked by -->.

- Open *editing.txt* and navigate to Example VIII. Make sure you are in
normal mode by hitting `ESC`.
- Move your the cursor to the beginning of word "abcd", and hit `cw`.
Type the correct word "some" and hit `ESC` to switch back to normal mode.
- Move your the cursor to character "&", and hit `c$`. Type the correct
content and hit `ESC` to switch back to normal mode.

### 5. Visual Mode

Command `v` is used to select text visually. After hit `v`, you will be
switched to visual mode, and by moving cursor you can change the range
of text being selected. The visually selected text can be copied use yank
command `y` and pasted with command `p`.

**Example IX:** Complete the text lines marked by -->.

- Open *editing.txt* and navigate to Example IX. Make sure you are in
normal mode by hitting `ESC`.
- Move your the cursor to the beginning of word "are", and hit `v`.
Now you are switched to visual mode. Navigate your cursor to the end of
line to select the text you would like to copy.
- Hit `y` to copy, and you will be automatically switched back to normal
mode.
- Navigate to the position you want to paste, hit `p`.

Command `y` can be also used similarly as `d` or `c` by combining it
with motion like `w` and `$`. E.g., you can use `y$` in the example above. You can also use `yy` to copy an entire line.

### 6. Named Buffer

When you use deletion command `d` or yank command `y`, the text is saved in a **buffer**. In order to work with multiple buffers, names from "a" to "z" can be assigned to buffers. E.g., command `"ayy` will assign name "a" to the line you just copy.

**Example X:** Order the sentences 1-3 in correct order.

- Open *editing.txt* and navigate to Example X. Make sure you are in
normal mode by hitting `ESC`.
- Move cursor to first line (Sentence 3), and hit `"ayy`.
- Move cursor to second line (Sentence 1), and hit `"byy`.
- Move cursor to third line (Sentence 2), and hit `"cyy`.
- Now move the empty space below. First hit `"bp` to recover Sentence 1, then hit `"cp` to recover Sentence 2, and finally, hit  `"ap` to recover Sentence 1. 

### 7. Undo command

To undo your last command, use command `u`.

**Example XI:** Correct the text lines marked by -->, then undo the
correction.

- Open *editing.txt* and navigate to Example XI. Make sure you are in
normal mode by hitting `ESC`.
- Use command `x` to correct the line marked by -->.
- Now hit `u`, it will undo your last deletion. Hit `u` again, it will
redo your second last deletion.

--------------

# More on Navigation and Search
Let's discuss some fast navigation techniques between lines and pattern
search methods in vim. For these exercises we will use *animals.txt*.

#### 1. Moving to start and end of the file

**Example I:** Move to start/end of the in normal mode
- Switch to normal mode by hitting ESC. Type `G` to move to the last
line of the file
- Switch to normal mode by hitting ESC. Type `gg` to move to the first
line of the file

**Example II:** Move to start/end of the file in command-line mode
- Switch to command-line mode by hitting ESC and then typing `:`. Type
`$` and hit enter/return to move to the last line of the file
- Hit ESC then type `:` to switch to command-line mode. Type `0` and hit
enter/return to move to the beginning of the file

#### 2. Moving to an arbitrary line

**Example III:** Move to a line using the line number in normal mode
- Hit ESC, type the number of the line, say 14, and then type `G` (i.e.
SHIFT+g)

**Example IV:** Move to a line using the line number in command-line mode
- Hit ESC, type `:`, then type the number of the line, say 23, hit
enter/return

**Example V:** Let's make sure we moved to 23rd line by showing the
line numbers before each line.
- Hit ESC, type `:set nu` (or equally `:set number`), hit enter/return
- Type `:set nonu` (or equally `:set nonumber`) and hit enter/return to
hide the line numbers

#### 3. Using Marks
A mark is location identifier which allows you to return to the same
location later. When you set a mark there is no visible indication on
the file. Each buffer (or practically the file) has its own default
marks (i.e. lowercase letters from a to z). The marks are persistent for
the files as long as you retain .viminfo file which includes the metadata
about marks, command-line history, search strings, buffers etc.

**Example VI:** Let's set mark "a" on the first comma (,) of the 9<sup>th</sup>
line in *animals.txt*. After setting "a" mark for this location move to
the end of the file. Using the mark, return to original location.
- Hit ESC, type `9G` (navigate to line 9) and move to the
first comma by hitting `l` key (or right arrow key)
- Type `ma` (while on the normal mode) to set the mark "a" to the
cursor location.
- Type `G` to move to the last line of the file
- Type `` `a `` to move back to the mark's position
- If you type `'a`, this will take you to the beginning of line on which
mark "a" has been set

**Example VII:** Set mark "c" on the second comma (,) of the 20<sup>th</sup>
in *animals.txt*.
- Hit ESC, type `20G` (navigate to line 20) and move to the
second comma by hitting `l` key (or right arrow key)
- Type `mc` (while on the normal mode) to set the mark "c" to the
cursor location.


**Example VIII:** Now we have to marks "a" and "c", it will be useful to
know how to review current marks.
- Hit ESC, type `:` to switch to command-line mode
- Type `marks` while in command-line mode and hit enter/return. This will
list all the default and user defined marks.


#### 4. Search for a pattern within the text file
Another strong suite of Vim lies in its pattern search functionality. It
is possible to search just for just a pattern, multiple patterns,
whole words, patterns that are in specific order, duplicate words etc.

**Example IX:** Find the first *bear* pattern in *animals.txt* file
from the normal mode.
- Hit ESC to switch to normal mode then type `/bear` and hit enter/return

Forward slash, `/`, is used to search the trailing pattern, in this case
"bear". Consequently, `/bear` will find the first matching pattern after
the cursor's current location and move the cursor to the beginning of
the pattern

**Example X:** Find the next *bear* pattern in *animals.txt*
file from the normal mode.
- Hit ESC to switch to normal mode then hit `n`

Each time you hit `n` the next matching pattern will be found and the
cursor will move to that location

**Example XI:** Find the previous *bear* pattern in *animals.txt*
file from the normal mode.
- Hit ESC to switch to normal mode then hit `N` (i.e. SHIFT+n)

Each time you hit `N` the previous matching pattern will be found and
the cursor will move to that location

**Example XII:** Find the pattern *badger* only if it is a whole word
in *animals.txt* file from the normal mode.
- Hit ESC to switch to normal mode
- Type `/` first before the pattern to be searched
- Type `\<badger\>` and hit ENTER/RETURN

Since we are looking for a whole word, a simply searching for "badger"
using `/badger` will not be useful as it will find any pattern containing
"badger" such as "honeybadger". To search whole words, we should use
`\<pattern\>` where `\<` represents the beginning of a word, and
`\>` represents the end of the word.

**Example XIII:** Find the next line containing *bear* pattern in
*animals.txt* file from the command-line mode.
- Hit ESC and type `:` to go to command-line mode
- Type `/bear` and hit enter/return

#### 5.  .
   To search for the same phrase in the opposite direction, type  N .

#### 6. Text substitution (or find&replace)
Many modern document and text editors provide functionality for finding
and replacing strings. Vim is no exception and it offers many additional
features.

The substitute operation can be done in command-line mode using `s` (short
for substitute). The general format of a substitute is `s/foo/bar` where
*foo* is the pattern to be substituted by *bar*.
<p>

**Example XIV:** Replace the first instance of "rabbit" with "squirrel"
in the 2<sup>th</sup> line of *animals.txt* using substitute. Save and exit.
- First let's create a backup file i.e. *animals_bckp.txt*
for *animals.txt*, then open *animals.txt* using vim from the terminal.
```bash
cp animals.txt animals_bckp.txt
vim animals.txt
```
- Hit ESC and go to command-line mode with typing ":"
- Type `2` to go to the second line
- Type `:` to start the command-line mode and write `s/rabbit/squirrel`
and hit enter/return
- Type `:` to start the command-line then type `wq` and hit enter/return

On the command-line mode we issued two distinct directives, `s/rabbit/squirrel`
and `wq`. Instead of doing the substitution and write&quit in two steps
we could have stack the commands using the pipe sign `|` which acts as
an "and".

- Type `:` to start the command-line mode and write `s/rabbit/squirrel | wq`
and hit enter/return
- Typing `:s/rabbit/squirrel | w | q` and hitting enter/return will
accomplish the same task
<p>

**Example XV:** Replace the first instance of "rabbit" with "squirrel"
in all the lines of *animals.txt* using substitute. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/rabbit/squirrel` and hit enter/return
- Type `:` to start the command-line then type `x` and hit enter/return

`%` indicates that whole buffer (practically whole document) will be
considered for substitution.
<p>

**Example XVI:** Replace all instances of "fox" with "wolf"
in all the lines of *animals.txt* using substitute. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/rabbit/squirrel/g` and hit enter/return
- Hit ESC to switch to normal mode and `ZZ`

Here `g` is short for global and it is used to replace all instances of
the pattern in a line.
<p>

**Example XVII:** Replace all instances of "wolf" with "fox" from line 20
 to 30 in *animals.txt* using substitute. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `20,30s/rabbit/squirrel/g` and hit enter/return
- Hit ESC to switch to normal mode and type `ZZ`

`20,30` before `s/rabbit/squirrel/g` indicates the range of lines to be
considered for substitution and it is inclusive.
<p>

**Example XVIII:** Replace all instances of "badger" with "Tasmanian devil"
in all the line of *animals.txt* using substitute but require
confirmation before the change. Save and exit. Make
sure not to substitute honeybadger.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/\<badger\>/Tasmanian devil/gc` and hit enter/return
- Hit ESC to switch to normal mode and type `ZZ`

`\<badger\>` searchers for only the whole words exactly matching badger.
`c` at the end is used for confirmation request.
<p>

**Example XIX:** Replace all instances of "Tasmanian devil" with "badger"
in all the line of *animals.txt* using substitute. Make the search case
insensitive. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/tasmanian devil/badger/gi` and hit enter/return
- Hit ESC to switch to normal mode and type `ZZ`

`i` at the end is used to make the search case insensitive.

--------------
# More on Editing Text From Bash Shell (no UI)

In cases where you need to repeat some specific tasks in editing your
files many times, opening the UI -user interface- and carrying out the
tasks will become inefficient. Furthermore if you are submitting
a workflow for batch processing, UI is impractical.

For such tasks, Vim can be used from your bash command line. It is
possible to pass command and command-line mode directives to Vim from
terminal.
<p>

**Example I:** Replace all instances of "wolf" with "fox"
in all the lines of *animals.txt* using Vim's substitute function
without starting the UI.

- In your bash terminal type the following:
```bash
vim animals.txt -c '%s/wolf/fox/g | wq'
```

You may recognize `%s/wolf/fox/g` and `wq` commands as we used them
to substitute all instances of "wolf" with "fox" in *animals.txt* and
save&quit the file respectively when in command-line mode. The flag "-c"
executes the following command as if the vim is operating in command-line
mode.

<p>

**Example II:** Prepare a vim script (say *operations.vim*) that includes
the commands to be applied on the *animals.txt*. The commands should \
replace all instances of "bear" with "giraffe" in all the lines of
*animals.txt*, save the file and exit.

- First create the file *operations.vim*
```bash
vim operations.vim
```
- Switch to insert mode by hitting `i`
- Type `:%s/bear/giraffe/g` on the first line of *operations.vim*
- Type `ZZ` on the second line of the *operations.vim*
- Switch to normal mode by hitting ESC and save&quit by hitting `ZZ`
- Run the command below in the terminal:
```bash
vim animals.txt -s operations.vim
```

The flag "-s" reads normal mode commands from a script file and applies
them to the input file

# Running shell commands from inside the vim

:! <command> --> runs the command
:!! --> repeats the last command
:silent !<command? --> eliminates the need to hit enter after the command is done
:r !<command>  --> push the output of command into the current buffer
:%!<command> -->to pass the current buffer from a command (:%!tac or :%!nl)
:3,$! sort -u --> send line range (3 to EOF) as buffer to command

# Using split windows for different files in Vim
It is possible to open multiple files spreading horizontally or
vertically in a single UI window. This can be achieved while you are
starting the UI or from within the UI.

**Example I:** Open the two files *animals.txt* and *editing.txt* in a
split windows oriented horizontally, then quit all without saving.
- Issue the following command on your terminal
```bash
vim -o animals.txt editing.txt
```
- Once the split windows are opened switch to command-line mode by
typing `:`
- Type `q!` and hit ENTER/RETURN

**Example II:** Open the two files *animals.txt* and *editing.txt* in a
split windows oriented vertically, then quit all without saving.
- Issue the following command on your terminal
```bash
vim -O animals.txt editing.txt
```
- Once the split windows are opened switch to command-line mode by
typing `:`
- Type `q!` and hit ENTER/RETURN

**Example III** Open the *animals.txt* first then open *editing.txt* by
splitting the window horizontally. Finally open *introduction.txt* in a
vertically split pane. Move the cursor from one pane to another.
- Issue the following command on your terminal
```bash
vim -O animals.txt
```
- Switch to command-line mode by typing `:`
- Type `split editing.txt`
- Switch to command-line mode by typing `:`
- Type `vsplit introduction.txt`
- Switch to normal mode by hitting ESC
- While holding CTRL hit `w` twice (i.e. CTRL+w+w) which will move the
cursor to the next pane

https://codeincomplete.com/posts/split-windows-and-tabs-in-vim/

# Additional Resources

Cheat sheets:

1. [Vim Cheat Sheet](https://vim.rtorr.com/)
2. [Graphical Cheat Sheet](http://www.viemu.com/vi-vim-cheat-sheet.gif)
3. [A Great Vim Cheat Sheet](http://vimsheet.com/)
4. [Advanced Vim Cheat Sheet](http://vimsheet.com/advanced.html)

Interactive Online Learning:

1. [VIM Adventures](https://vim-adventures.com/)
2. [Interactive Vim tutorial](http://www.openvim.com/)
