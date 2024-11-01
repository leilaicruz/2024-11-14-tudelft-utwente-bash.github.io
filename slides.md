# Introducing the Shell

------------------------------------------------------------------------


# Navigating Files and Directories

------------------------------------------------------------------------

![](fig/filesystem.svg){alt="The file system is made up of a root directory that contains sub-directories titled bin, data, users, and tmp"}

------------------------------------------------------------------------

![](fig/home-directories.svg){alt="Like other directories, home directories are sub-directories underneath \"/Users\" like \"/Users/imhotep\", \"/Users/larry\" or\"/Users/nelle\""}

------------------------------------------------------------------------

![](fig/filesystem-challenge.svg){alt="A directory tree below the Users directory where \"/Users\" contains the directories \"backup\" and \"thing\"; \"/Users/backup\" contains \"original\",\"pnas_final\" and \"pnas_sub\"; \"/Users/thing\" contains \"backup\"; and\"/Users/thing/backup\" contains \"2012-12-01\", \"2013-01-08\" and\"2013-01-27\""}

------------------------------------------------------------------------

![](fig/filesystem-challenge.svg){alt="A directory tree below the Users directory where \"/Users\" contains the directories \"backup\" and \"thing\"; \"/Users/backup\" contains \"original\",\"pnas_final\" and \"pnas_sub\"; \"/Users/thing\" contains \"backup\"; and\"/Users/thing/backup\" contains \"2012-12-01\", \"2013-01-08\" and\"2013-01-27\""}

------------------------------------------------------------------------

![](fig/shell_command_syntax.svg){alt="General syntax of a shell command"}

------------------------------------------------------------------------

::: challenge
## Exploring More `ls` Options

You can also use two options at the same time. What does the command
`ls` do when used with the `-l` option? What about if you use both the
`-l` and the `-h` option?

Some of its output is about properties that we do not cover in this
lesson (such as file permissions and ownership), but the rest should be
useful nevertheless.
:::

------------------------------------------------------------------------

::: challenge
## Listing in Reverse Chronological Order

By default, `ls` lists the contents of a directory in alphabetical order
by name. The command `ls -t` lists items by time of last change instead
of alphabetically. The command `ls -r` lists the contents of a directory
in reverse order. Which file is displayed last when you combine the `-t`
and `-r` options? Hint: You may need to use the `-l` option to see the
last changed dates.
:::

------------------------------------------------------------------------

::: challenge
## Absolute vs Relative Paths

Starting from `/Users/nelle/data`, which of the following commands could
Nelle use to navigate to her home directory, which is `/Users/nelle`?

1.  `cd .`
2.  `cd /`
3.  `cd /home/nelle`
4.  `cd ../..`
5.  `cd ~`
6.  `cd home`
7.  `cd ~/data/..`
8.  `cd`
9.  `cd ..`
:::

------------------------------------------------------------------------

::: challenge
## Relative Path Resolution

Using the filesystem diagram below, if `pwd` displays `/Users/thing`,
what will `ls -F ../backup` display?

1.  `../backup: No such file or directory`
2.  `2012-12-01 2013-01-08 2013-01-27`
3.  `2012-12-01/ 2013-01-08/ 2013-01-27/`
4.  `original/ pnas_final/ pnas_sub/`

![](fig/filesystem-challenge.svg){alt="A directory tree below the Users directory where \"/Users\" contains the directories \"backup\" and \"thing\"; \"/Users/backup\" contains \"original\",\"pnas_final\" and \"pnas_sub\"; \"/Users/thing\" contains \"backup\"; and\"/Users/thing/backup\" contains \"2012-12-01\", \"2013-01-08\" and\"2013-01-27\""}
:::

------------------------------------------------------------------------

::: challenge
## `ls` Reading Comprehension

Using the filesystem diagram below, if `pwd` displays `/Users/backup`,
and `-r` tells `ls` to display things in reverse order, what command(s)
will result in the following output:

``` output
pnas_sub/ pnas_final/ original/
```

![](fig/filesystem-challenge.svg){alt="A directory tree below the Users directory where \"/Users\" contains the directories \"backup\" and \"thing\"; \"/Users/backup\" contains \"original\",\"pnas_final\" and \"pnas_sub\"; \"/Users/thing\" contains \"backup\"; and\"/Users/thing/backup\" contains \"2012-12-01\", \"2013-01-08\" and\"2013-01-27\""}

1.  `ls pwd`
2.  `ls -r -F`
3.  `ls -r -F /Users/backup`
:::

------------------------------------------------------------------------


# Working With Files and Directories

------------------------------------------------------------------------

![](fig/nano-screenshot.png){alt="screenshot of nano text editor in action with the text It's not publish or perish any more, it's share and thrive"}

------------------------------------------------------------------------

::: challenge
## Creating Files a Different Way

We have seen how to create text files using the `nano` editor. Now, try
the following command:

``` bash
$ touch my_file.txt
```

1.  What did the `touch` command do? When you look at your current
    directory using the GUI file explorer, does the file show up?

2.  Use `ls -l` to inspect the files. How large is `my_file.txt`?

3.  When might you want to create a file this way?

To avoid confusion later on, we suggest removing the file you've just
created before proceeding with the rest of the episode, otherwise future
outputs may vary from those given in the lesson. To do this, use the
following command:

``` bash
$ rm my_file.txt
```
:::

------------------------------------------------------------------------

::: challenge
## Moving Files to a new folder

After running the following commands, Jamie realizes that she put the
files `sucrose.dat` and `maltose.dat` into the wrong folder. The files
should have been placed in the `raw` folder.

``` bash
$ ls -F
 analyzed/ raw/
$ ls -F analyzed
fructose.dat glucose.dat maltose.dat sucrose.dat
$ cd analyzed
```

Fill in the blanks to move these files to the `raw/` folder (i.e. the
one she forgot to put them in)

``` bash
$ mv sucrose.dat maltose.dat ____/____
```
:::

------------------------------------------------------------------------

::: challenge
## Renaming Files

Suppose that you created a plain-text file in your current directory to
contain a list of the statistical tests you will need to do to analyze
your data, and named it `statstics.txt`

After creating and saving this file you realize you misspelled the
filename! You want to correct the mistake, which of the following
commands could you use to do so?

1.  `cp statstics.txt statistics.txt`
2.  `mv statstics.txt statistics.txt`
3.  `mv statstics.txt .`
4.  `cp statstics.txt .`
:::

------------------------------------------------------------------------

::: challenge
## Moving and Copying

What is the output of the closing `ls` command in the sequence shown
below?

``` bash
$ pwd
```

``` output
/Users/jamie/data
```

``` bash
$ ls
```

``` output
proteins.dat
```

``` bash
$ mkdir recombined
$ mv proteins.dat recombined/
$ cp recombined/proteins.dat ../proteins-saved.dat
$ ls
```

1.  `proteins-saved.dat recombined`
2.  `recombined`
3.  `proteins.dat recombined`
4.  `proteins-saved.dat`
:::

------------------------------------------------------------------------

::: challenge
## Using `rm` Safely

What happens when we execute `rm -i thesis_backup/quotations.txt`? Why
would we want this protection when using `rm`?
:::

------------------------------------------------------------------------

::: challenge
## Copy with Multiple Filenames

For this exercise, you can test the commands in the
`shell-lesson-data/exercise-data` directory.

In the example below, what does `cp` do when given several filenames and
a directory name?

``` bash
$ mkdir backup
$ cp creatures/minotaur.dat creatures/unicorn.dat backup/
```

In the example below, what does `cp` do when given three or more file
names?

``` bash
$ cd creatures
$ ls -F
```

``` output
basilisk.dat  minotaur.dat  unicorn.dat
```

``` bash
$ cp minotaur.dat unicorn.dat basilisk.dat
```
:::

------------------------------------------------------------------------

::: challenge
## List filenames matching a pattern

When run in the `alkanes` directory, which `ls` command(s) will produce
this output?

`ethane.pdb   methane.pdb`

1.  `ls *t*ane.pdb`
2.  `ls *t?ne.*`
3.  `ls *t??ne.pdb`
4.  `ls ethane.*`
:::

------------------------------------------------------------------------

::: challenge
## More on Wildcards

Sam has a directory containing calibration data, datasets, and
descriptions of the datasets:

``` bash
.
├── 2015-10-23-calibration.txt
├── 2015-10-23-dataset1.txt
├── 2015-10-23-dataset2.txt
├── 2015-10-23-dataset_overview.txt
├── 2015-10-26-calibration.txt
├── 2015-10-26-dataset1.txt
├── 2015-10-26-dataset2.txt
├── 2015-10-26-dataset_overview.txt
├── 2015-11-23-calibration.txt
├── 2015-11-23-dataset1.txt
├── 2015-11-23-dataset2.txt
├── 2015-11-23-dataset_overview.txt
├── backup
│   ├── calibration
│   └── datasets
└── send_to_bob
    ├── all_datasets_created_on_a_23rd
    └── all_november_files
```

Before heading off to another field trip, she wants to back up her data
and send some datasets to her colleague Bob. Sam uses the following
commands to get the job done:

``` bash
$ cp *dataset* backup/datasets
$ cp ____calibration____ backup/calibration
$ cp 2015-____-____ send_to_bob/all_november_files/
$ cp ____ send_to_bob/all_datasets_created_on_a_23rd/
```

Help Sam by filling in the blanks.

The resulting directory structure should look like this

``` bash
.
├── 2015-10-23-calibration.txt
├── 2015-10-23-dataset1.txt
├── 2015-10-23-dataset2.txt
├── 2015-10-23-dataset_overview.txt
├── 2015-10-26-calibration.txt
├── 2015-10-26-dataset1.txt
├── 2015-10-26-dataset2.txt
├── 2015-10-26-dataset_overview.txt
├── 2015-11-23-calibration.txt
├── 2015-11-23-dataset1.txt
├── 2015-11-23-dataset2.txt
├── 2015-11-23-dataset_overview.txt
├── backup
│   ├── calibration
│   │   ├── 2015-10-23-calibration.txt
│   │   ├── 2015-10-26-calibration.txt
│   │   └── 2015-11-23-calibration.txt
│   └── datasets
│       ├── 2015-10-23-dataset1.txt
│       ├── 2015-10-23-dataset2.txt
│       ├── 2015-10-23-dataset_overview.txt
│       ├── 2015-10-26-dataset1.txt
│       ├── 2015-10-26-dataset2.txt
│       ├── 2015-10-26-dataset_overview.txt
│       ├── 2015-11-23-dataset1.txt
│       ├── 2015-11-23-dataset2.txt
│       └── 2015-11-23-dataset_overview.txt
└── send_to_bob
    ├── all_datasets_created_on_a_23rd
    │   ├── 2015-10-23-dataset1.txt
    │   ├── 2015-10-23-dataset2.txt
    │   ├── 2015-10-23-dataset_overview.txt
    │   ├── 2015-11-23-dataset1.txt
    │   ├── 2015-11-23-dataset2.txt
    │   └── 2015-11-23-dataset_overview.txt
    └── all_november_files
        ├── 2015-11-23-calibration.txt
        ├── 2015-11-23-dataset1.txt
        ├── 2015-11-23-dataset2.txt
        └── 2015-11-23-dataset_overview.txt
```
:::

------------------------------------------------------------------------

::: challenge
## Organizing Directories and Files

Jamie is working on a project, and she sees that her files aren't very
well organized:

``` bash
$ ls -F
```

``` output
analyzed/  fructose.dat    raw/   sucrose.dat
```

The `fructose.dat` and `sucrose.dat` files contain output from her data
analysis. What command(s) covered in this lesson does she need to run so
that the commands below will produce the output shown?

``` bash
$ ls -F
```

``` output
analyzed/   raw/
```

``` bash
$ ls analyzed
```

``` output
fructose.dat    sucrose.dat
```
:::

------------------------------------------------------------------------

::: challenge
## Reproduce a folder structure

You're starting a new experiment and would like to duplicate the
directory structure from your previous experiment so you can add new
data.

Assume that the previous experiment is in a folder called `2016-05-18`,
which contains a `data` folder that in turn contains folders named `raw`
and `processed` that contain data files. The goal is to copy the folder
structure of the `2016-05-18` folder into a folder called `2016-05-20`
so that your final directory structure looks like this:

``` output
2016-05-20/
└── data
   ├── processed
   └── raw
```

Which of the following set of commands would achieve this objective?
What would the other commands do?

``` bash
$ mkdir 2016-05-20
$ mkdir 2016-05-20/data
$ mkdir 2016-05-20/data/processed
$ mkdir 2016-05-20/data/raw
```

``` bash
$ mkdir 2016-05-20
$ cd 2016-05-20
$ mkdir data
$ cd data
$ mkdir raw processed
```

``` bash
$ mkdir 2016-05-20/data/raw
$ mkdir 2016-05-20/data/processed
```

``` bash
$ mkdir -p 2016-05-20/data/raw
$ mkdir -p 2016-05-20/data/processed
```

``` bash
$ mkdir 2016-05-20
$ cd 2016-05-20
$ mkdir data
$ mkdir raw processed
```
:::

------------------------------------------------------------------------


# Pipes and Filters

------------------------------------------------------------------------

![](fig/redirects-and-pipes.svg){alt="Redirects and Pipes of different commands: \"wc -l *.pdb\" will direct theoutput to the shell. \"wc -l *.pdb > lengths\" will direct output to the file\"lengths\". \"wc -l *.pdb | sort -n | head -n 1\" will build a pipeline where theoutput of the \"wc\" command is the input to the \"sort\" command, the output ofthe \"sort\" command is the input to the \"head\" command and the output of the\"head\" command is directed to the shell"}

------------------------------------------------------------------------

::: challenge
## What Does `sort -n` Do?

The file `shell-lesson-data/exercise-data/numbers.txt` contains the
following lines:

``` source
10
2
19
22
6
```

If we run `sort` on this file, the output is:

``` output
10
19
2
22
6
```

If we run `sort -n` on the same file, we get this instead:

``` output
2
6
10
19
22
```

Explain why `-n` has this effect.
:::

------------------------------------------------------------------------

::: challenge
## What Does `>>` Mean?

We have seen the use of `>`, but there is a similar operator `>>` which
works slightly differently. We'll learn about the differences between
these two operators by printing some strings. We can use the `echo`
command to print strings e.g.

``` bash
$ echo The echo command prints text
```

``` output
The echo command prints text
```

Now test the commands below to reveal the difference between the two
operators:

``` bash
$ echo hello > testfile01.txt
```

and:

``` bash
$ echo hello >> testfile02.txt
```

Hint: Try executing each command twice in a row and then examining the
output files.
:::

------------------------------------------------------------------------

::: challenge
## Appending Data

We have already met the `head` command, which prints lines from the
start of a file. `tail` is similar, but prints lines from the end of a
file instead.

Consider the file
`shell-lesson-data/exercise-data/animal-counts/animals.csv`. After these
commands, select the answer that corresponds to the file
`animals-subset.csv`:

``` bash
$ head -n 3 animals.csv > animals-subset.csv
$ tail -n 2 animals.csv >> animals-subset.csv
```

1.  The first three lines of `animals.csv`
2.  The last two lines of `animals.csv`
3.  The first three lines and the last two lines of `animals.csv`
4.  The second and third lines of `animals.csv`
:::

------------------------------------------------------------------------

::: challenge
## Piping Commands Together

In our current directory, we want to find the 3 files which have the
least number of lines. Which command listed below would work?

1.  `wc -l * > sort -n > head -n 3`
2.  `wc -l * | sort -n | head -n 1-3`
3.  `wc -l * | head -n 3 | sort -n`
4.  `wc -l * | sort -n | head -n 3`
:::

------------------------------------------------------------------------

::: challenge
## Pipe Reading Comprehension

A file called `animals.csv` (in the
`shell-lesson-data/exercise-data/animal-counts` folder) contains the
following data:

``` source
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
2012-11-06,deer,2
2012-11-06,fox,4
2012-11-07,rabbit,16
2012-11-07,bear,1
```

What text passes through each of the pipes and the final redirect in the
pipeline below? Note, the `sort -r` command sorts in reverse order.

``` bash
$ cat animals.csv | head -n 5 | tail -n 3 | sort -r > final.txt
```

Hint: build the pipeline up one command at a time to test your
understanding
:::

------------------------------------------------------------------------

::: challenge
## Pipe Construction

For the file `animals.csv` from the previous exercise, consider the
following command:

``` bash
$ cut -d , -f 2 animals.csv
```

The `cut` command is used to remove or 'cut out' certain sections of
each line in the file, and `cut` expects the lines to be separated into
columns by a `<kbd>`{=html}Tab`</kbd>`{=html} character. A character
used in this way is called a **delimiter**. In the example above we use
the `-d` option to specify the comma as our delimiter character. We have
also used the `-f` option to specify that we want to extract the second
field (column). This gives the following output:

``` output
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
```

The `uniq` command filters out adjacent matching lines in a file. How
could you extend this pipeline (using `uniq` and another command) to
find out what animals the file contains (without any duplicates in their
names)?
:::

------------------------------------------------------------------------

::: challenge
## Which Pipe?

The file `animals.csv` contains 8 lines of data formatted as follows:

``` output
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
...
```

The `uniq` command has a `-c` option which gives a count of the number
of times a line occurs in its input. Assuming your current directory is
`shell-lesson-data/exercise-data/animal-counts`, what command would you
use to produce a table that shows the total count of each type of animal
in the file?

1.  `sort animals.csv | uniq -c`
2.  `sort -t, -k2,2 animals.csv | uniq -c`
3.  `cut -d, -f 2 animals.csv | uniq -c`
4.  `cut -d, -f 2 animals.csv | sort | uniq -c`
5.  `cut -d, -f 2 animals.csv | sort | uniq -c | wc -l`
:::

------------------------------------------------------------------------

::: challenge
## Removing Unneeded Files

Suppose you want to delete your processed data files, and only keep your
raw files and processing script to save storage. The raw files end in
`.dat` and the processed files end in `.txt`. Which of the following
would remove all the processed data files, and *only* the processed data
files?

1.  `rm ?.txt`
2.  `rm *.txt`
3.  `rm * .txt`
4.  `rm *.*`
:::

------------------------------------------------------------------------


# Loops

------------------------------------------------------------------------

![](fig/shell_script_for_loop_flow_chart.svg){alt="The for loop \"for filename in .dat; do echo cp $filename original-$filename;done\" will successively assign the names of all \".dat\" files in your currentdirectory to the variable \"$filename\" and then execute the command. With thefiles \"basilisk.dat\", \"minotaur.dat\" and \"unicorn.dat\" in the current directorythe loop will successively call the echo command three times and print threelines: \"cp basislisk.dat original-basilisk.dat\", then \"cp minotaur.datoriginal-minotaur.dat\" and finally \"cp unicorn.datoriginal-unicorn.dat\""}

------------------------------------------------------------------------

::: challenge
## Write your own loop

How would you write a loop that echoes all 10 numbers from 0 to 9?
:::

------------------------------------------------------------------------

::: challenge
## Variables in Loops

This exercise refers to the `shell-lesson-data/exercise-data/alkanes`
directory. `ls *.pdb` gives the following output:

``` output
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
```

What is the output of the following code?

``` bash
$ for datafile in *.pdb
> do
>     ls *.pdb
> done
```

Now, what is the output of the following code?

``` bash
$ for datafile in *.pdb
> do
>     ls $datafile
> done
```

Why do these two loops give different outputs?
:::

------------------------------------------------------------------------

::: challenge
## Limiting Sets of Files

What would be the output of running the following loop in the
`shell-lesson-data/exercise-data/alkanes` directory?

``` bash
$ for filename in c*
> do
>     ls $filename
> done
```

1.  No files are listed.
2.  All files are listed.
3.  Only `cubane.pdb`, `octane.pdb` and `pentane.pdb` are listed.
4.  Only `cubane.pdb` is listed.

How would the output differ from using this command instead?

``` bash
$ for filename in *c*
> do
>     ls $filename
> done
```

1.  The same files would be listed.
2.  All the files are listed this time.
3.  No files are listed this time.
4.  The files `cubane.pdb` and `octane.pdb` will be listed.
5.  Only the file `octane.pdb` will be listed.
:::

------------------------------------------------------------------------
https://swcarpentry.github.io/shell-novice/06-script.html
------------------------------------------------------------------------

::: challenge
## Doing a Dry Run

A loop is a way to do many things at once --- or to make many mistakes
at once if it does the wrong thing. One way to check what a loop *would*
do is to `echo` the commands it would run instead of actually running
them.

Suppose we want to preview the commands the following loop will execute
without actually running those commands:

``` bash
$ for datafile in *.pdb
> do
>     cat $datafile >> all.pdb
> done
```

What is the difference between the two loops below, and which one would
we want to run?

``` bash
# Version 1
$ for datafile in *.pdb
> do
>     echo cat $datafile >> all.pdb
> done
```

``` bash
# Version 2
$ for datafile in *.pdb
> do
>     echo "cat $datafile >> all.pdb"
> done
```
:::

------------------------------------------------------------------------

::: challenge
## Nested Loops

Suppose we want to set up a directory structure to organize some
experiments measuring reaction rate constants with different compounds
*and* different temperatures. What would be the result of the following
code:

``` bash
$ for species in cubane ethane methane
> do
>     for temperature in 25 30 37 40
>     do
>         mkdir $species-$temperature
>     done
> done
```
:::

------------------------------------------------------------------------


# Shell Scripts

------------------------------------------------------------------------

::: challenge
## List Unique Species

Leah has several hundred data files, each of which is formatted like
this:

``` source
2013-11-05,deer,5
2013-11-05,rabbit,22
2013-11-05,raccoon,7
2013-11-06,rabbit,19
2013-11-06,deer,2
2013-11-06,fox,1
2013-11-07,rabbit,18
2013-11-07,bear,1
```

An example of this type of file is given in
`shell-lesson-data/exercise-data/animal-counts/animals.csv`.

We can use the command `cut -d , -f 2 animals.csv | sort | uniq` to
produce the unique species in `animals.csv`. In order to avoid having to
type out this series of commands every time, a scientist may choose to
write a shell script instead.

Write a shell script called `species.sh` that takes any number of
filenames as command-line arguments and uses a variation of the above
command to print a list of the unique species appearing in each of those
files separately.
:::

------------------------------------------------------------------------

::: challenge
## Why Record Commands in the History Before Running Them?

If you run the command:

``` bash
$ history | tail -n 5 > recent.sh
```

the last command in the file is the `history` command itself, i.e., the
shell has added `history` to the command log before actually running it.
In fact, the shell *always* adds commands to the log before running
them. Why do you think it does this?
:::

------------------------------------------------------------------------

::: challenge
## Variables in Shell Scripts

In the `alkanes` directory, imagine you have a shell script called
`script.sh` containing the following commands:

``` bash
head -n $2 $1
tail -n $3 $1
```

While you are in the `alkanes` directory, you type the following
command:

``` bash
$ bash script.sh '*.pdb' 1 1
```

Which of the following outputs would you expect to see?

1.  All of the lines between the first and the last lines of each file
    ending in `.pdb` in the `alkanes` directory
2.  The first and the last line of each file ending in `.pdb` in the
    `alkanes` directory
3.  The first and the last line of each file in the `alkanes` directory
4.  An error because of the quotes around `*.pdb`
:::

------------------------------------------------------------------------

::: challenge
## Find the Longest File With a Given Extension

Write a shell script called `longest.sh` that takes the name of a
directory and a filename extension as its arguments, and prints out the
name of the file with the most lines in that directory with that
extension. For example:

``` bash
$ bash longest.sh shell-lesson-data/exercise-data/alkanes pdb
```

would print the name of the `.pdb` file in
`shell-lesson-data/exercise-data/alkanes` that has the most lines.

Feel free to test your script on another directory e.g.

``` bash
$ bash longest.sh shell-lesson-data/exercise-data/writing txt
```
:::

------------------------------------------------------------------------

::: challenge
## Script Reading Comprehension

For this question, consider the
`shell-lesson-data/exercise-data/alkanes` directory once again. This
contains a number of `.pdb` files in addition to any other files you may
have created. Explain what each of the following three scripts would do
when run as `bash script1.sh *.pdb`, `bash script2.sh *.pdb`, and
`bash script3.sh *.pdb` respectively.

``` bash
# Script 1
echo *.*
```

``` bash
# Script 2
for filename in $1 $2 $3
do
    cat $filename
done
```

``` bash
# Script 3
echo $@.pdb
```
:::

------------------------------------------------------------------------

::: challenge
## Debugging Scripts

Suppose you have saved the following script in a file called
`do-errors.sh` in Nelle's `north-pacific-gyre` directory:

``` bash
# Calculate stats for data files.
for datafile in "$@"
do
    echo $datfile
    bash goostats.sh $datafile stats-$datafile
done
```

When you run it from the `north-pacific-gyre` directory:

``` bash
$ bash do-errors.sh NENE*A.txt NENE*B.txt
```

the output is blank. To figure out why, re-run the script using the `-x`
option:

``` bash
$ bash -x do-errors.sh NENE*A.txt NENE*B.txt
```

What is the output showing you? Which line is responsible for the error?
:::

------------------------------------------------------------------------


# Finding Things

------------------------------------------------------------------------

::: challenge
## Using `grep`

Which command would result in the following output:

``` output
and the presence of absence:
```

1.  `grep "of" haiku.txt`
2.  `grep -E "of" haiku.txt`
3.  `grep -w "of" haiku.txt`
4.  `grep -i "of" haiku.txt`
:::

------------------------------------------------------------------------

::: challenge
## Tracking a Species

Leah has several hundred data files saved in one directory, each of
which is formatted like this:

``` source
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
2012-11-06,deer,2
2012-11-06,fox,4
2012-11-07,rabbit,16
2012-11-07,bear,1
```

She wants to write a shell script that takes a species as the first
command-line argument and a directory as the second argument. The script
should return one file called `<species>.txt` containing a list of dates
and the number of that species seen on each date. For example using the
data shown above, `rabbit.txt` would contain:

``` source
2012-11-05,22
2012-11-06,19
2012-11-07,16
```

Below, each line contains an individual command, or pipe. Arrange their
sequence in one command in order to achieve Leah's goal:

``` bash
cut -d : -f 2
>
|
grep -w $1 -r $2
|
$1.txt
cut -d , -f 1,3
```

Hint: use `man grep` to look for how to grep text recursively in a
directory and `man cut` to select more than one field in a line.

An example of such a file is provided in
`shell-lesson-data/exercise-data/animal-counts/animals.csv`
:::

------------------------------------------------------------------------

::: challenge
## Little Women

You and your friend, having just finished reading *Little Women* by
Louisa May Alcott, are in an argument. Of the four sisters in the book,
Jo, Meg, Beth, and Amy, your friend thinks that Jo was the most
mentioned. You, however, are certain it was Amy. Luckily, you have a
file `LittleWomen.txt` containing the full text of the novel
(`shell-lesson-data/exercise-data/writing/LittleWomen.txt`). Using a
`for` loop, how would you tabulate the number of times each of the four
sisters is mentioned?

Hint: one solution might employ the commands `grep` and `wc` and a `|`,
while another might utilize `grep` options. There is often more than one
way to solve a programming task, so a particular solution is usually
chosen based on a combination of yielding the correct result, elegance,
readability, and speed.
:::

------------------------------------------------------------------------

::: challenge
## Matching and Subtracting

The `-v` option to `grep` inverts pattern matching, so that only lines
which do *not* match the pattern are printed. Given that, which of the
following commands will find all .dat files in `creatures` except
`unicorn.dat`? Once you have thought about your answer, you can test the
commands in the `shell-lesson-data/exercise-data` directory.

1.  `find creatures -name "*.dat" | grep -v unicorn`
2.  `find creatures -name *.dat | grep -v unicorn`
3.  `grep -v "unicorn" $(find creatures -name "*.dat")`
4.  None of the above.
:::

------------------------------------------------------------------------

::: challenge
## `find` Pipeline Reading Comprehension

Write a short explanatory comment for the following shell script:

``` bash
wc -l $(find . -name "*.dat") | sort -n
```
:::

------------------------------------------------------------------------


