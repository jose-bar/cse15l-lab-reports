# **Lab Report 1**

## 1. **cd:** "Change Directory"
a) Using the command with no arguments:
```
[user@sahara ~]$ cd
[user@sahara ~]$
```

> Working directory: `/home` 

> Having no arguments meant we did not specify a directory to change to. This would change us to the home directory which is the one we were already on.

> The output is not an error

b) Using the command with a path to a directory as an argument:
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```

> Working directory: `/home`

> Specifying a directory meant that our user prompt change to reflect that our current directory had changed.

> The output is not an error

c) Using the command with a path to a file as an argument:
```
[user@sahara ~/lecture1]$ cd README
bash: cd: README: Not a directory
```

> Working directory: `/home/lecture1`

> The command recognizes that the argument is not a directory and therefore notifies the user of this.

> The output is an error, the `cd` command is meant to only take in directories as arguments



## 2. **ls:** "List"
a) Using the command with no arguments:
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  **messages**  README
```

> Working directory: `home/lecture1` 

> Having no arguments meant it outputs the available files and directories from our current directory. Directories are highlighted a different color to show that distinction.

> The output is not an error

b) Using the command with a path to a directory as an argument:
```
[user@sahara ~/lecture1]$ ls messages
af.txt  en-us.txt  es-mx.txt  zh-cn.txt
```

> Working directory: `/home/lecture1`

> The output reads the list of files from the directory path that we passed as an argument. It states that the directory `messages` has those files within it.

> The output is not an error

c) Using the command with a path to a file as an argument:
```
[user@sahara ~/lecture1]$ ls README
README
```

> Working directory: `/home/lecture1`

> The command displays the name of the file passed as an argument.

> The output is not an error. (Although I do not know the practicality of it)
   
## 3. **cat:** "Concatenate"
a) Using the command with no arguments:
```
[user@sahara ~/lecture1]$ cat
```

> Working directory: `home/lecture1`

> Entering `cat` with no arguments will put the terminal in a state where all text inputs will be spat out as outputs. To exit this state enter `[CTRL] + [C]`

> The output is not an error

b) Using the command with a path to a directory as an argument:
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```

> Working directory: `/home/lecture1`

> Since `cat` is used to read the outputs of files, it cannot read an argument that is a directory. It lets the user know that the argument was a directory.

> The output is an error as `cat` takes in file paths not directories for its argument.

c) Using the command with a path to a file as an argument:
```
[user@sahara ~/lecture1/messages]$ cat af.txt
Hello Wêreld!
```
```
[user@sahara ~/lecture1/messages]$ cat af.txt en-us.txt
Hello Wêreld!
Hello World!
```

> Working directory: `/home/lecture1/messages`

> The command displays the text "Hello World!" in African. This is the content of the `af.txt` file and thus the output of `cat`. Adding another file name prints out the contexts subsequently

> The output is not an error.
