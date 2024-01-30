 # Lab 1
## Command 1 (cd)
**No Argument**
```
[user@sahara ~]$ cd
[user@sahara ~]$ 
```
The working directory was the root directory `/home`. When we put in no argument, the `cd` command 
returns back to the home directory. This is not an error as `cd` as a command's purpose is to change
the working directory so a natural default operation would be returning to the home directory.

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
a directory as an argument.

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
```
[user@sahara ~/lecture1]$ cat
test
test
 
 
hi
hi
[user@sahara ~/lecture1]$
```
The working directory was `/home/lecture1`. When we do not pass an argument into `cat`, the
the terminal begins accepting text into the standard input and reprints what was inputted
by the user. It seems like when no argument is passed into `cat`, the command begins 
concatenating what the user inputs to nothing, which is why it reprints the text recieved in
the standard input. I do not think this is an error.

**Directory Argument**
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
[user@sahara ~/lecture1]$
```
The working directory was `/home/lecture1`. When provided with a directory argument, `cat`
outputs the name of the directory and specifies it as a directory. This is an error as `cat` is
used for reading and concatenating contents of a file, not of a directory.

**File Argument**
```
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}[user@sahara ~/lecture1]$
```
The working directory was `/home/lecture1`. When provided with a file argument, `cat`
outputs the contents of the file. In this case, I inputted `Hello.java` as an argument
and the command printed the text contained in the file. This is not an error.









