## Scripts
>Contain a series of commands.
An interpreter executes commands in the script.
Anything we can type at the command line, we can put in a script.
Great for automating tasks.

```bash
# !/bin/bash
echo "Scripting is Fun!"
```
>**To Run**
chmod 755 script.sh
<br>OR
chmod +x script.sh

./script.sh

>**Shebank or Not to Shebang**<br>
If a script does not contain a shebang the commands are executed using your shell.
Different shells have slightly varying syntax.
<br>Default interpreter is bash

>>nano demo1.sh
```bash
#! /bin/bash
echo "Welcome to Script";
NAME = "Suresh"
echo "I am $NAME working on bash. 
```


>**Demos**
```bash
#! /bin/bash 
##echo command
echo "Welcome to Script"
```

```bash
#! /bin/bash 
##Variables
#Uppercase by convention
#Letters,numbers,underscores

NAME="Suresh"
echo "My name is $NAME"
```

```bash
#! /bin/bash 
## User Input
read -p "Enter your name : " NAME
echo "Hello $NAME, nice to meet you!"
```
```bash
#! /bin/bash 
## If Statement
NAME="Customer"

read -p "Enter Name : " NAME

if [ "$NAME" == "Admin" ]
then
echo "Welcome Admin"
elif [ "$NAME" == "Customer" ]
then
echo "Welcome Customer"
else
echo "Welcome User"
fi
```

```bash
#! /bin/bash 
## Operators
# val1 -eq val2 returns true if the values are equal
# val1 -ne val3 returns true if the values are not equal
# val1 -gt val2 returns true if val1 is greate than val2
# val1 -lt val2 returns true if val2 is greater than  val1
# ge => greater than or equal to
# le => less than or equal to

read -p "Enter Mark :" MARK
if [ "$MARK" -ge 50 ]
then
echo "PASS"
else
echo "FAIL"
fi

```

```bash
#! /bin/bash 

## File conditions
# -d file True if the file is a directory
# -e file True if the file exists 
# -f file True if the provided string is a file
# -g file True of the group id is set on a file
# -r file True if the file is readable

FILE="test.txt";
if [ -f "$FILE" ]
then
echo "$FILE is a file"
else
echo "$FILE is not a file"
fi
```

```bash
#! /bin/bash 

FILE="mydirectory";
if [ -e "$FILE" ]
then
echo "Exists"
else
echo "Not Exists"
fi
```

```bash
#! /bin/bash 
FILE="Desktop";
if [ -d "$FILE" ]
then
echo "$FILE directory is exists"
else
echo "$FILE directory is not exists"
fi
```


```bash
#! /bin/bash 

##CASE Statements
read -p "Are you 18 or over Y/N ?" AGE
case "$AGE" in 
[yY] | [yY][eE][sS])
echo "You are eligible for Vote"
;;
[nN] | [nN][oO])
echo "You are not eligible for Vote"
;;
*)
echo "Please enter y/yes or n/no "
;;
esac
```


```bash
#! /bin/bash 

## Simple For loop
NAMES="Ram Krishna Shiva Harish"
for NAME in $NAMES
	do
		echo "Hello $NAME"
done
```

```bash
#! /bin/bash 

FILES=$(ls *.txt)
NEW="new"
for FILE in $FILES
	do
	echo "Renaming $File to new-$FILE"
	mv $FILE $NEW-$FILE
done
```
```bash
#! /bin/bash 

## while loop - read through a file line by line
LINE=1
while read -r CURRENT_LINE
	do
	echo "$LINE:$CURRENT_LINE"
	((LINE++))
done < "./data.txt"
```

```bash
#! /bin/bash 

# Function
function displayName(){
echo "Welcome Suresh"
}

displayName
```

```bash
#! /bin/bash 

function displayName(){
echo "Welcome $1"
}

displayName "Ram"
```

```bash
#! /bin/bash 

##Create a folder and write to a file
mkdir hello
touch "hello/h1.txt"
echo "Hello One" >> "hello/h1.txt"
echo "Created hello/h1.txt"
```
