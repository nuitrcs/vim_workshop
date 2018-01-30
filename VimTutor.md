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
- Hit ESC, type the number of the line and then type `G`

**Example II:** Move to a line using the line number in command-line mode
- Hit ESC, type `:`, then type the number of the line, hit enter/return

#### 3. Marks

#### 3. Search for a pattern within the text file

**Example I:** Move to the
- Hit ESC,

Type  /  followed by a phrase to search for the phrase


#### 5. To search for the same phrase again, simply type  n .
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
in the 2nd line of *animals.txt* using substitute. Save and exit.

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
save&quit the file respectively.

<p>

**Example II:** Replace all instances of "wolf" with "fox"
in all the lines of *animals.txt* using Vim's substitute function
without starting the UI.

vim deneme -S script.vim (in script.vim commands-line mode commands without :)
vim deneme -s script.vim (in script.vim both command-line {with :} and normal mode commands {without :} )

# Running shell commands from inside the vim
:! <command> --> runs the command
:!! --> repeats the last command
:silent !<command? --> eliminates the need to hit enter after the command is done
:r !<command>  --> push the output of command into the current buffer
:%!<command> -->to pass the current buffer from a command (:%!tac or :%!nl)
:3,$! sort -u --> send line range (3 to EOF) as buffer to command

# Additional Resources

Cheat sheets:

1. [Vim Cheat Sheet](https://vim.rtorr.com/)
2. [Graphical Cheat Sheet](http://www.viemu.com/vi-vim-cheat-sheet.gif)
3. [A Great Vim Cheat Sheet](http://vimsheet.com/)
4. [Advanced Vim Cheat Sheet](http://vimsheet.com/advanced.html)

Interactive Online Learning:

1. [VIM Adventures](https://vim-adventures.com/)
2. [Interactive Vim tutorial](http://www.openvim.com/)
