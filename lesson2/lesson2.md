# lesson2
## Tips
`!!` can replace to last command  
`echo $?` return 0 means everything went fine, no errors
`||` if left false then run right
```bash
false || echo "Oops fail" # return Oops fail
true || echo "Will be not be printed" # return nothing
```
`&&`if left true then run right
```bash
true && echo "Things went well" # return Things went well
false && echo "This will not print" # return nothing
```
`;` concat result
```bash
false;echo "This will always print" # return This will always print
```
```bash
foo=$(pwd) # get what pwd output to foo variable
```
```bash
#!/bin/bash

echo "Starting program at $(date)"
# $0 means current file
# $# counts the number of arguments
# $$ get current pid
echo "Running program $0 with $# arguments with pid $$"
# $@ means $1 $2 $3, any other
for file in "$@"; do
    grep foobar "$file" > /dev/null 2> /dev/null
    # it will have 2 result, 0 and 1
    # -ne not equal
    if [["$?" -ne 0]]; then
        echo "File $file does not have any foobar, adding one"
        echo "# foobar: >> :$file"
    fi
done
```
## globing
1. `ls *.sh` get all .sh files  
2. `ls project?` `?` will expand to anyone character  
3. `convert image.png image.jpg` equals to `convert image.{png,jpg}`  
4. `touch foo{,1,2,10}` equals to `touch foo foo1 foo2 foo10`
`touch project{1,2}/src/test/test{1,2,3}.py` will do the Cartesian product to `touch project1/src/test/test1.py project1/src/test/test2.py project1/src/test/test3.py project2/src/test/test1.py project2/src/test/test2.py project2/src/test/test3.py`  
5. `touch {foo,bar}{a..j}` will also do the Cartesian to `touch foo/a foo/b ... bar/i bar/j`  
6. compare 2 directories `diff < (ls foo) < (ls bar)`  
## with python
```python
#!/usr/local/bin/python 
# when you want to run this in shell, you have to let shell to know it has use python as the interpreter
#!/usr/bin/env python
import sys
for arg in reversed(sys.argv[1:]):
    print(arg)
```
## tldr
`tldr` give some examples to a shell word  
`tldr ffmpeg` give some convert example for pictures and videos  
## find files
`find . -name src -type d` find in current directory, name is src, type is directory  
`find . -path '**/test/*.py' -type f` find in current directory, from test directory, `.py` python files  
`find . -mtime -1` find files modified time is last day  
`find . -name "*.tmp" -exec rm {} \;` find all `.tmp` files and remove  
`fd ".*py"` find all `.py` files
## locate
`updatedb` update locate database  
`locate missing-semester` find all files which have missing-semester directory location
## grep
`grep foobar mcd.sh` find string foobar in mcd.sh  
`grep -R foobsr .` find files have foobar in current directory  
`rg "import requests" -t py ~/scratch` quick find python files import requests in scratch directory, **rg=riggrep**  
`rg "import requests" -t py -C 5 ~/scratch` get 5 lines before and after your finding result  
`rg -u --files-without-match "^#\!" -t sh` `-u` means ignore hiding files, find files do not have some words 
`rg "import requests" -t py -C 5 --stats ~/scratch` get all info about this search
## History command
`history` will print commands  
`history 1 | grep convert` find history commands with `convert`  
`C+r` key words to find command, keep using and find more command with key words
## fzf
fuzzy finder  
`cat a | fzf` can use fzf to find words dynamically
## Tips
`-R` recursively list directory structure, like `ls -R`, but `tree` is more friendly  
`broot` can do some thing, can search key files  
`nnn` use navigation arrows to quick explore and open files