# Lab 1
## Command 1 (cd)
**No Argument**
```
[user@sahara ~]$ cd
[user@sahara ~]$ 
```
The working directory was the root directory `/home`. When we put in no argument, the `cd` command 
does not change the current directory. This is not an error as the computer needs to know what
directory to change to and if the user does not input a specified path, the computer should not
change the directory.

**Directory Argument**
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
The working directory was `/home`. When specified a directory, `cd` changes the working directory 
to the specified directory, which in this case was `lecture1`. This does not produce an output.
This is not an error as `cd` should not be generating an output as we are only changing the
working directory.

**File Argument**
```
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$
```
The working directory was `/home/lecture1`. When given a file as an argument, `cd` outputs an error
saying the input is not a directory. This makes sense as a file and directory are not the same so
`cd` should fail. This is an error because the specified input is a file when `cd` only takes 
directories as an argument.
