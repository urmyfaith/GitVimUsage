# usage of vi/vim under windows:

## move line

* up --> k

* down -->j

* left -->h

* right -->l

* linehead-->0

* noneBlankLineHead--> shift+^

* linetail-->shift+$

* up one line --> ctrl +e

* down one line --> ctrl +y

* to N line ---> :n    or-->nG

----

## move word

* word before  start--->w

* 				end --->e

* word after after -->b

* 				end --> ge

* to somechar  left-->Tx

* 				right--->fx

---

## move sentence 

* to start --> (

* to end --> )

---
## move paragraph

* to start {

* to end }

---
## move doc

*head --> gg
*end ---> G
*parecent -->50%

----

## screen move

* up a screen --> ctrl +b

* **up half a acreen ---> ctrl + d**

* down a screen ---> ctrl+f

* **down half a screen --> ctrl +u**

* to screen high -->H    3H

* to sreen middle --> M

* to screen low --> L 5L

* zt  --> cursor to screen top 

* zz --> cursor to screen middle

* zb --> cursor to screen buttom

----

## insert 

* i --> befor cursor 
* a --> after cursor
* A --> line end insert
* o ---> next line
* O ---> up line insert

---

## delete

* x --> delete cursor

* X --> befor cursor

* dw --> delete word

* dd --> delete line

* ndd --> delete N lines

* d0 --> delete to line start

* d^ -->			line start

* D ---> delete to line end

* d$ --> 			line end

* dG ---> delete to document end

* dgg ----> delete teo document start

* :g/^\n*$/ d ---> delete blank line

----
## copy

* yy --> copy current line.
* 2yy --> copy two lines
* y^ --> copy to line start
* y$ --> copy to line end
* yw --> copy one word.
* y2w --> copy two words
* yG ---> copy to  doc end
* y1G ---> copy to doc start
* p --> paste to after cursor 
* P --> paste to befor cursor 

## search

* /string  ---->search the stirng...

* ? ----> search upside.

* q/ ---> search resulte set

* q? ---> search reslute set .

----

![vi summary](https://raw.githubusercontent.com/urmyfaith/GitVimUsage/master/vi.png "")

