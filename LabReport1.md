# **Lab Report 1**

## **CD:** "Change Directory"
1. Using the command with no arguments:
```
[user@sahara ~]$ cd
[user@sahara ~]$
```
> Working directory: /home 

> Having no arguments meant we did not specify a directory to change to. This would change us to the home directory which is the one we were already on.

> The output is not an error

2. Using the command with a path to a directory as an argument:
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
> Working directory: /home

> Specifying a directory meant that our user prompt change to reflect that our current directory had changed.

> The output is not an error

3. Using the command with a path to a file as an argument:
```
[user@sahara ~/lecture1]$ cd README
bash: cd: README: Not a directory
```
> Working directory: /home/lecture1

> The command recognizes that the argument is not a directory and therefore notifies the user of this.

> The output is an error, the ***cd*** command is meant to only take in directories as arguments



## **ls:** "List"
1. Using the command with no arguments:
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  **messages**  README
```
> Working directory: home/lecture1 

> Having no arguments meant it outputs the available files and directories from our current directory. Directories are highlighted a different color to show that distinction.

> The output is not an error

2. Using the command with a path to a directory as an argument:
```
[user@sahara ~/lecture1]$ ls messages
af.txt  en-us.txt  es-mx.txt  zh-cn.txt
```
> Working directory: /home/lecture1

> The output reads the list of files from the directory path that we passed as an argument. It states that the directory **messages** has those files within it.

> The output is not an error

3. Using the command with a path to a file as an argument:
```
[user@sahara ~/lecture1]$ ls README
README
```
> Working directory: /home/lecture1

> The command displays the name of the file passed as an argument.

> The output is not an error. (Although I do not know the practicality of it)
   
