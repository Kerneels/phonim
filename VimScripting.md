# Introduction #

In order to communicate with our Java code, Vim sends messages over the Netbeans protocol.

We achieve this communication with a combination of simple key-mappings and event-driven scripting.

Info on events: http://vimdoc.sourceforge.net/htmldoc/autocmd.html#autocommand

Netbeans Protocol:
http://vimhelp.appspot.com/netbeans.txt.html#netbeans.txt

# Details #


_Note:_  There appear to be no events triggered by movement in visual mode.

**Events**
`CursorMoved`  Triggered when the cursor moves in normal mode. ALSO triggered when text is added or removed ON the cursor's line in normal mode, ala "p"/"x" etc.

`CursorMovedI`  Text inserted in normal mode.

`InsertEnter`

`InsertLeave`


**Mapping**
To come

**Functions**

_Built-in Variables:_

(v:  means global to vim)

v:insertmode -- is Vim in insert mode?

v:operator --- last operator (p,d,y etc.) used in normal mode

v:errmsg   -- last error message

v:statusmsg -- las stat message

v:warningmsg

_Built-in Functions_

`getline()`   called as `getline(".")`

`col()`

_Example Functions_

Below are some simple examples of how this might work.
Mostly, they give an idea of the Vim sytax. We can use "nbkey {args...}"
to communicate with our java code. For example, we already have a "nbkey speak {arg}" command.

```
function! SpeakWord(word)
   execute 'nbkey speak ' . a:word
endfunction


function! GetWord()
   let temp9 = @9
   normal "9yw
   let currentWord = @9 
   let @9 = temp9

" resets the contents of the register to be the old contents of that regiser.

   return currentWord
endfunction

```