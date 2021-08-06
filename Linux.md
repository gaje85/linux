# Linux
## 1) Command basics
## 2) Navigation
## 3) Files and Folders
## 4) Nano 
## 5) Delete , copy and move 
## 6) shortcuts , history , redirection and piping 
## 7) find and grep
## 8) permission and Cron 
## 9) Shell Script basics 
## 10) exit and return codes, functions
## 11) wildcards
## 12) logging and loops 
---

## 1) Command basics

### Understanding prompt
```cmd
username@hostname:~$
```

* suresh@demos:~$ something
* suresh@demos:~$ clear
* commands are case sensitive
* Usage of arrow keys

### Username and Hostname
```bash
hostname
sudo hostnamectl set-hostname newname
echo $USER
```
### Date Commands
```
date 
cal
ncal
``` 

### Command Structure
```syntax
command –options  arguments
```
* Arguments
    * echo "Welcome to Linux Commands"
    
    ```
    echo - command
    Welcome to Linux Commands - arguments
    ```
    * ncal 2021
    * ncal july 2021
    * sort colors.txt

    ```bash
    Create a file in terminal [ Ctrl + D to save and exit]
        cat > colors.txt
            Enter content to a file    
            CTRL + D to save a file
        cat colors.txt => open a file
    ```
* Options
    * Options are prefixed by a dash, as in –h or -3
    ```
    julion days:
        ncal -j
        ncal -jy
        sort -r colors.txt
    -h – highlight of current date is getting off
        ncal -h
    Monday first day of week
        ncal -M
    current previous and next month
        ncal -3
    Before and Ater 
        ncal -B1
        ncal -A2
        ncal -B1 -A2
        ncal -B1 -A1 june 2020
        ncal -w     [weeknumber]
    ```
    * combined options
    ```
        ncal -3 -h
        ncal -3 -h -j
        ncal -3h
        ncal -3hj
    ```
    * long form options
    ```
    date --univarsal
    sort --reverse colors.txt
    sort --reverse --unique colors.txt
    sort --ru colors.txt
    ```
### Getting Help
    ```
    man command [manual page]
        man ncal  [press q to exit]
    ```
#### Manual Sections
1. User Commands
2. System Calls
3. C Libraray
4. Spefical files
5. File forms
6. Games
7. Miscellaneous
8. System admin commands

```
man 1 sort

man -k <word> [-k means to search in manual page]
    man -k sort
    man -k dog
```

#### Types of commands
>An executable program usually stored in /bin  or /usr/bin   or   /usr/local/bin

```
type sort
which sort
help sort
```
>Some commands do not have man pages written for them, because they are commands that are directy built in to the shell.
so we can use help command.
```
help cd
```
## 2) Navigation
![Folder Structure](overall.png "Title")

>Confusingly,there is a sub directory named "root". There are not the same.

>/home contains a home folder for each user on this system. home folder located at /home/colt

### 2 main directories
**/ - root**

**~ - home**

```
To Change into Root directory:
    cd ..
    cd ..

    OR
    cd ../../

Back to User Directory:
    cd home
    cd

    OR
    cd home/suresh
    OR
    cd ~
```
### Home Directory
```
To open Graphical User Interface:
    xdg-open /
    xdg-open ~
```
### Navigation Commands
1. pwd
>The print working directory command is super simple
but very useful. Think of it as a "where am I" command.

```bash
suresh@demos:~$ pwd
```
2. ls
>The list command will list the contents of a directory.
We can also list the contents of a specific directory
using ls path.
```bash
suresh@demos:~/Desktop/technology/java$ cd ..
suresh@demos:~/Desktop/technology$ ls
dotnet  java
suresh@demos:~/Desktop/technology$ ls java
advanced  core
suresh@demos:~/Desktop/technology$ ls /
bin    dev   lib    libx32      mnt   root  snap      sys  var
boot   etc   lib32  lost+found  opt   run   srv       tmp
cdrom  home  lib64  media       proc  sbin  swapfile  usr
```
* ls options
    * ls -l
    >-l (lowercase L) prints in long listing
format. It shows far more
information about each file/folder.
    * ls -a
    >the -a option will also list any
hidden files that begin with . These
are normally not listed.

    * ls -la
    >We can combine options! This
example prints detailed information
for all files, including hidden files.

    * ls -lah
    > human readable size

    * ls -l --sort=time
    > List folders and file wiht sort based on time.

    * . and ..
    ```bash
    suresh@demos:~/Desktop/technology$ ls -a
    .  ..  dotnet  java
    ```
    * list with comma separated values
    ```cmd
    suresh@demos:~/Desktop/technology$ ls -m
    ```
### Relative Paths and Absolute Paths
> Relative paths are paths that specify a
directory/file relative to the current directory.

> Absolute paths are paths that start from the
root directory (they start with a / )

```bash
suresh@demos:~/Desktop$ cd technology/java
suresh@demos:~/Desktop/technology/java$ 

suresh@demos:~/Desktop/technology/java$ cd /home/suresh/
```
## 3) Files and Folders
#### File
* Create a file (touch)
```cmd
suresh@demos:~/Desktop/employee$ ls
developer  org.txt  programmer  trainer
suresh@demos:~/Desktop/employee$ touch events.txt
suresh@demos:~/Desktop/employee$ touch technology/events2.txt
```
* File Details
```cmd
suresh@demos:~/Desktop/employee$ file events.txt
events.txt: empty

suresh@demos:~/Desktop/employee$ file website.html
website.html: HTML document, ASCII text
```
* Create a directory
```cmd
suresh@demos:~/Desktop/employee$ mkdir offers
suresh@demos:~/Desktop/employee$ mkdir dir1 dir2
```
* Create nested directory(-p => parent)
```cmd
suresh@demos:~/Desktop/employee$ mkdir -p dir3/dir3-1
```

* Open a file
```cmd
    cat events.txt
```
* move a file
```cmd
mv events.txt developer/
```
* copy a file
```cmd
cp events.txt ../programmer/
```
* file name
```cmd
touch abc
touch 123
touch my-file
touch my_file
touch second\ file
```
## 4) Nano
>Nano is a simple text editor that we can access rightfrom the terminal.
It's far more accessible than otherpopular command-line editors like vim and emacs.
Nano includes all the basic text editing functionalityyou would expect: search, spellcheck, syntaxhighlighting, etc.

```cmd
cd ~
mkdir Todos
cd Todos/
touch shoppingList.txt
nano shoppingList.txt
    * edit contents
    * Ctrl + S => to save
    * Ctrl + X => to Close
    * Ctrl + G => for Help
    * Alt + U => undo
    * Alt + E => redo
nano anotherFile.txt

nano +3 shoppingList.txt
    * cursor on 3rd line
```
```cmd
>copy and paste
    *copy content from some where
    *right click paste
    *to arrange properly press F4
> Searching
    Ctrl + W
        Alt + B => backward search
        Alt + C => case sensitive
> Replace
    Ctrl + \
        find word =>
        replace word =>
```
```cmd
>Spell Check
do some mistake in file and try the following
    * nano /etc/nanorc
    * sudo nano /etc/nanorc
    * uncomment => set speller "aspell -x -c"
    * open the file where we want to do spell check
    * Ctrl + T
```

>Demo
```cmd
>open more files in same buffer:

suresh@demos:~/Desktop/Nano$ sudo nano /etc/nanorc

    uncomment, "set multibuffer"


suresh@demos:~/Desktop/Nano$ nano File.txt

Ctrl + R => add another file in the same buffer.

Alt + ,  and Alt + .  => switching opened files. 
```

>Copy and paste in nano
```cmd
to Set Mark : alt + A
    then select content 
to copy : alt + ^
    choose the place to paste
to paste : Ctrl + U

to cut : alt + A (set mark and select content)
       : Ctrl + K
```
>Moving cursor
```cmd
Alt + \ => first line
Alt + /  => last line
Alt + g => goto particular line number
```
## 5) Delete , copy and move 
1.Deleting File/s
>We use the remove (rm) command to remove files from our machine.
For example,
rm app.js
would remove the app.js file.
Note: rm DELETES FILES, there is no undo or recyclingbin to retrieve them from!
They are gone!
```cmd
rm 123
rm technical/java/core/demo1.txt
```
2. Deleting folder/s
>To delete empty folders, we need to use the
-d
optionwith rm.
For example,
rm -d cats
would remove thecats directory (only if it's already empty)
To delete folders that are NOT empty, use the -r option.
For example,
rm -r chickens
would delete the chickensdirectory whether it's empty or not.
You definitely want to be careful when deletingdirectories!
```cmd
rm -d technology1
rm: cannot remove 'technology1': Directory not empty

rm  -r technology1
    * remove all contents of the dir.(recursive)

rm -i technology2
    * do you want to remove?

rm -ri technology3/
rm: descend into directory 'technology3/'? y
rm: remove directory 'technology3/dotnet'? y
rm: descend into directory 'technology3/java'? y
rm: remove regular empty file 'technology3/java/j2.txt'? y
rm: remove directory 'technology3/java/core'? y
rm: remove regular empty file 'technology3/java/j1.txt'? y
rm: remove directory 'technology3/java/advanced'? y
rm: remove directory 'technology3/java'? y
rm: remove directory 'technology3/'? y
```
3. Moving Files and Folders
>Use the move command (mv) to move files anddirectories from one location to another.
When we specify a file or files as the source and adirectory as the destination, we are moving the filesinto the directory.
For example,
mv app.css styles/
will move the app.cssfile into the styles directory

```cmd
suresh@demos:~/Desktop/technology3/java/core$ ls
suresh@demos:~/Desktop/technology3/java/core$ touch demo1.txt
suresh@demos:~/Desktop/technology3/java/core$ touch demo2.txt

suresh@demos:~/Desktop/technology3/java/core$ cd ..
suresh@demos:~/Desktop/technology3/java$ mv core/demo1.txt ../dotnet/
suresh@demos:~/Desktop/technology3/java$ ls ../dotnet
demo1.txt

>moving folder
suresh@demos:~/Desktop/technology3/java$ mv core/ ../dotnet/
suresh@demos:~/Desktop/technology3/java$ ls ../dotnet
core  demo1.txt
```

```cmd
>Rename
suresh@demos:~/Desktop/technology3/dotnet$ ls
core  demo1.txt
suresh@demos:~/Desktop/technology3/dotnet$ mv demo1.txt demo11.txt
suresh@demos:~/Desktop/technology3/dotnet$ ls
core  demo11.txt
```

4.  Copy File/s and Folder/s
>We can use the copy command to create copies offiles and folders.
To create a copy of sheep.txt called dolly.txt, we couldrun
cp sheep.txt dolly.txt
To copy multiple files into another directory, use cp file1file2 directory.
```cmd
cp events.txt ../../employee/
cp events.txt ../programmer/

suresh@demos:~/Desktop/technology3/dotnet$ cp demo11.txt ../../employee/
suresh@demos:~/Desktop/technology3/dotnet$ ls ../../employee/
 123          developer   dir3            offers    programmer
 2abc         dir1       'my file'        one-two   trainer
 demo11.txt   dir2       'my file2.txt'   org.txt   website.html
```
## 6) shortcuts , history , redirection and piping 

### Shortcuts
>We can speed up our command-line experience by
taking advantage of the many built-in shortcuts.
These shortcuts are designed so that your hands never
have to leave your keyboard "home base"
They take a little bit of practice to get comfortable
with, but it's worth the effort!
```cmd
    Ctrl + L  OR  clear 
        >clear terminal
    Ctrl + a => moves begin of a line
    Ctrl + e => moves end of a line
    Ctrl + f => moves next character(right arrow)
    Ctrl + b => moves previous character(left arrow)
    Ctrl + P => like up arrow
    Ctrl + N  => like down arrow

    Ctrl + space => forward one word(Ctrl + right arrow)
    Alt +  space => backward one word(Ctrl _ left arrow)

    Ctrl+V  => moves down a page, 
    Ctrl+Y  => moves up a page.

    Ctrl + - => decrease font size 
    Ctrl + = => increase font size

    Ctrl+t => swap
```
### History
>**History :** We can easily re-run an earlier command if we have its
line number from the history.
For example, to run the 73rd command in the history, we
could run !73
```cmd
history
!45
```
>**Searching History :** Often it's easiest to find an earlier command by searching
using a small portion of the command that you remember.
Type ctrl-r to enter "reverse-i-search". As you start typing,
bash will search the history and show you the best match.
Hit ctrl-r to cycle through potential matches.
```cmd
>in terminal
history
ctrl + r 
```
>>Working with Files

>**less** : The less command displays the contents of a file, one
page at a time. We can navigate forwards and
backwards through the file, which is especially useful
with very large files.
less somefile.txt will display the contents of somefile.txt
using less.
less
```cmd
less <filename>
```
>**cat** : The cat command concatenates and prints the
contents of files.
cat <filename> will read the contents of a file and
print them out. For example, cat instructions.txt will
read in from the instructions.txt file and then print the
contents out to the screen.
```cmd
cat <filename>
cat <file1> <file2>
```
>**tac** : tac (cat spelled backwards) will concatenate and print files in
reverse. It prints each line of a file, starting with the last line. You
can think of it as printing in reverse "vertically"
```cmd
cat file.txt
tac file.txt
```
>**rev** : the rev command prints the contents of a file, reversing the order
of each line. Think of it as a "horizontal" reverse, whereas tac is a
"vertical" reverse.
```cmd
rev file.txt
```

>**head** : 
The head command prints a portion of a file, starting
from the beginning of the file. By default, it prints the
first 10 lines of a file.
head file.txt would print the first 10 lines of
the file.txt file
>>We can also provide a number of bytes to print out,
rather than lines using the -c option.
```cmd
head file.txt
head  -n 12 file.txt
head -c 8 file.txt
```

>**tail** The tail command works similarly to the head
command, except it prints from the END of a file. By
default, it prints the last 10 lines of a file.
tail warAndPeace.txt would print the last 10 lines of the
warAndPeace.txt file
The same -n and -c options we saw with head also
work with the tail command.
```cmd
tail file.txt
tail  -n 12 file.txt
tail -c 8 file.txt
```

>**count** : The word count command can tell us the number of
words, lines, or bytes in files. By default, it prints out
three numbers: the lines, words, and bytes in a file.
We can use the -l option to limit the output to the
number of lines.
The -w option limits the output to the number of words
in the file.
```cmd
wc -l students.txt
```

>**sort** : The sort command outputs the sorted contents of a file
(it does not change the file itself). By default, it will sort
the lines of a file alphabetically.
sort names.txt would print each line from names.txt,
sorted in alphabetical order.
>>The **-n** option tells the sort command to sort using
numerical order.
sort -n prices.txt would print each line from names.txt,
sorted in numerical order.
We could also reverse it with sort -nr prices.txt
>>
>>We can specify a particular "column" that we want to
sort by, using the -k option followed by a field number.
In this example, sort data.txt -nk 2 tells sort to use the
numeric sort and to sort using the 2nd field.
```cmd
sort file.txt
sort file.txt -r
sort file.txt -u 
sort data.txt -nk 2
```

### Redirection
>**Standard Streams** :The three standard streams are communication
channels between a computer program and its environment.
They are:<br>
    **Standard Input** <br>
    **Standard Output**<br>
    **Standard Error**<br>


![Standard Input](standard_output.png "Output")

>**redirecting output** :<br>
The redirect output symbol (>) tells the shell to redirect
the output of a command to a specific file instead of
the screen.
By default, the date command will print the current
date to the screen. If we instead run date > output.txt
the output will be redirected to a file called output.txt
```cmd
echo "firstline" > first.txt
ls > first.txt
ls -l > first.txt
ls -l >> first.txt
```
![Standard Input](standard_input.png "Input")
>**redirecting input** :<br>
To pass the contents of a file to standard input, use the
< symbol followed by the filename.
For example, we could pass the contents of the
chickens.txt file to the cat command using
cat < chickens.txt
```bash
cat < first.txt
cat first.txt
```
>**combo** : <br>
We can redirect standard input and output at the same
time! In this example, we are using cat to read in the
contents of original.txt and then redirecting the output
to a file called output.txt
```bash
cat <first.txt >output.txt
sort <colors.txt >sorted.txt
sorts <colors.txt >sorted.txt 2>error.txt
```

![Standard Input](standard_error.png "Error")
>**redirecting standard error** : <br>
By default, error messages are output to the screen,
but we can change this by redirecting standard error.
The standard error redirection operator is 2>
If we ran a command like cat nonexistentfile (where
the file really does not exist) we would see an error
printed to the screen. We can instead redirect
standard error to a file with cat nonexistentfile 2>
error.txt
```cmd
cat < nonfile.txt >output.txt 2>error.txt

date 1> now.txt
OR
date > now.txt
```
>**getting fancy** : <br>
If we wanted to redirect both standard output and
standard error to the same file, we could do this...
getting fancy
ls docs > output.txt 2> output.txt
❯ls docs > output.txt 2>&1
❯
Or we could instead use 2>&1 which is a fancy syntax
for saying "redirect standard error to the same
location as standard output (or whatever has the file
descriptor #1)
```cmd
ls docs >output.txt 2>&1
    (same file using for output and error)
OR
ls docs &> output.txt
```

### Piping
>**Pipes** : <br>
Pipes are used to redirect a stream from one program
to another program. We can take the output of one
command and redirect it to the input of another.
>>We use the pipe character ( | ) to separate two
commands. The output of the first command will be
passed to the standard input of the second command.

```cmd
ls head-10
```
>**> vs |** <br>
Though both the > character and the | character are
used to redirect output, they do it in very different ways.<br>
**>** connects a command to some file.<br>
**|** connects a command to another command.
```cmd
ls | head -10
ls -l /usr/bin | less
date | rev
ls | wc
tac | rev
cat | sort
cat file.txt | head -7 | tail -5
```
>**tee command** <br>
The tee program reads standard input and copies it
both to standard output AND to a file. This allows us to
capture information part of the way through a pipeline,
without interrupting the flow.
```cmd
cat colors.txt error.txt | tee combo.txt

cat combo.txt
```

## Find and Grep
### Find
>**locate** :<br>
The locate command performs a search of pathnames
across our machine that match a given substring and
then prints out any matching names.
It is nice and speedy because it uses a pre-generated
database file rather than searching the entire machine.
For example, locate chick will perform a search for all
files that contain chick in their name.
>>**install mlocate** <br>
sudo apt install mlocate <br>
>>**locate options** <br>
The -e option will only print entries that actually exist at
the time locate is run.
The -i option tells locate to ignore casing
The -l or --limit option will limit the number of entries
that locate retrieves

```cmd
locate dotnet
locate -e dotnet
locate -i Dotnet
locate --limit 2 dotnet
```

>**find** : <br>
The locate command is nice and easy, but it can only
do so much! The find command is far more powerful!
Unlike locate, find does not use a database file.
By default, find on its own will list every single file and
directory nested in our current working directory.
We can also provide a specific folder. find friends/
would print all the files and directories inside the
friends directory (including nested folders)

>>**finding by type**<br>
We can tell find to only find by file type: only print files,
directories, symbolic links, etc using the -type option.
find -type f will limit the search to files
find -type d will limit the search to directories<br>

>>**finding by name**<br>
We can provide a specific pattern for find to use when
matching filenames and directories with the -name
option. We need to enclose our pattern in quotes.
To find all files on our Desktop that end in the .txt
extension, we could run find ~/Desktop -name "*.txt"
Use the -iname option for a case insensitive search

```bash
suresh@demos:~/Desktop$ find employee/

suresh@demos:~/Desktop$ find technology/

suresh@demos:~/Desktop$ find employee/programmer

suresh@demos:~/Desktop$ find employee -type d

suresh@demos:~/Desktop$ find employee -type f

suresh@demos:~/Desktop$ find employee/ -name "*.txt"

suresh@demos:~/Desktop$ find employee/ -iname "*.txt"

suresh@demos:~/Desktop$ find employee/ -name "*.txt"


```
>> **Counting Result** <br>
We can pipe the output of find to other commands like
word count. Use the -l option to count the number of
lines (each result from find is its own line)
```bash
suresh@demos:~/Desktop$ find employee/ -name "*.txt" | wc -l

suresh@demos:~/Desktop$ find employee/ -type d | wc -l

suresh@demos:~/Desktop$ find employee/ -type d | wc -l
```

>>**finding by size** <br>
We can use the -size option to find files of a specific
size. For example, to find all files larger than 1
gigabyte we could run find -size +1G
To find all files under 50 megabytes, we could run
find -size -50M
To find all files that are exactly 20 kilobytes, we could
run find -size 20k
```bash
find -size +20k
find -size -20k
```
>>**finding by owner** <br>
We can use the -user option to match files and
directories that belong to a particular user.
```bash
find -user suresh
find -user suresh | wc -l
```
> **Timestamps** <br>
mtime, or modification time, is when a file was last
modified AKA when its contents last changed.
ctime, or change time, is when a file was last changed.
This occurs anytime mtime changes but also when we
rename a file, move it, or alter permissions.
atime, or access time, is updated when a file is read by
an application or a command like cat.
>>**Finding by time** <br>
We can use the -mtime num option to match
files/folders that were last modified num*24 hours ago.
find -mmin -20 matches items that were modified LESS
than 20 minutes ago.
find -mmin +60 matches items that were modified
more than 60 minutes ago
```bash
find -mmin -30
find cmin +60
```

>>**Logical Operators**<br>
We can also use the -and, -or, and -not operators to
create more complex queries.
```bash
find -name "employee" or -name "technology"

suresh@demos:~/Desktop$ find -name "*and*" -or -name "*.html"

find -name "*n*" -or -name "*.html"

find -name "*n*" -and -name "*.txt"
```
>> **User-Defined Actions** <br>
We can provide find with our own action to perform
using each matching pathname.
The syntax is find -exec command {} ;
The {} are a placeholder for the current pathname
(each match), and the semicolon is required to indicate
the end of the command.
```bash
suresh@demos:~/Desktop/employee$find -name "*c*";

suresh@demos:~/Desktop/employee$find -name "*c*" -exec cat '{}' ';'

suresh@demos:~/Desktop$ find -name "*n*" -exec rm '{}' ';'

find -type f -user suresh -exec ls -l '{}' ';'

```
>>**User defined Actions with copy** <br>
find -type f -name "*.html" -exec cp  '{}' '{}_COPY' ';' <br>
The above example finds all files that end with .html. It then creates a
copy of each one using the cp command. Each of the copies ends with
"_COPY" so we end up with files like "index.html_COPY" and
"navbar.html_COPY"

```bash
find -type f -name "*.html" -exec cp '{}' '{}_COPY' ';'
```

>>**xargs** <br>
When we provide a command via -exec, that command
is executed separately for every single element. We
can instead use a special command called xargs to
build up the input into a bundle that will be provided as
an argument list to the next command.
```bash
find -name "*.txt" -exec ls '{}' ';'
OR
find -name "*.txt" | xargs ls

find -name "chapter[1-4].txt" | xargs cat>fullbook.txt

echo "hello" "world" | mkdir
 => Error

echo "hello" "word" | xargs mkdir
```

### Grep
>The grep command searches for patterns in
each file's contents. Grep will print each line
that matches a pattern we provide.
For example, grep "chicken" animals.txt will
print each line from the animals.txt file that
contains the pattern "chicken"

>> **Syntax** : grep PATTERN FILE

>> **Case Insensitive** :<br>
Use the -i option with grep to make the search
case insensitive.
grep -i "Chapter" book.txt will print all
matching lines from the book.txt file that contain
the word "chapter" in any casing. <br>
**grep -i "Chapter" book.txt**

>>**Word Search** : <br>
Use the -w option to ensure that grep only
matches words, rather than fragments located
inside of other words. A word is defined by nonword
characters on either side (start of line,
spaces, end of line, punctuation, etc.)<br>
**grep -w "cat" book.txt**  <br>
would match cat but not
catheter!

>>**Recursive Search** <br>
Use the -r option to perform a recursive search
which will include all files under a directory,
subdirectories and their files, and so on.
If we don't specify a starting directory, grep will
search the current working directory.<br>
**grep -r "chicken"** <br>
will search the current
working directory and any nested directories for
lines that contain "chicken"

>**Regex** <br>
We can provide regular expressions to grep. Regular
expressions helps us match complex patterns, BUT the
syntax does differ from what we've seen so far.
*   . - matches any single character
*   ^ - matches the start of a line
*   $ - matches the end of a line
*   [abc] - matches any character in the set
*   [^abc] - matches any char NOT in set
*[A-Z] - matches characters in a range
* *- repeat previous expression 0 or more times
*   \ - escape meta-characters

*   -c => count
*   -o => only matches(not entire line)
*   -i => ignore case
*   -w => only particular word
*   -r => recursive in all files and sub folders
```bash

suresh@demos:~/Desktop$ grep "ram" employee.txt

suresh@demos:~/Desktop$ grep -i "ram" employee.txt

suresh@demos:~/Desktop$ grep -iw "Ram" employees.txt

suresh@demos:~/Desktop$ grep -r "Ram";


grep '[1-9]....' prices.txt

grep -c '$[1-9]....' prices.txt 

grep -o "\$[1-9]" prices.txt

```

>**Piping To Grep** <br>
A common use case is to use grep to whittle
down or filter a large chunk of data.
In this example, the ps -aux command will
output a huge list of all processes running on our
machine. We pipe that data to grep, and then
filter it down to only the processes that include
"hermione"
In effect, this command lets us see what
hermione is up to!

```bash
ps -aux | grep hermione

man grep | grep "count"
```

## 8) permission and Cron 
### Permission
>**Multiple Users** <br>
Unix and unix-like systems are multiuser operating
systems. More than one person can be using the same
computer at the same time (though this is tough
logistically with only one display and keyboard!)
Way back when, computers were crazy expensive,
massive machines. A university might only have one
computer, but dozens of terminals sprinkled across
campus.

>>**Permission Denied?** <br>
As regular users, we do not have permission to write or
even read every file on the machine.
For example, if I try to read the file /etc/sudoers using <br>
**cat /etc/sudoers** <br> I get a "permission denied" message.

>>**Groups** <br>
On unix systems, a single user may be the owner of files
and directories, meaning that they have control over
their access.
Additionally, users can belong to groups which are
given access to particular files and folders by their
owners.

>>**User and Group IDs** <br>
When a new user account is made, it is
assigned a user ID. The user is also assigned
a group ID.
We can use the id command to view user and
group ids.<br><br>
These user ids are stored in <br>
**/etc/passwd** <br>
and the group ids are in 
**/etc/group** <br>
```bash
suresh@demos:~/Desktop$  id
```
```bash
suresh@demos:~/Desktop$ echo "Welcom to Linux" > greet.txt

suresh@demos:~/Desktop$ ls greet.txt
Ans : greet.txt

suresh@demos:~/Desktop$ ls -l greet.txt
Ans: -rw-rw-r-- 1 suresh suresh 16 Aug  3 14:37 greet.txt

```

>**File Attributes** <br>
The weird looking 10 characters we see
printed out first are the file attributes.
These characters tell us the type of the file,
the read, write, and execute permissions for
the file's owner, the file's group owner, and
everyone else.

>>**File Types** <br>
The very first character indicates the type of
the file. Some of the more common types and
their corresponding attributes are:
*   -regular file
*   d directory
*   c character special file
*   l symbolic link

![Permission Image](Permission.png "Title")

>**Permissions** <br>
**Effect on Files** <br>
**r** : file can be read <br>
**W** : file can be modified<br>
**X** : file can be treated as a
program to be executed<br>
**-** : file cannot be read, modified,
or executed depending on the
location of the - character<br>

**Effect on Directories** <br>
**r** : directory's contents can be listed <br>
**W** : directory's contents can be modified (create new
files, rename files/folders) but only if the
executable attribute is also set<br>
**X** : allows a directory to be entered or "cd"ed into<br>
**-** : directory contents cannot be shown, modified, or
cd'ed into depending on the location of the -
character<br>

```bash
create a user:

```

```
suresh@demos:~$ whoami

suresh@demos:~$ cd ~

suresh@demos:~$ pwd

suresh@demos:~$ cd ..
suresh@demos:/home$ ls
    dinesh  suresh

```

>**chmod**<br>
To change the permissions of a file or directory, we can
use the chmod command (change mode).
To use chmod to alter permissions, we need to tell it:
- **Who** we are changing permissions for
- **What** change are we making? Adding? Removing?
- **Which** permissions are we setting?

>>**syntax** <br>
chmod mode file

>>**who**
- **u** - user (the owner of the file)
- **g** - group (members of the group the file belongs to
- **o** - others (the "world"
- **a** - all of the above

>>**what**
-   **-** (minus sign) removes the permission
-   **+** (plus sign) grants the permission
-   **=** (equals sign) set a permission and removes others

>>**which**
-   **r** - the read permission
-   **w** - the write permission
-   **x** - the execute permission

```bash
chmod g+w file.txt
    => Add write permissions to the group
chmod a-w file.txt
    => Remove write permissions from all

chmode a=r file.txt
    => Set permissions to read ONLY for all.
```

>**chmod octals**
chmod also supports another way of representing
permission patterns: octal numbers (base 8). Each digit
in an octal number represents 3 binary digits.

| Octal | Binary | File Mode |
| :---: | :---: | :---: |
| 0 | 000 | --- |
| 1 | 001 | --x |
| 2 | 010 | -w- |
| 3 | 011 | -wx |
| 4 | 100 | r-- |
| 5 | 101 | r-x |
| 6 | 110 | rw- |
| 7 | 111 | rwx |

>>chmod 755 file.txt
<br>rwxr-xr-x


change current user / Identity
>>su - dinesh

>**Root User**<br>
In Linux systems, there is a super user called
root. The root user can run any command and
access any file on the machine, regardless of
the file's actual owner.
The root user has tons of power and could
easily damage or even destroy the system by
running the wrong commands!
For this reason, Ubuntu locks the root user by
default.

```bash
sudo -l

sudo apt update
```

