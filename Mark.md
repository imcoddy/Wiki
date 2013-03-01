This script is written to highlight several words in different colors simultaneously. For example, when you are browsing a big program file, you could highlight some key variables. This will make it easier to trace the source code.

I now have not much interest in upgrading Mark. It is just OK for my daily use. But I found Ingo Karkat has some further development on it and I am sure you will be interest to check it out, it's really a good job:
http://www.vim.org/scripts/script.php?script_id=2666

Usage:

Highlighting:
  Normal mode:
    \m mark or unmark the word under (or before) the cursor
          Place the cursor under the word to be highlighted, press \m, then the word will be colored.
    \r manually input a regular expression
          To highlight an arbitrary regular expression, press \r and input the regexp.
    \n clear this mark (i.e. the mark under the cursor), or clear all highlighted marks
  Visual mode:
    \m mark or unmark a visual selection
          Select some text in Visual mode, press \m, then the selection will be colored.
    \r manually input a regular expression (base on the selection text)
  Command line:
    :Mark regexp   to mark a regular expression
    :Mark regexp   with exactly the same regexp to unmark it
    :Mark          to clear all marks
Searching:
  Normal mode:
    * # \* \# \/ \? use these six keys to jump to the other marks
    and you could also use VIM's / and ? to search, since the mark patterns have
    been added to the search history.

Here is a sumerization of * # \* \# \/ \?:

" First of all, \#, \? and # behave just like \*, \/ and *, respectively,
" except that \#, \? and # search backward.
"
" \*, \/ and *'s behaviors differ base on whether the cursor is currently
" placed over an active mark:
"
"       Cursor over mark                  Cursor not over mark
" ---------------------------------------------------------------------------
"  \*   jump to the next occurrence of      jump to the next occurrence of
"       current mark, and remember it       "last mark".
"       as "last mark".
"
"  \/   jump to the next occurrence of        same as left
"       ANY mark.
"
"   *   if \* is the most recently used,        do VIM's original *
"       do a \*; otherwise (\/ is the
"       most recently used), do a \/.

Screenshot:
http://elephant.net.cn/files/vim_screenshot.png (It is also the screenshot of my colorscheme vimscript #1253.)

Bugs and Notes:
Some words which have been already colored by syntax scripts could not be highlighted.

mark.vim should be re-sourced after any changing to colors. For example, if you
:set background=dark  OR
:colorscheme default
you should
:source PATH_OF_PLUGINS/mark.vim
after that. Otherwise, you won't see the colors.
Unfortunately, it seems that .gvimrc runs after plugin scripts. So if you set any color settings in .gvimrc, you have to add one line to the end of .gvimrc to source mark.vim.