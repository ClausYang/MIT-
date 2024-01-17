# Exercises
1. Create a new directory called `missing` under `/tmp`.  
`cd /tmp`  
`mkdir semester`
2. Use `touch` to create a new file called `semester` in `missing`.
`touch missing`
3. Write the following into that file, one line at a time:
    ```bash
    #!/bin/sh
    curl --head --silent https://missing.csail.mit.edu
    ```
    `echo "#!/bin/sh" > semester`  
    `echo "curl --head --silent https://missing.csail.mit.edu" >> semester`  

4. Try to execute the file, i.e. type the path to the script (`./semester`) into your shell and press enter. Understand why it doesn’t work by consulting the output of `ls` (hint: look at the permission bits of the file).  
because it does not have executer permission, should use `chmod` to give.
5. Use `chmod` to make it possible to run the command `./semester` rather than having to type `sh semester`  
`chmod +x semester`
6. Use `|` and `>` to write the “last modified” date output by `semester` into a file called `last-modified.txt` in your home directory.  
`./semester | grep last-modified > last-modified.txt`