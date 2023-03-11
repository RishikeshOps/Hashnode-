---
title: "Basic Linux Commands | All in One Linux Commands Cheetsheet |"
seoTitle: "linux commands"
seoDescription: "basic linux commands. beginner linux cheetsheet."
datePublished: Tue Nov 01 2022 06:57:46 GMT+0000 (Coordinated Universal Time)
cuid: cl9xuyg98001909jjhrhxdvhv
slug: basic-linux-commands-all-in-one-linux-commands-cheetsheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1667285559713/BmlzsYsnG.png
tags: linux, commands, linux-for-beginners, linux-basics, linux-commands

---

**\# Create Directory**

1. For creating a single directory `#mkdir /Tiger`
    
2. For creating multiple directories `#mkdir Lion Elephant Wolf`
    
3. To create a directory path (directory inside the directory) `#mkdir -p /red/pink/yellow/black`
    
4. For creating a number of directories `#mkdir /student{1..10}`
    

**\# For Create File**

**Touch:**

The touch command is used for creating an empty file, we can’t write data in a file, can’t edit or save a file.

1. Create a single file with the touch command `#touch notes`
    
2. Create multiple files `#touch physics chemistry math`
    
3. 3\. Create a number of files `#touch books{1..10}`
    

**\# Create File With cat Command**

Cat command is used for creating files, adding data in files, read files, we can also append files but we can't edit files.

**Syntax of cat command** `#cat <option> <file name>`

1. To create and write file `#cat > demo.txt`
    
2. For reading file #`cat < demo.txt`
    
3. For Append file `#cat >> demo.txt` *Ctrl+d is used for writing and quitting files (save & exit)*
    

**\# For Remove File and Directory**

rm: rm command is used for delete files or directory Syntax: `#rm <option> <destination>` **Options**

\-r for recursive

\-v for verbose

\-f for forcefully

1. For deleting files or directory `#rm -rvf /india/pune`
    
2. To delete a File or Directory which starts from the D alphabet `#rm -rvf /india/D*`
    
3. To delete all databases of the current directory `#pwd #rm -rvf *`
    

**\# For Copy and Paste**

\*\*cp: \*\*

cp command is used for copying and pasting files or directories Syntax: `#cp <option> <source> <destination>` \*\*Options: \*\* -r for recursive

\-v for verbose

\-f for forcefully

1. For copy file `#cp -rvf /root/demo.txt /home`
    
2. To copy all data which start from the D alphabet `#cp -rvf /root/D* /home`
    

\*\*# For moving or Rename File And Directory \*\*

**mv :**

mv stands for a move, mv command is used to move one or more files or directories from one place to another. It is also used for renaming files or directories.

**Syntax:** `#mv <source > <destination>`

1. To move files or directory `#mv /home/demo /root/Desktop`
    
2. For renaming files or directory `#mv Tiger Tigers`
    

# **Basic Commands**

```plaintext
/ is your root directory 
~ is your home directory

1. pwd       : it show present working directory
2. ls        : it show available files and directory list in present working directory.
3. uname     : it show name of kernel (OS)
4. uname -r  : it show version of kernel 
5. cd        : it use for change directory
6. clear     : it use for clear screen
7. whoami    : it show currently login user name
8. history   : it show list of previously used commands
9. date      : it show time and date
10. users    : Display the username of all users currently logged on the system
11. Clear    : Clear Screen
12. lastlog  : The lastlog command is used to find the details of a recent login of all users
13. Tail     : This command prints the last N number of data of the given input. By default, it prints 10 lines. 
14. Chmod    : This command is used to change the access permissions of files and directories.
15. Chown    : This command is used to change the file Owner or group.
16. Cut      : This command is used to extract specific fields or columns from a file or standard input.
```

\*\*5 ways to become a sudo user in Linux OS \*\* `(1) sudo -i (2) sudo -s (3) sudo su - (4) su -root (5) su -`

\*\*# For Installing Packages \*\*

1. Install the package with help of the yum command which will look like
    

```plaintext
  yum install package_name
```

1. To display brief detail about a package `yum info package_name`
    
2. To remove the package `yum remove package_name`
    
3. Installing a package from a local file  
    `./filename`
    

> Thanks For Reading! :)

> \-Rushikesh Mashidkar