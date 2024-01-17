# lesson 1
`pwd` present working directory  
`cd` change directory  
`.` current directory  
`..` father directory  
`ls` list  
`~` home directory  
`cd -` back to last directory  
`ls -l` use a long listing format  
## info
```bash
# drwxr-xr-x    5 yangchenghao1  staff   160B 11 16  2021 PycharmProjects/
drwxr-xr-x # d means directory
r # read 
w # write 
x # execute
drwxr-xr-x # group 1 first 3 characters for user/owner
drwxr-xr-x # group 2 second 3 characters for group owner
drwxr-xr-x # group 3 third 3 characters for others
```
`mv` move, can also use to rename files  
`cp` copy  
`rm` remove
`rm -r` recursive remove  
`rmdir` remove **empty** directory  
`mkdir` make directory, **caution** when mkdir, you can not do `mkdir my photo`, that will make 2 directory, you should use `mkdir "my photo"` or `mkdir my\ photo`  
`man` manual, like `man ls`can give you info about `ls`  
`C+l` can clear and back to top  
`< file` rewire the input as the file  
`> file` rewire the output as the file  
`cat` print contents of a file, also can use to copy file, like `cat < a > b`  
`>>` append, `cat < a >> b` will not overwrite but append  
pipe `|` left is input for right  
`tail` print last n lines `tail -n1` print last line  
`sudo` super user do  
## Tip1
when i try to change brightness use `sudo echo 500 > brightness` will be permission denied, because its a **stream**, shell do the **write** operation with `sudo`, but shell **open** the file without `sudo`, you can use `sudu su` to get a super user shell, or you can use `echo 500 | sudo tee brightness`  
`tee -` duplicate standard input, can write input into file and screen
## Tip2
```bash
chmod +x file # add execute permission
chmod u/g/o+x # add execute permission to user/group/others
chmod -x file # delete execute permission
```