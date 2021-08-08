# Task1 - Command Basics
- There is a command called `whoami`.  **Before you run it**, read the manual page entry on it.  From the manual page entry, can you tell if it needs any options or arguments? What does it do?
- Now try running it! What happens?
- There is another command called `who`.  Without turning to Google, figure out what it does! Does it require any arguments or options to run?
- Use the `who` command to print out the time of the most recent system boot.  You'll need to find an option to help you do this!
- Run a command to figure out whether the `echo` command is a a binary, a shell-built in, or an alias.
- Do the same for  the `date` command

# Task2 - Navigation
>The Farm folder contains the following subdirectories:
<pre>
Farm/
	Coop/ 
		Chickens/
		Geese/
	Stable/
		Horses/
</pre>

**From this point forward, ONLY use the terminal to accomplish the following:**

1. Open a new terminal window. Navigate to the `Farm` folder.
2. List the contents of the `Farm` directory.
3. "Move" into the `Coop` folder.
4. List the contents of the `Coop` folder.
5. "Move" into the `Chickens` folder.
6. List out the chickens in the `Chickens` folder.  How many are there?
7. One of the chickens is very very old, which one is it? (which file in the `Chickens` folder has the oldest modification time?) Use a command to figure it out!
8. In a **single** command, move from the `Chickens` directory to the `Geese` directory.  Consult the folder structure written out above if needed.
9. How many geese (files) are in the `Geese` directory?
10. One of the geese is sitting on a golden egg!  It's larger than the other geese. Which one is it?  (which file in the `Geese` folder is the largest?).  Use a command to figure it out!
11. Navigate to the `Horses` directory.  Consult the folder structure written out above, if needed.
12. How many horses are in the `Horses` directory?
13. Wait! There is a hidden horse in the `Horses` directory! What is it's name??

# Task3 Making/Creating Files and Folders
To get some practice creating files and folders from the command-line, we'll be creating a standard React project file structure.  Don't worry at all if you don't know React, we're just making a bunch of empty files and folders!  

1. Create a new folder called `my-app`
2. Navigate to `my-app` and inside create two new empty files called `README.md` and `package.json`
3. Still inside of `my-app` create a new folder called `public`. Without `cd`-ing into `public`, create an `index.html` file inside of it.
4. Create a new folder called `src` inside of `my-app`.  Navigate inside of it.
5. Using a single line, create the following four files inside of `src`: `App.css`, `App.js`, `index.css`, and `index.js`

Your folder structure should now look like this:
<pre>
my-app/
  README.md
  package.json
  public/
    index.html
  src/
    App.css
    App.js
    index.css
    index.js
    </pre>
