## Task1:
*   Write a shell script that prints "Shell Scripting is Fun!" to the screen.
*   Hint 1:
Remember to make the shell script executable with the chmod command.
*   Hint 2: Remember to start your script with a shebang!

## Task2:
*   Write a shell script to check to see if the file "/etc/shadow" exists. 
*   If it does exist, display
"Shadow passwords are enabled." Next, check to see if you can write to the file. 
*   If you can, display "You have permissions to edit /etc/shadow." If you cannot, display "You do NOT have
permissions to edit /etc/shadow."

## Task3:
*   Write a shell script that displays "man", "bear", "pig", "dog", "cat", and sheep to the screen with
each appearing on a separate line. Try to do this in as few lines as possible.
*   Hint: Loops can be used to perform repetitive tasks.

## Task4:
*   Write a shell script that prompts the user for a name of a file or directory and reports if it is a
regular file, a directory, or other type of file.
*   Also perform an ls command against the file or directory with the long listing option.


## Task5
*   Modify the previous script so that it accepts the file or directory name as an argument instead of
prompting the user to enter it.






## Task6
*   Write a shell script that accepts a file or directory name as an argument. Have the script report
*   If it is a regular file, a directory, or other type of file. 
*   If it is a regular file, exit with a 0 exit status.
*   If it is a directory, exit with a 1 exit status. If it is some other type of file, exit with a 2 exit status.


## Task7
*   Write a script that executes the command "cat /etc/shadow". 
*   If the command returns a 0 exit
status report "Command succeeded" and exit with a 0 exit status. 
*   If the command returns a nonzero
exit status report "Command failed" and exit with a 1 exit status.




## Task8
Write a shell script that consists of a function that display the number of files in the present
working directory. Name this function "file_count" and call it in your script. If you use a variable
in your function, remember to make it a local variable.
Hint: The wc utility is used to count the number of lines, words, and bytes.

## Task9 
*   Write a shell script that renames all files in the current directory that end in ".jpg" to begin with
today's date in the following format: YYYYMMDD.
For example, if a picture of my cat was in
the current directory and today was October 31, 2016 it would change name from "mycat.jpg" to
"20161031mycat.
jpg".
*   Hint: Look at the format options to the date command.
For "extra credit" make sure to gracefully handle instances where there are no ".jpg" files in the
current directory. (Hint: Man bash and read the section on the nullglob option.)