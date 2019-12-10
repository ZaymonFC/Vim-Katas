### 01 insert at end of line

Change this text:

```javascript
var foo = 1
var bar = 'a'
var foobar = foo + bar
```

to this:

```javascript
var foo = 1;
var bar = 'a';
var foobar = foo + bar;
```

Use `A` to insert at the end of line.

Add ';' to the end of these lines using `A`!

### 02 insert at beginning of line

Change this text:

```javascript
var foo = 1
var bar = 'a'
var foobar = foo + bar
```

to this:

```javascript
;var foo = 1
;var bar = 'a'
;var foobar = foo + bar
```

Use `I` to insert at the beginning of line.

Add ';' to the beginning of these lines using `I`!

### 03 one step back two forward

Change this text:

```javascript
var foo = "method("+argument1+","+argument2+")";
```

to this:

```javascript
var foo = "method(" + argument1 + "," + argument2 + ")";
```

Steps:

1. find "+" with `f+`
2. delete and switch to insert mode with `s`
3. Type ` + `
4. Leave insert mode
5. find the next "+" with `;`
6. Repeat with `.`

### 05 find and replace by hand

Replace the first and third occurrence of "content" with "copy" in this text:

```text
"...We're waiting for content before the site can go live...

...If you are content with this, let's go ahead with it...

...We'll launch as soon as we have the content...”
```

Steps:

1. Find the word content by `/content`
2. Replace the word by `cw copy`
3. Go to the next one `n`
4. Go to the last one `n`
5. Repeat command `.`

### 10 use counts

Change this text:

```css
.blog, .news { background-image: url(/sprite.png); }
.blog { background-position: 0px 0px }
```

to this:

```css
.blog, .news { background-image: url(/sprite.png); }
.blog, .news { background-image: url(/sprite.png); }
.news { background-position: -180px 0px }
```

Moves:

1. `yyp` to duplicate the last line
2. `cW.news<Esc>` to replace the word 'blog' with 'news'
3. `180<C-x>`

### 12 combine and conquer

Use this text for practicing:

```text
This is some text, I hope you like it.
  one more
 and more
```

Do the following exercises on it:

`2cw` - change 2 words
`2dw` - delete 2 words
`2yw` - yank 2 words into register
`g~`  - swap case
`gu`  - make selection all lower case
`gU`  - make selection all UPPER case
`>`   - shift right
`<`   - shift left
`=`   - auto indent

### 13 delete in insert mode

This is again some text.

Type the sentence again and practice these:

`<C-h>` - delete back 1 char
`<C-w>` - delete back 1 word
`<C-u>` - delete back to the start of the line

```text
This is again
```

### 15 paste from register in insert mode

Here is an unfinished excerp of text:

```text
Practical Vim, by Drew Neil
Read Drew Neil's
```

Copy and paste the page title here:

`yt,` - yanks the text 'Practical Vim
`jA ` - jumps to the end of the second line and adds a space
`<C-r>0` - pastes the text from register
`.<Esc>` - adds the dot to the very end

Make it look like this:

```text
Practical Vim, by Drew Neil
Read Drew Neil's Practical Vim.
```

### 16 back of envelop calculations in place

Suppose that we've just typed the following:

```text
6 chairs, each costing $35, totals $
```

`A` - append mode
`<C-r>=6*35` - put the calculation result in register
`<CR>` paste the result at the cursor

You should get this:

```text
6 chairs, each costing $35, totals $210
```

### 18 insert unusual characters

Insert the following unusual characters:

¿ - ¢

`:digraphs` - Look up all the possible options
`<C-k>?I` - will give you ¿
`<C-k>Ct` - will give you ¢

### 19 overwrite existing text with replace

Example text:

```text
Typing in insert mode extends the line. But in replace mode
the line length does not change.
```

Change the ". But" to ", but" in replace mode

`f.` - find the dot
`R, b<Esc>` - enter into replace mode, replace . with comma, space and replace "B" with "b"

`gR` triggers the Virtual Replace Mode, which is better, as that handles the tab spaces.

### 20 grokking visual mode

Given the following text:

```text
I like March better than anything.
```

Change the word "March" to "April"

Use `jfM` to jump to the beginning of "March"
Visually select the word with `viw`
Hit `c` to change selection
Type `April<Esc>` to add the word "April"

### 21 defining visual selection

There are 3 visual modes:
`v` - characterwise
`<C-v>` - block
`V` - linewise

`gv` - reselect last visual mode

Practice those on this block of text:

```text
This is some text.
Another one is right here.
Here is more and more text.
```


### 22 repeat likewise visual commands

Suppose we have this Python code:

```python
def fib(n):
    a, b = 0, 1
    while a < n:
print a,
a, b = b, a+b
fib(42)
```

Set `:set shiftwidth=4 softtabstop=4 expandtab`

`Vj` - Visually select the line
`>..`- Indent the text and repeat

The result should look like this:

```python
def fib(n):
    a, b = 0, 1
    while a < n:
        print a,
        a, b = b, a+b
fib(42)
```

### 23 prefer operators to visual commands

Change the text in the tags to be upper-case.

```html
<a href="#">one</a>
<a href="#">two</a>
<a href="#">three</a>
```

`{start}` - on the first line, first char
`gUit` - make the word inside the tag ('it' ~ inside tag) upper case
`j.` - go to next line and repeat
`j.` - go to next line and repeat

This is what the HTML snippet should look like:

```html
<a href="#">ONE</a>
<a href="#">TWO</a>
<a href="#">THREE</a>
```

`gU{motion}` - visual mode equivalent in normal mode

### 24 editing tabular data with visual block mode

Change this text:

```
Chapter             Page
Normal Mode           15
Insert Mode           31
Visual Mode           44
```

Make it look like this

```
Chapter      | Page
-------------------
Normal Mode  |   15
Insert Mode  |   31
Visual Mode  |   44
```

`<C-v>3j` - block select the column to the point we need to delete back
`d...` - delete the columns
`gv` - reselects the same visual selection
`r|` - repeats adding the pipe
`yyp` - duplicate the first row
`Vr-` - select the entire line, repeat the "-" for the row

### 25 changing column of text

Suppose there is this text:

```css
li.one   a{ background-image: url('/images/sprite.png'); }
li.two   a{ background-image: url('/images/sprite.png'); }
li.three a{ background-image: url('/images/sprite.png'); }
```

Change 'images' to 'components' to look like this:

```css
li.one   a{ background-image: url('/components/sprite.png'); }
li.two   a{ background-image: url('/components/sprite.png'); }
li.three a{ background-image: url('/components/sprite.png'); }
```

Steps to get there:

`<C-v>jje` - visual select the entire block
`c` - change the selection
`components` - type in the text 'components'
`<Esc>` - add the word 'components' to the other lines
Note, `<C-c>` is not `<Esc>` :-(


### 26 append after a ragged visual block

We already had this text before:

```javascript
var foo = 1
var bar = 'a'
var foobar = foo + bar
````

Append ';' at the end of each line using visual mode.

Start on the first line, at "1"
`<C-v>jj$`
`A;` - appends the ';' at the end of each line
`<Esc>` - will apply it for each selected line

### 28 exec commands on one or more consecutive lines

Look at this HTML sample:

```html
<!DOCTYPE html>
<html>
  <head><title>Practical Vim</title></head>
  <body>
    <h1>Practical Vim</h1>
  </body>
</html>
```

Do the following exercises on the text avove:

`:7` - move to line 7
`:print` print current line
`:9p` - move to line 9, print it
`:10d` - move to line 10 and delete it in 1 command
`:8,11p` - print range
`:.,$p` - print from current line ('.') to the end ('$')
`:%p` - % means the entire file
visual select multiple lines, `:'<,'>p` - prints the visual selection
`:/<html>/,/<\/html>/p` - print out everything within html
`:/<html>/+1,/<\/html>/-1p` - without the html tags

### 29 duplicate or move lines

Given this text:

```
Shopping list
    Hardware store
        Buy new hammer
    Beauty parlor
        Buy nail polish remover
        Buy nails
```

Do the following exercises on the text above:

Start at 'H' on line 7
`:11copy.` - copies line to current line
`:11t.` - should do the same
`:t.` - duplicate current line
`:t$` - copy current line to end of file

`:11m$` - move line 11 to the end of the file
Visual select 2 lines
`:'<,'>m$` move the selected lines to the end of the file

### 30 run normal mode commands across range

There is a block of text like this:

```javascript
var foo = 1
var bar = 'a'
var baz = 'z'
var foobar = foo + bar
var foobarbaz = foo + bar + baz
```

`A;<Esc>` - Add semicolon to the end of first line
Visual select the rows
`:'<,'>normal.` - repeats the command for all highlighted lines

or solve it like this:
`:'<,'>normal A;` - executes normal command for all highlighted lines

Add semi-colon to all lines in file:
`:%normal A;`

Comment out an entire JS file:
`:%normal i//`

### 31 repeat last ex command

`:bn` - move to the next buffer
`@:` - repeat last ex command
`@@` - repeat last ex command

### 32 tab complete your ex command

Type this in the command menu:

`:col<C-d>`

The options 'colder colorscheme should be displayed

### 33 insert current word at command prompt

Rename the variable 'tally' to 'counter':

```javascript
var tally;
for (tally=1; tally <= 10; tally++) {
  // Do something with tally
};
```

Start on line 6 at the 't' character
`*` - selects all the words 'tally'
`cwcounter<Esc>` - replaces the word with counter
`:%s//<C-r><C-w>/g` - gets the current word for the substitute command

### 35 running commands in shell

1. Combine two commands with one shell execution:

`:write !sh` - will write this file (a vim command) and start a shell

2. Sort the content of this text:

```
first name, last name, email
john,smith,john@example.com
drew,neil,drew@vimcast.org
jane,doe,jane@example.com
```

Visual highlight the lines to be sorted
`:'<,'>!sort -t',' -k2` - the sort shell command is used to sort the lines

3. Pull up command history in vim

`q:` will show normal mode history
`q/` will show search history

### 39 split windows

All about split windows

`<C-w>v` - Divide the window vertically
`<C-w>s` - Divide the window horizontally

Switch between windows:
`<C-w>w` - cycle open windows
`<C-w>h`, `<C-w>j`, `<C-w>k`, `<C-w>l` move around in the windows

`:cl[ose]` or `<C-w>c` - close active window
`:on[ly]` or `<C-w>o` - keep the active window, closing the others

`<C-w>=` - equalize all windows
`<C-w>_` - maximize height of the active window
`<C-w>|` - maximize width of the active window

### 40 organize window layout with tab pages

All about tab pages

`:tabe 01..` - Open the 01 markdown file in a new tab
`gt` - move ot next tab
`gT` - move to previous tab

`:sp 02` - open the 02 markdown file in a horizontal split window
`<C-w>T` - move the current window into its own tab

`:tabc` - close the current tab
`:tabo` - keep the active page, close all tabs

### 49 find by character

Find the c in '{char}'

Find the first occurence of {char} and move to it.

`fc` - finds the first char
`;;` - move to it by repeating the search with ;
`Fc` - search backwards to the previous character

### 50 operate with a search motion

There is this text, delete the part "take time but eventually".

```
This phrase takes time but
eventually gets to the point.
```

`v` - enter into character-wise visual mode
`/ge<CR>` - highlight 'til the word 'gets'
`h` - moves back 1 char
`d` - deletes the content

Here is a quicker way of doing the same thing:

`d/ge<CR>` - does the whole thing in 1 move

### 51 trace your selection with precision text objects

Let's say there is this JS snippet:

```javascript
var tpl = [
  '<a href="{url}">{title}</a>'
]
```

`vi}` - enter into visual mode, select inside }
`a"` - select indluding "
`i>` - select inside angle bracket
`it` - select inside tag
`at` - select at tag, or the whole tag
`a]` - select inside square bracket

Exercise:

`ci"#<Esc>` - change the url to #
`cit click here<Esc>` - change the {title} to 'click here'

### 52 jump between matching parentheses

Let's say there is this console statement:

```javascript
console.log([{'a':1},{'b':2}]);
```

Start on the first opening paren
`%` - jumps to the closing paren
`h` - select the last ']' bracket
`%` - jump to the first '[' bracket
`l` - select the first curly '{'
`%` - jump to the last curly

```ruby
%w{London Berlin New\ York}
```

`dt{` - deletes the '%w' part
`%` - jumps to the closing curly
`r]` - replace curly with square bracket
`tick tick` - jumps to the first curly
`r[` - replaces the opening curly with square bracket

### 53 mark your place and snap back to it

`m{a-zA-Z}` - marks the location of the cursor

`:18` - go to the 18th row
`ma`  - mark the line
`G`   - go to the bottom of the page
`'a`  - jump back to the mark

_Built in marks_

`'.` - location of last change
`'^` - location of last insert
`'[` - start of last change or yank
`']` - end of last change or yank
`'<` - start of last visual selection
`'>` - end of last visual selection

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70

### 55 traverse the jump list

`<C-o>` - is like the browser's back button, but here it's used for files
`<C-i>` - is like the browser's forward button

`:jumps` - will list all the different jump points

### 56 traverse the change list

`:changes` -  will list all the changes during an editing session

`g;` - traverse backward the changelist
`g,` - traverse forward the changelist

`backtic .` - moves you to the last change
`backtic ^` - moves you to the last insertion
`gi` - live insert mode, move around, this takes you back to insert mode where I left off

### 58 snap between files using global marks

While `m{a-z}` sets a local mark in the current file
`m{A-Z}` - sets a global mark

`vs 01_` - open the 01_ markdown file
`:10` - go to the 10th line
`mA` - mark the position there
switch back to this file
`backticA` - takes you back to the file's location

`:vimgrep /cursor/ **` - searches for the word in the current dir,
  takes you there
`:cn` - takes you to next result
`:cp` - take you to previous result

### 59 delete yank and put with unnamed register

Let's say we made a mistake of typing this text:

```
Practica lvim
```

Start on the last character 'm'
`F space` - to search for space backwards
`x` - to cut
`p` - to paste

`xp` - transpose two chars

Similar concept can be used for lines

```
2) line two
1) line one
3) line three
```

Start on the first line
`dd` - to cut out the line
`p` - to insert

`ddp` - to transpose lines
`yyp` - to duplicate lines

## Using the unnamed register

```javascript
collection = getCollection();
process(somethingInTheWay, target);
```

`yiw` - yanks the word collection into the register
`jww` - moved to the beginning of "somethingInTheWay"
`dw` - deletes the word
`P` - pastes before comma

But oops, try this instead of `dw`
`"_de` - deletes the word, but does not put it into register

`"_d{motion}` - deletes the word without putting it into the register

### 60 grok vim registers

Given this text

```text
1) This is the first block of text
2) Another block of text
```

`"ayy` - will yank the first line into register "a"
`"byy` - yank the 2nd line into register "b"
`"bp` - paste in from register "b" first
`"ap` - paste in from register "a" after

Use the yank register to fix the text from previous kata

```javascript
collection = getCollection();
process(somethingInTheWay, target);
```

`yiw` - to yank the word into yank register
`jww` - to go to next line to the beginning of "somethingInTheWay"
`dw` - will delete the word
`"0P` - will insert the word from the yank register

`:reg "0` - will inspect the yank and unnamed registers

`"_` - is the black hole register, nothing returns from there

`"+` - system clip board
`"*` - system selection

Visual select this entire doc, yank its content into `"+yy`, go to
Pages and insert it into a new document there

`"=` - expressions register

`i` - switch to insert mode
`<C-r>=` - switches to expression register
`6*35<CR>` - will provide the text "210" and drop back into insert mode

## More registers
`<C-r>%` - name of the current file
`<C-r>#` - name of the alternate file
`<C-r>.` - last inserted text

### 61 replace visual selection with a register

There is an easier way to swap the word "somethingInTheWay" with "collection"

```javascript
collection = getCollection();
process(somethingInTheWay, target);
```

`yiw` - to yank the word into the yank register
`jww` - to move to 's' char in "somethingInTheWay"
`ve` - visually selects the entire word
`p` - will insert the yanked word over the visually selected text

Another exercise: swap the 2 words "chips" and "fish"

I like chips and fish.

Start on 'I'
`fc` - find the first word to swap
`de` - delete the word
`mm` - mark the place
`ww` - move to 'f' in "fish"
`ve` - visually select the word
`p` - paste the word over "fish"
`backtickm` - to take back to the mark position
`P` - to insert the word fish

### 62 pasting from a register

Use the yank register to fix this:

```javascript
collection = getCollection();
process(somethingInTheWay, target);
```

`yiw` - yank the word into the yank register
`jww` - move down 1 line to 'somethingInTheWay'
`ciw<C-r>0` - insert the text from the yank register

Duplicate the `<tr>` tag content

```html
<table>

  <tr>
    <td>keystrokes</td>
    <td>buffer contents</td>
  </tr>

</table>
```

`yap` - yanks the paragraph
`5j` - move down 5 lines
`gP` - insert above

### 64 record and execute a macro

Given this text:

```javascript
foo = 1
bar = 'a'
foobar = foo + bar
```

Start on the first line
`qa` - start recording your macro in the "a" register
`A;` - append semicolon at the end of the line
`Ivar<Space><Esc>` - add "var" to the beginning of the line
`q` - quit recording the macro

Inspect what's in register a with `:reg a`

`@{register}` - will replay the macro

`j` - go to next line
`@a` - replay it on second line
`j@@` - replay it on the next line

### 66 play back with a count

Make this text:

```javascript
var x = "("+a+","+b+","+c+","+d+","+e+")";
```

Look like this:

```javascript
var x = "(" + a + "," + b + "," + c + "," + d + "," + e + ")";
```

`f+` - find the first "+"
`s<Space>+<Space><Esc>` - add spaces around "+"
`qq;.q` - record the `;.` keystrokes in the q register
`22@q` - run the macro 22 times, it's OK to run it more

### 67 repeat a change on contiguous lines

Given this text:
```
1. one
2. two
3. three
4. four
5. five
```

Change it to be like this:
```
1) One
2) Two
3) Three
4) Four
5) Five
```

`qa` - record the macro in the "a" register
`0f.` - find the dot on the first line
`r)` - replace the dot with a ")"
`w~` - title-case the word
`j` - move down 1 line
`q` - quit recording the macro

We can replay the macro with this:
`@a` - and `@@` after that

But what if there is line barrier in the text like this?
```
1. one
2. two
3. three
// Some comment
4. four
5. five
```

Replay it with the highlighted text:
`'<,'>norm @a` - this will replay the macro from the "a" register on the highlighted lines

### 68 append commands to macro

Let's say we recorded this macro:

```text
1. one
2. two
3. three
4. four
```

`qa` - record in "a" register
`0f.r)w~` - replace "." with ")" and tile-case word
`q` - quit recording macro

We forgot adding the "j" to move to the next line.

Inspect what got recorded:

`:reg a` - look at what's in "a" register

`qA` - append to the macro recorded in "a" register
`j` - move to next line
`q` - quit recording the macro

Look at it again, you should have the "j" at the end

### 69 act upon a collection of files

`:cd ruby_module` - move into the "ruby_module" dir
`:args *.rb` - open all the .rb files there
`:args` - review all the files

`:first` - move to the first
`:last` - move to the last

Start on the first one
`qa` - record the macro into "a" register
`gg/class<CR>` - find the "class" word
`Omodule Rank` - add the "module Rank" above
`j>G` - indent the file
`Goend<Esc>` - add the "end" to the bottom
`q` - end recording the macro

`:edit!` - undo all edits of the first file
`:argdo normal @a` - run the macro in parallel

`qA` - append to the previously recorded macro
`:next` - go to the next file in buffer
`q` - quit recording
`22@a` - repeat the macro 22 times - in series

Executing the macro in series might be slower, but if error occurs, it stops on the file where the error is.

### 70 evaluate an iterator to number items in a list

Change this text:

```shell
partridge in a pear tree
turtle doves
French hens
calling birds
golden rings
```

to:

```shell
1) partridge in a pear tree
2) turtle doves
3) French hens
4) calling birds
5) golden rings
```

Use the expression register to do the loop
`:let i=1` - set the i var to 1
`qa` - record the the macro in the 'a' register
`I<C-r>=i<CR>)<Esc>` - insert the value of i
`let i += 1` - increment i by 1
`q` - finish recording the macro

`:'<,'>norm @a` - execute the macro on the visual selection in parallel

### 71 edit the contents of a macro

```text
1. One
2. Two
3. three
4. four
```

Some of the lines use capital letter, `~` would just switch casing, we need to use `vU` here, which makes the char upper-cased at the cursor.

This is what is should look like after your changes:

```test
1) One
2) Two
3) Three
4) Four
```

`:put a` - paste the content of register a into the doc
Edit the macro by replacing `~` with `vU`
Remove the last J, as it will be added back
`"add` - replaces the current line with register a

Characterwise yank is a safer bet, try this instead:
`0` - go back to the first char in line
`"ay$` - yank the content of the line
`dd` - delete the line

### 72 tune the case sensitivity of search patterns

Here is a small text snippet to search on:

```
foo
foo & foo
foo & Foo
FOO & foo
```

Setting case sensitivity per search:
`/foo` - Search for the word "foo"
`/foo\C` - Search for the word "foo", case sensitive
`/foo\c` - Search for the word "foo", case insensitive

`set smartcase` - cancels out of case insensitive search when first upper-cased character is typed

### 73 use the v pattern switch for regex search

Let's use this snippet of CSS:

```css
body   { color: #3c3c3c; }
a      { color: #0000EE; }
strong { color: #000; }
```

`/#\([0-9a-fA-F]\{6}\|[0-9a-fA-F]\{3\}\)` - this regex will match all the hex values

The `\v` switch make Vim's regex search like Perl, Python and Ruby.

`/\v#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})` - the search works the same way, but it does not need to escape the special characters.
`/\v#(\x{6}|\x{3})` - will be the same as above, but it's using `\x` character class
`

### 74 use the backslash v literal switch for verbatim search

Use this excerpt of text:

```
The N key searches backwards...
... the \v pattern swtich (a.k.a. very magic search)...
```

`/a.k.a.` - will match more than 1 result
`/a\.k\.a\.` - will find the right word, but escaping the dots is a lot of work
`/\Va.k.a.` - turns off all special char in regex, only backslash is escaped

General rule:
If you search for a regular expression use the `\v`, if you want to search for
verbatim text, use the `\V` switch.


### 76 stake the boundaries of a word

```
the problem with these new recruits is that
they don't keep their boots clean.
```

`/the` - will yield results with words where "the" is embedded, like "they"
`/\v<the>` - will find only the exact macthes

The `<` and `>` are zero-width items, they represent boundaries.

`/\<the\>` - will match the angle brackets as chars



### 77 stake the boundaries of a match

Sometimes we might want to specify a broad pattern, then focus on a subset
of that match. Vim's `\zs` and `\ze` items allow just to do that.

```text
Practical Vim is really a great book.
```

`/Practical Vim<CR>` - will match the word "Practical Vim"
`/Practical \zsVim<CR>` - will match the "Vim" from the maches

```test
Match "quoted words" not quote marks.
```

`/\v"[^"]+"` - matches the word with quotes (`[^"]+` - match anything that's not a quote mark)
`/\v"\zs[^"]+\ze"` - matches words inside the quote


### 78 escape problem characters

```text
Search items: [http://vimdoc.net/search?q=/\\][s]
...
[s]: http://vimdoc.net/search?q=/\\
```

`"uyi[` - yank the url into register 'u'
`/\V<C-r>u<CR>` - to populate the search field

We could escape the backslash, but that's tedious.

Vim will search forward with `/` character, but with `?` it searches backwards.

`?http://vimdoc.net/search?q=/\\` - will match everything until the '?'

### 79 meet the search command

```text
Going to Union Station takes time,
but this time can be an advantage.
Use it right, and travelling time
will pay off.
```

`/time` - search for time forward
`?time` - search for time backwards
`n` - go to the next result
`N` - go to the previous result - it always goes in the opposite direction
`/<CR>` - will execute the last search forward
`?<CR>` - will execute the last search backwards

Use the "Up" button to browse search history.

### 82 count the matches for current pattern

Use this text to search on:

```text
Going to Union Station takes time,
but this time can be an advantage.
Use it right and travelling time
will pay off.
```

`/time` - to search for the word 'time'
`%s///gn` - to count the number of matches

### 83 offset cursor to the end of a search match

Use this text as an example:

```text
Aim to learn a new programming lang each year.
Which lang did you pick up last year?
Which langs would you like to learn?
```

Task: replace "lang" with "language".

`{start} on A of Aim` - initial position
`/lang/e<CR>` - find the word 'lang'
`auage<Esc>` - add "uage" to "lang"
`n.n.` - repeat it twice

### 84 operate on complete search match

Make this:

```ruby
class XhtmlDocument < XmlDocument; end
class XhtmlTag < XmlTag; end
```
to be like this:

```ruby
class XHTMLDocument < XMLDocument; end
class XHTMLTag < XMLTag; end
```

One possible solution:
`/\vX(ht)?ml\C<CR>` - find the items to change
`gU//e<CR>` - make the text uppercase - we use '//e' as a motion
`//<CR>` - move to next item
`.` - rerun the command
`//<CR>.` - move to next item and rerun the command

### 85 create complex patterns by iterating upon search history

Change the single quotes to double quotes.

```
This string contains a "quoted" word.
This string contains "two" quoted "words".
This "string doesn't make things easy".
```

`/\v".+"` - will match everything in single quote, quote included
`/<Up>` - Use search history get this search string back
`/\v"[^"]+` - this will be better, but not perfect
Use search history again
`/\v"([^"]|"\w])+"` - this should be an even better match
`q/` - let's use the search command-line window
Find this search: `/\v"[^"]+` - to edit
`f[` - jump to the first square bracket
`c%(<C-r>")<Esc>` - cut and paste + insert parens
`i|'\w<Esc>` - inserts the remaining search

We want to capture everything in the quotes, wrap it in parens
`/\v'(([^']|'\w)+)'` - this is perfect
`:%s//'\1'/g` - replace double quotes with single quotes by using a %1 capture register
