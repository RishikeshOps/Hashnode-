---
title: "Bash Scripting: A Simple and Effective Way to Boost Your Productivity"
seoTitle: "Exploring the Capabilities of Bash: A Guide for the Curious"
seoDescription: "Bash: The Key to Streamlining Your Workflow on a Computer"
datePublished: Wed Feb 01 2023 20:01:12 GMT+0000 (Coordinated Universal Time)
cuid: cldm3gbbg00010amm5npmf5zm
slug: bash-scripting-a-simple-and-effective-way-to-boost-your-productivity
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675280805756/0c47e86b-4cb4-4710-a311-e179def8f0d2.png
tags: linux, bash, devops, ineuron, 90daysofdevops

---

# Bash: The Key to Streamlining Your Workflow on a Computer

Bash is a type of software that allows you to interact with your computer using text commands. Think of it like a more advanced version of the Command Prompt on Windows or Terminal on Mac. With Bash, you can perform all sorts of tasks, such as copying and moving files, starting and stopping programs, and even automating repetitive tasks.

Bash is an acronym for **Bourne-Again Shell**, and it is the default shell on many Linux and macOS systems. It is also available on many other operating systems, including Windows, through the Windows Subsystem for Linux (WSL).

Bash scripts are like recipes for your computer. They contain a list of instructions that Bash can follow to accomplish a specific task. For example, you can write a script to back-up your important files or deploy a new version of a software program. These scripts can be saved and run whenever you need them, which saves you time and effort compared to manually performing these tasks.

Bash is commonly used by professionals who manage computer systems and networks, such as system administrators and DevOps engineers. However, it can also be useful for anyone who wants to automate tasks and streamline their work on a computer.

# Let's Get Crackin' with Bash Scripting

```bash
#!/bin/bash
- First line of the script is the shebang which tells the system how to execute
- As you already figured, comments start with #. Shebang is also a comment.

# Simple hello world example:
echo Hello world! # => Hello world!

# Each command starts on a new line, or after a semicolon:
echo 'This is the first line'; echo 'This is the second line'
 => This is the first line
 => This is the second line
-----------------------------------------------------------------------------
# Declaring a variable looks like this:
Variable="Some string"

# But not like this:
Variable = "Some string" # => returns error "Variable: command not found"
# Bash will decide that Variable is a command it must execute and give an error
# because it can't be found.

# Nor like this:
Variable= 'Some string' # => returns error: "Some string: command not found"
# Bash will decide that 'Some string' is a command it must execute and give an
# error because it can't be found. (In this case the 'Variable=' part is seen
# as a variable assignment valid only for the scope of the 'Some string'
# command.)

# Using the variable:
echo $Variable # => Some string
echo "$Variable" # => Some string
echo '$Variable' # => $Variable
# When you use the variable itself — assign it, export it, or else — you write
# its name without $. If you want to use the variable's value, you should use $.
# Note that ' (single quote) won't expand the variables!

# Parameter expansion ${ }:
echo ${Variable} # => Some string
# This is a simple usage of parameter expansion
# Parameter Expansion gets a value from a variable.
# It "expands" or prints the value
# During the expansion time the value or parameter can be modified
# Below are other modifications that add onto this expansion

# String substitution in variables
echo ${Variable/Some/A} # => A string
# This will substitute the first occurrence of "Some" with "A"

# Substring from a variable
Length=7
echo ${Variable:0:Length} # => Some st
# This will return only the first 7 characters of the value
echo ${Variable: -5} # => tring
# This will return the last 5 characters (note the space before -5)

# String length
echo ${#Variable} # => 11

# Indirect expansion
OtherVariable="Variable"
echo ${!OtherVariable} # => Some String
# This will expand the value of OtherVariable
-----------------------------------------------------------------------------
# Declare an array with 5 elements
my_array=(one two three four five)
# Print first element
echo $my_array # => "one"
# Print first element
echo ${my_array[0]} # => "one"
# Print all elements
echo ${my_array[@]} # => "one two three four five"
# Print number of elements
echo ${#my_array[@]} # => "5"
# Print number of characters in third element
echo ${#my_array[2]} # => "5"
# Print 2 elements starting from fourth
echo ${my_array[@]:3:2} # => "four five"
# Print all elements. Each of them on new line.
for i in "${my_array[@]}"; do
    echo "$i"
done
-----------------------------------------------------------------------------
# Brace Expansion { }
# Used to generate arbitrary strings
echo {1..10} # => 1 2 3 4 5 6 7 8 9 10
echo {a..z} # => a b c d e f g h i j k l m n o p q r s t u v w x y z
# This will output the range from the start value to the end value
-----------------------------------------------------------------------------
# Built-in variables:
# There are some useful built-in variables, like
echo "Last program's return value: $?"
echo "Script's PID: $$"
echo "Number of arguments passed to script: $#"
echo "All arguments passed to script: $@"
echo "Script's arguments separated into different variables: $1 $2..."
-----------------------------------------------------------------------------
# Now that we know how to echo and use variables,
# let's learn some of the other basics of bash!

# Our current directory is available through the command `pwd`.
# `pwd` stands for "print working directory".
# We can also use the built-in variable `$PWD`.
# Observe that the following are equivalent:
echo "I'm in $(pwd)" # execs `pwd` and interpolates output
echo "I'm in $PWD" # interpolates the variable

# If you get too much output in your terminal, or from a script, the command
# `clear` clears your screen
clear
# Ctrl-L also works for clearing output
-----------------------------------------------------------------------------
# Reading a value from input:
echo "What's your name?"
read Name # Note that we didn't need to declare a new variable
echo Hello, $Name!

# We have the usual if structure:
# use `man test` for more info about conditionals
if [ $Name != $USER ]
then
    echo "Your name isn't your username"
else
    echo "Your name is your username"
fi
# True if the value of $Name is not equal to the current user's login username

# NOTE: if $Name is empty, bash sees the above condition as:
if [ != $USER ]
# which is invalid syntax
# so the "safe" way to use potentially empty variables in bash is:
if [ "$Name" != $USER ] ...
# which, when $Name is empty, is seen by bash as:
if [ "" != $USER ] ...
# which works as expected
-----------------------------------------------------------------------------
# There is also conditional execution
echo "Always executed" || echo "Only executed if first command fails"
# => Always executed
echo "Always executed" && echo "Only executed if first command does NOT fail"
# => Always executed
# => Only executed if first command does NOT fail
-----------------------------------------------------------------------------
# A single ampersand & after a command runs it in the background. A background command's
# output is printed to the terminal, but it cannot read from the input.
sleep 30 &
# List background jobs
jobs # => [1]+  Running                 sleep 30 &
# Bring the background job to the foreground
fg
# Ctrl-C to kill the process, or Ctrl-Z to pause it
# Resume a background process after it has been paused with Ctrl-Z
bg
# Kill job number 2
kill %2
# %1, %2, etc. can be used for fg and bg as well
-----------------------------------------------------------------------------
# To use && and || with if statements, you need multiple pairs of square brackets:
if [ "$Name" == "Rishi" ] && [ "$Age" -eq 23 ]
then
    echo "This will run if $Name is Rishi AND $Age is 23."
fi

if [ "$Name" == "EC2" ] || [ "$Name" == "Varsha" ]
then
    echo "This will run if $Name is EC2 OR Varsha." #😁😉
fi

# There is also the `=~` operator, which tests a string against a Regex pattern:
Email=demo12@example.com
if [[ "$Email" =~ [a-z]+@[a-z]{2,}\.(com|net|org) ]]
then
    echo "Valid email!"
fi
# Note that =~ only works within double [[ ]] square brackets,
# which are subtly different from single [ ].
# See https://www.gnu.org/software/bash/manual/bashref.html#Conditional-Constructs for more on this.
-----------------------------------------------------------------------------
# Redefine command `ping` as alias to send only 5 packets
alias ping='ping -c 5'
# Escape the alias and use command with this name instead
\ping 192.168.1.1
# Print all aliases
alias -p

# Expressions are denoted with the following format:
echo $(( 10 + 5 )) # => 15

# Unlike other programming languages, bash is a shell so it works in the context
# of a current directory. You can list files and directories in the current
# directory with the ls command:
ls # Lists the files and subdirectories contained in the current directory

# This command has options that control its execution:
ls -l # Lists every file and directory on a separate line
ls -t # Sorts the directory contents by last-modified date (descending)
ls -R # Recursively `ls` this directory and all of its subdirectories

# Results (stdout) of the previous command can be passed as input (stdin) to the next command
# using a pipe |. Commands chained in this way are called a "pipeline", and are run concurrently.
# The `grep` command filters the input with provided patterns.
# That's how we can list .txt files in the current directory:
ls -l | grep "\.txt"

# Use `cat` to print files to stdout:
cat file.txt

# We can also read the file using `cat`:
Contents=$(cat file.txt)
# "\n" prints a new line character
# "-e" to interpret the newline escape characters as escape characters
echo -e "START OF FILE\n$Contents\nEND OF FILE"
# => START OF FILE
# => [contents of file.txt]
# => END OF FILE
-----------------------------------------------------------------------------
# Use `cp` to copy files or directories from one place to another.
# `cp` creates new versions of the sources,
# so editing the copy won't affect the original (and vice versa).
# Note that it will overwrite the destination if it already exists.
cp srcFile.txt clone.txt
cp -r srcDirectory/ dest/ # -r = recursively copy
-----------------------------------------------------------------------------
# Use `mv` to move files or directories from one place to another.
# `mv` is similar to `cp`, but it deletes the source.
# `mv` is also useful for renaming files!
mv sourc.txt dest.txt 
-----------------------------------------------------------------------------
# Since bash works in the context of a current directory, you might want to
# run your command in some other directory. We have cd for changing location:
cd ~    # change to home directory
cd      # also goes to home directory
cd ..   # go up one directory
        # (let say, from /home/username/Downloads to /home/username)
cd /home/username/Documents   # change to specified directory
cd ~/Documents/..    # now in home directory (if ~/Documents exists)
cd -    # change to last directory
# => /home/username/Documents

# Use subshells to work across directories
(echo "First, I'm here: $PWD") && (cd someDir; echo "Then, I'm here: $PWD")
pwd # still in first directory
-----------------------------------------------------------------------------
# Bash uses a `case` statement that works similarly to switch in Java and C++:
case "$Variable" in
    # List patterns for the conditions you want to meet
    0) echo "There is a zero.";;
    1) echo "There is a one.";;
    *) echo "It is not null.";;  # match everything
esac
-----------------------------------------------------------------------------
# `for` loops iterate for as many arguments given:
# The contents of $Variable is printed three times.
for Variable in {1..3}
do
    echo "$Variable"
done
# => 1
# => 2
# => 3


# Or write it the "traditional for loop" way:
for ((a=1; a <= 3; a++))
do
    echo $a
done
# => 1
# => 2
# => 3

# They can also be used to act on files..
# This will run the command `cat` on file1 and file2
for Variable in file1 file2
do
    cat "$Variable"
done

# ..or the output from a command
# This will `cat` the output from `ls`.
for Output in $(ls)
do
    cat "$Output"
done

# Bash can also accept patterns, like this to `cat`
# all the txt files in current directory
for Output in ./*.txt
do
    cat "$Output"
done
-----------------------------------------------------------------------------
# while loop:
while [ true ]
do
    echo "loop body here..."
    break
done
# => loop body here...
-----------------------------------------------------------------------------
# There are a lot of useful commands you should learn:
# prints last 10 lines of file.txt
tail -n 10 file.txt

# prints first 10 lines of file.txt
head -n 10 file.txt

# print file.txt's lines in sorted order
sort file.txt

# report or omit repeated lines, with -d it reports them
uniq -d file.txt

# prints only the first column before the ',' character
cut -d ',' -f 1 file.txt

# replaces every occurrence of 'okay' with 'great' in file.txt
# (regex compatible)
sed -i 's/okay/great/g' file.txt
# be aware that this -i flag means that file.txt will be changed
# -i or --in-place erase the input file (use --in-place=.backup to keep a back-up)

# The `trap` command allows you to execute a command whenever your script
# receives a signal. Here, `trap` will execute `rm` if it receives any of the
# three listed signals.
trap "rm $TEMP_FILE; exit" SIGHUP SIGINT SIGTERM
-----------------------------------------------------------------------------
# Read Bash shell built-ins documentation with the bash `help` built-in:
help
help help
help for
help return
help source
help .

# Read Bash manpage documentation with `man`
apropos bash
man 1 bash
man bash

# Read info documentation with `info` (`?` for help)
apropos info | grep '^info.*('
man info
info info
info 5 info

# Read bash info documentation:
info bash
info bash 'Bash Features'
info bash 6
info --apropos bash
```

# Two Bash Scripts that DevOps Engineer Mostly Uses

## 1\. Backup Script

A script is written in a computer language called "Bash" which helps in automatically making copies of important files and databases. This script helps to make sure that important information is not lost if something goes wrong with the original files or databases. The script can use different tools to make compressed copies of the information and send it to a safe storage location. i.e backup.sh

```bash
#!/bin/bash

# Define the location of the files to be backed up
source_dir="/path/to/important/files"

# Define the location for the backup files
destination_dir="/path/to/backup/location"

# Define a timestamp for the backup files
timestamp=$(date +"%Y-%m-%d_%H-%M-%S")

# Create the backup archive
tar -czf "$destination_dir/$timestamp.tar.gz" "$source_dir"

# Check if the backup was successful
if [ $? -eq 0 ]; then
  echo "Backup successful!"
else
  echo "Backup failed!"
fi
```

## 2\. Deployment Script

A script that automatically updates a live website or application. This script helps to ensure that changes made to the code, such as bug fixes or new features, are quickly and easily sent to the live environment. The script can retrieve the latest code from a version control system, build it, and make updates to the servers that are running the live environment.

```bash
#!/bin/bash

# Define the location of the code repository
repo_dir="/path/to/code/repository"

# Define the location of the production environment
prod_dir="/path/to/production/environment"

# Go to the code repository
cd "$repo_dir"

# Pull the latest code changes
git pull

# Build the code
./build.sh

# Stop the running production environment
systemctl stop myapp

# Copy the new code to the production environment
rsync -av "$repo_dir/build/" "$prod_dir"

# Start the production environment
systemctl start myapp

# Check if the deployment was successful
if [ $? -eq 0 ]; then
  echo "Deployment successful!"
else
  echo "Deployment failed!"
fi
# In bash scripting, `$?` is used to refer to the exit status of the last executed command. In Unix-like operating systems, every command returns an exit status code when it completes, indicating whether it completed successfully (exit status 0) or not (non-zero exit status).
```

---

*Thanks For Reading! :)*

*\- Rushikesh Mashidkar💕*