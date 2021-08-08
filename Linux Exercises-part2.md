>>Kindly find and download needed files from this repository 

# Task4
download the following files
1.  recipe.txt
1.  website.html
1.  country-data.json

## Part 1

1. Open up the `recipe.txt` file using `nano`
2. On line 3, add your own name after `Author:` so that it says `Author: Stevie Wonder` or whatever your name is
3. Whoever wrote this recipe didn't know how to spell "parmesan", so instead they wrote "parm".  Please update the two instances of "Parm" to "Parmesan".  You can do this manually or by using nano's replace feature.
4. Write out your changes! Close the file.

## Part 2

1. Open up the `website.html` file with `nano`
2. This html file contains a simple website for a fictional restaurant called "Ristorante Colt".  You recently purchased the restaurant and have decided to change its name! Please replace all instance of "Ristorante Colt" with your new restaurant's name.  Do this using a nano shortcut, rather than manually replacing each one.
3. Save your changes and close the file!

## Part 3

1. The `country-data.json` file contains a large country dataset, with over 39,000 lines of json!
2. Unfortunately, there is a typo on line **15399**.  It says "Hondras" but it should say "Honduras".  Please fix this!  Rather than scrolling for a decade, use a nano shortcut to jump to line **15399**.
3. **Bonus:** Figure out how to tell `nano` to open the file at exactly **15399**.


# Task5 Deleting, Moving & Copying
## Part 1: Creating The Folders & Files

Before we can delete, move, or copy things...we need things! It's time to get some more practice using `touch` and `mkdir`

Please create a new directory somewhere on your machine called `Bootcamp`.  Inside of it, create the the folders and files indicated below:
```bash
Bootcamp/
	FallCohort/
		Italo.txt
		Edgar.txt
		Linus.txt
		Sara.txt 
		Silvio.txt
		Waitlist/
			Hanna.txt
			Haris.txt
			Netta.txt
	WinterCohort/
		Santiago.txt
		Iris.txt
		Naomi.txt
```
- Sadly `Edgar` had to drop out of the course.  Delete the `Edgar.txt` file in `FallCohort`
- This means we now have space in our Fall Cohort to move someone off of the waitlist.  Please move `Netta.txt` from the `Waitlist` folder into the `FallCohort` folder.
- Please delete the `Waitlist` folder and its contents
- It turns out that I misspelled Sara.  She spells her name "Sarah" with an "h" at the end.  Please rename the `Sara.txt` file to `Sarah.txt`
- Unfortunately Italo is having a bit of a personal emergency, and he would like to move to our WinterCohort.  Please move the `Italo.txt` file from `FallCohort` to the `WinterCohort` folder
- Oh no, our entire Winter Cohort had to be cancelled because of a worldwide pandemic :(   We decided to bump all of the scheduled winter students to spring. In the `Bootcamp` directory create a copy of the `WinterCohort` folder called `SpringCohort`
- Please rename the WinterCohort folder to `WinterCohortCANCELLED`
- Oh no! We're going out of business. Please delete the entire `Bootcamp` directory 😢

# Task6 Working with Files
## Part 1

- Use a command to print out the entire contents of the `poem.txt` file. Use an option so that the output also includes line numbers.
- That is a headache to read all at once! Read poem.txt using `less` instead.
    - Scroll down one line at a time
    - Scroll up one line at a time
    - Scroll down one "page" at a time
    - Scroll up one "page" at a time
- Search within less for the term "Dog".  Can you find the line that contains it?
    - **BONUS:** can you run a case-insesitive search?  The poem contains both "dog" and "Dog" on separate lines.
- Now it's time to do some research! Find the option to tell less to open with lines numbers displayed. Open `poem.txt` this way
- Then find the "command" you can type into less to go to exactly 50% of the way through the file.
- Use a command to find the number of **words** in `poem.txt`
- Run a command to print out the first 4 lines of `poem.txt`
- Run a command to print out the last 8 lines of `poem.txt`

## Part 2

- Run a command to print out the lines in `purchases.txt` in reverse order (last line printed first)
- Run a command to print out the lines in `purchases.txt`, sorted alphabetically.
- Run a command to count the number of **lines** in `purchases.txt`
- Run a command to print out the lines in `purchases.txt`, sorted by the price (the final column) in the dataset in REVERSE order (highest price to lowest price)

# Task7 Redirection
You are taking part in a wildlife survey in a remote portion of the Peruvian Amazon! This morning, three of your research assistants each went on transect walks where they recorded the individual species they observed.     Your (simple) job is to combine their findings into a new file that contains all the species that were observed!

1. Create a new file called `all-species.txt` that contains the combined contents of `angela-survey.txt`, `nico-survey.txt`, and `juan-survey.txt`.  Do this using a single command!
2. The problem with the `all-species.txt` file is that it contains duplicate entries!  Use a single command to sort the lines in alphabetical order, only sorting uniques, and send the output to a new file called `sorted-animals.txt`
3. Now, you go out for a nice morning stroll and stumble upon a large anaconda sunning itself on a log.  You should add this observation to the list of species!!
    1. Start by appending the current date to the end of the `sorted-animals.txt` file using a command (don't open the file manually!)
    2. Then append the text "Green Anaconda" to the end of `sorted-animals.txt`
4. Run the non-existent command `ughhh` and redirect any error messages so that they are **appended** to the sorted-animals.txt file.

# Task8 Piping
Unzip the file([PokemonExercise.zip]  The resulting folder contains a subfolder called `PokeDex/` which in turn contains a whole bunch of files, each named for a specific Pokemon like:

```bash
PokemonExercise/
	PokeDex/
		100Voltorb
		101Electrode
	  619Mienfoo
		...
```

