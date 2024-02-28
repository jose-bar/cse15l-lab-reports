
# **Lab Report 4**

## Step 4: Log into ieng6

> Keys Pressed: `s s h <space> j b a r c e l o g a r c i a @ i e n g 6 . u c s d . e d u <enter>`

![Image](ssh.png)

I ran the `ssh` command which allows me to connect my device to the ieng6 server. You specify the server after the `@` key and you specify the user before the `@`. 

## Step 5: Clone your fork of the repository from your Github account (using the SSH URL)

> Keys Pressed: `g i t <space> c l o n e <space> <ctrl> v <enter> l s <enter>`

![Image](cloneSSH.png)

I ran the `git clone` commands which makes a copy of the specified git resposatory in a new directory. I specified the `ssh` key git@github.com:jose-bar/lab7.git using `ctrl` + `v` to paste the link from my clipboard. Using the ssh key allows me to push changes to the git repository later on. After entering that command, I enter the `ls` command to list my files and directories to make sure the repository was correctly cloned.

## Step 6: Run the tests, demonstrating that they fail

>Keys Pressed: `c d <space> l a b 7 <enter> b a s h <space> t e s t . s h`

![Image](test.png)

I ran the `cd` command to switch into the `lab7/` directory. From this directory, I entered `bash test.sh` which runs a shell script using bash. This script is within `lab7/` and essentially compiles and runs the JUnit tests for me.
