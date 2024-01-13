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

---
## Command 2 (ls)
**No Argument**
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ 
```
The working directory was `/home/lecture1`. When we do not input an argument, `ls` outputs
all items in the working directory, which includes the files `Hello.class`, `Hello.java`, and 
`README` along with the directory `messages`. This is not an error.

**Directory Argument**
```
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  zh-cn.txt
[user@sahara ~/lecture1]$
```
The working directory was `/home/lecture1`. When we input a directory argument, `ls` outputs
all items within the specified directory, which is the intended output as `ls` is supposed to
output all items that are in the directory. This is not an error.

**File Argument**
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
[user@sahara ~/lecture1]$
```
The working directory was `/home/lecture1`. When we pass a file into the argument of `ls`, 
the command outputs the name of the file, which is expected as the only file at specified
path is the file that was passed as an argument. This is not an error.

---
## Command 3 (cat)
**No Argument**










