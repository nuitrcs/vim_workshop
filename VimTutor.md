# The very basics

0. (Install and) Start Vim (Installation instructions will be provided prior to training)

1. Vi versus Vim?

2. Three modes: insert mode, command mode and command-line mode
    - Switching to insert mode: Press i when in command mode
    - Switching to command mode: Press <ESC> to exit back to command mode from any other mode
    - Switching to command-line mode: Press ":" when in command mode

4. Navigation: h, j, k, l (or arrow keys)

5. How to no-save/quit, save/quit: q!, wq, x, ZZ

--------------

# More on Text Editing

1. Delete command: d

2. Using motion

    d   motion
    - w - until the start of the next word, EXCLUDING its first character.
    - e - to the end of the current word, INCLUDING the last character.
    - $ - to the end of the line, INCLUDING the last character.

3.  Using count for a motion

    d   number   motion

4. Undo command: u

5. Put command: p

6. Replace command: r

7. Change command: c

8. Other insert commands: o, a

9. Copy paste: Visual mode with  v, yank with y, p

10. Named buffers

--------------

# More on Navigation and Search
Let's discuss some fast navigation techniques between lines and pattern
search methods in vim. For these exercises we will use *animals.txt*.

#### 1. Moving to start and end of the file

**Example I:** Move to start/end of the in command mode
- Switch to command mode by hitting ESC. Type `G` to move to the last
line of the file
- Switch to command mode by hitting ESC. Type `gg` to move to the first
line of the file

**Example II:** Move to start/end of the file in command-line mode
- Switch to command-line mode by hitting ESC and then typing `:`. Type
`$` and hit enter/return to move to the last line of the file
- Hit ESC then type `:` to switch to command-line mode. Type `0` and hit
enter/return to move to the beginning of the file

#### 2. Moving to an arbitrary line

**Example I:** Move to a line using the line number in command mode
- Hit ESC, type the number of the line, say 14, and then type `G` (i.e.
SHIFT+g)

**Example II:** Move to a line using the line number in command-line mode
- Hit ESC, type `:`, then type the number of the line, say 23, hit
enter/return

**Example III:** Let's make sure we moved to 23rd line by showing the
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

**Example I:** Let's set mark "a" on the first comma (,) of the 9<sup>th</sup>
line in *animals.txt*. After setting "a" mark for this location move to
the end of the file. Using the mark, return to original location.
- Hit ESC, type `9G` (navigate to line 9) and move to the
first comma by hitting `l` key (or right arrow key)
- Type `ma` (while on the command mode) to set the mark "a" to the
cursor location.
- Type `G` to move to the last line of the file
- Type `` `a `` to move back to the mark's position
- If you type `'a`, this will take you to the beginning of line on which
mark "a" has been set

**Example II:** Set mark "c" on the second comma (,) of the 20<sup>th</sup>
in *animals.txt*.
- Hit ESC, type `20G` (navigate to line 20) and move to the
second comma by hitting `l` key (or right arrow key)
- Type `mc` (while on the command mode) to set the mark "c" to the
cursor location.


**Example III:** Now we have to marks "a" and "c", it will be useful to
know how to review current marks.
- Hit ESC, type `:` to switch to command-line mode
- Type `marks` while in command-line mode and hit enter/return. This will
list all the default and user defined marks.


#### 4. Search for a pattern within the text file
Another strong suite of Vim lies in its pattern search functionality. It
is possible to search just for just a pattern, multiple patterns,
whole words, patterns that are in specific order, duplicate words etc.

**Example I:** Find the first *bear* pattern in *animals.txt* file
from the command mode.
- Hit ESC to switch to command mode then type `/bear` and hit enter/return

Forward slash, `/`, is used to search the trailing pattern, in this case
"bear". Consequently, `/bear` will find the first matching pattern after
the cursor's current location and move the cursor to the beginning of
the pattern

**Example II:** Find the next *bear* pattern in *animals.txt*
file from the command mode.
- Hit ESC to switch to command mode then hit `n`

Each time you hit `n` the next matching pattern will be found and the
cursor will move to that location

**Example III:** Find the previous *bear* pattern in *animals.txt*
file from the command mode.
- Hit ESC to switch to command mode then hit `N` (i.e. SHIFT+n)

Each time you hit `N` the previous matching pattern will be found and
the cursor will move to that location

**Example IV:** Find the pattern *badger* only if it is a whole word
in *animals.txt* file from the command mode.
- Hit ESC to switch to command mode
- Type `/` first before the pattern to be searched
- Type `\<badger\>` and hit ENTER/RETURN

Since we are looking for a whole word, a simply searching for "badger"
using `/badger` will not be useful as it will find any pattern containing
"badger" such as "honeybadger". To search whole words, we should use
`\<pattern\>` where `\<` represents the beginning of a word, and
`\>` represents the end of the word.

**Example V:** Find the next line containing *bear* pattern in
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

**Example I:** Replace the first instance of "rabbit" with "squirrel"
in the 2<sup>th</sup> line of *animals.txt* using substitute. Save and exit.

</p>First let's create a backup file i.e. *animals_bckp.txt*
for *animals.txt*, then open *animals.txt* using vim from the terminal.

```bash
cp animals.txt animals_bckp.txt
vim animals.txt
```

Substitute the firsy instances of "rabbit" with "squirrel".
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

**Example II:** Replace the first instance of "rabbit" with "squirrel"
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

**Example III:** Replace all instances of "fox" with "wolf"
in all the lines of *animals.txt* using substitute. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/rabbit/squirrel/g` and hit enter/return
- Hit ESC to switch to command mode and `ZZ`

Here `g` is short for global and it is used to replace all instances of
the pattern in a line.
<p>

**Example IV:** Replace all instances of "wolf" with "fox" from line 20
 to 30 in *animals.txt* using substitute. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `20,30s/rabbit/squirrel/g` and hit enter/return
- Hit ESC to switch to command mode and type `ZZ`

`20,30` before `s/rabbit/squirrel/g` indicates the range of lines to be
considered for substitution and it is inclusive.
<p>

**Example V:** Replace all instances of "badger" with "Tasmanian devil"
in all the line of *animals.txt* using substitute but require
confirmation before the change. Save and exit. Make
sure not to substitute honeybadger.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/\<badger\>/Tasmanian devil/gc` and hit enter/return
- Hit ESC to switch to command mode and type `ZZ`

`\<badger\>` searchers for only the whole words exactly matching badger.
`c` at the end is used for confirmation request.
<p>

**Example VI:** Replace all instances of "Tasmanian devil" with "badger"
in all the line of *animals.txt* using substitute. Make the search case
insensitive. Save and exit.

- Open *animals.txt* using vim from the terminal
```bash
vim animals.txt
```
- Hit ESC and type `:` go to command-line mode
- Write `%s/tasmanian devil/badger/gi` and hit enter/return
- Hit ESC to switch to command mode and type `ZZ`

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
- Switch to command mode by hitting ESC and save&quit by hitting `ZZ`
- Run the command below in the terminal:
```bash
vim animals.txt -s operations.vim
```

The flag "-s" readsnNormal mode commands from a script file and applies
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

**Example I:** Open the two files *animals.txt* and *basics.txt* in a
split windows oriented horizontally, then quit all without saving.

- Issue the following command on your terminal
```bash
vim -o animals.txt basics.txt
```
- Once the split windows are opened switch to command-line mode 


**Example II:** Open the two files *animals.txt* and *basics.txt* in a
split windows oriented vertically

**Example III**

in all the lines of *animals.txt* using Vim's substitute function
without starting the UI.

split and vsplit
vim -o <filename1> <filename2>
vim -O <filename1> <filename2>
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
