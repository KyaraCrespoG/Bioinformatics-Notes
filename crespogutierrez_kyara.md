# **February 6th, 2026**

## Tab key will fill out command automatically with the information provided
E.g. "cd g [press tab]" will fill out automatically with "cd gen711-811"

## pwd = print working directory, aka a folder
"/home/users/kac1224/gen711-811" means that pwd gen711 is inside pwd kac, which is inside pwd users, inside pwd home.

## ls = list
+ Lists pwd's and files within current pwd.
+ ls -F = gives out empty pwd's.
+ man ls = pulls out entire ls manual, but google might be better to find specific commands.
+ ls *[wanted search] = lists results that contain wanted search at the *end* **ONLY**.
+ ls [wanted search]* = lists results that contain wanted search at the *beginning* **ONLY**.
+ ls -l = lists files within directory, shows file size, creation date and time, and file titles.

## ctrl z = cancels command, does not undo

## clear = deletes all previous commands

## cd "directory" = opens wanted directory
+ E.g. cd gen711-811, cd shell_data, cd $HOME
+ cd ../ = gets you out of a directory, adding more ../ will bring you to the next outer directory
+ cd ~ = brings you to home directory

## head + file = opens up only the first few lines of the file
+ head -n[number of lines you want to display] + file = will print out the first, asked number of lines

## grep + [wanted search] = looks up wanted search among the entire pwd you are currently in
+ Sort of like a ctrl+F, but for coding
+ E.g. grep '@' will look for any "at symbols"
+ Adding "^" before the wanted search will give out results with the wanted search at the beginning of the line **ONLY**.
+ grep -B[number] -A[number] [wanted search] + [file] = looks up wanted serach within file, and displays the [number] of line Before and After the wanted search.
+ grep -v [unwanted characters] + [file] = prints out the lines within the file that do **NOT** contain the unwanted characters. called "reverse grep"

## [command] | wc -l = counts the number of lines brought up by the command
+ wc (without -l) will give out: lines, words, characters

## [command] > [file name] = will pull up results from command into a new file

# **February 13th, 2026**
## Hidden files and directories start with . and can be viewed using ls -a.
## The commands with "*" are using a "wildcard"
## cp [file from which you're copying] [new file to which you're copying to] = copies file's contents into a new file, aka makes a copy

# **February 20th, 2026**
## chmod -w [file you want to change permissions on] = removes writing permission from a file
+ chmod ug+rwx [file] = grants reading, writing, and executing permissions to the user and the group.

## rm = remove

## mv [file old name] [file new name] = rename a file

#### **conda activate genomics = allows anaconda to work in bash for certain genomics programs**
#### **conda deactivate = leaves anaconda environment**

# **February 27th, 2026**

## less = displays entire file on the screen

## Keypoints
- `grep` is a powerful search tool with many options for customization.
- `>`, `>>`, and `|` are different ways of redirecting output.
- `command > file` redirects a command's output to a file.
- `command >> file` redirects a command's output to a file without overwriting the existing contents of the file. (adds the command to the existing file, combining them)
- `command_1 | command_2` redirects the output of the first command as input to the second command.
- `for` loops are used for iteration.
- `basename` gets rid of repetitive parts of names.

## For loops basic structure:
- for
- do
- done

# **March 6th, 2026**
## For metadata, do not use special characters, spaces (use underscores instead), or tabs. Especially no commas since these are used to delineate what is part of each column in a csv file.
- Metadata are tables with every sample in an experiment, and every identifier or conditions or file, etc.

## wget [link] = pulls data from online link into new file
## uniq = removes any adjacent, repeated values
- add sort | uniq to remove repeated values everywhere in your data, not just adjacent, identical values.
- uniq -c will tell you how many duplicates there are of any given value.
## cut -f[column number] -d[column ending indicator] =  prints only the desired column, indicated by the column ending symbol (such as comma in csv)
## tr ',' '\n' = makes every comma into a new line, used for csv for example

# Examples
1. How many different generations exist in the data? 

KCG: cut -f2 -d',' ecoli_metadata_composite.csv | sort | uniq | grep -v 'gen' | wc -l for 25 generations

- only show the second column, which you identify using the commas to know where each column ends, of the file; sort the values; collapse any repeated values so I only see each one represented once; do not show the column header "generation"; count the number of lines.

2. How many rows and how many columns are in this data? 

KCG: head -n1 ecoli_metadata_composite.csv | tr ',' '\n' | wc -l for 12 columns, and grep -v '^strain' ecoli_metadata_composite.csv | wc -l for 62 rows

- only show the first row of the file; convert any comma you find into a new line; count the number of lines. show me everything on the file whose line does not start with "strain"; count the lines.

3. How many citrate+ mutants have been recorded in **Ara-3**?

KCG: cut -f12 -d',' ecoli_metadata_composite.csv | sort | uniq -c | grep 'plus'  
     10 plus

- only show the twelfth column, which you identify using the commas to know where each column ends, of the file; sort the values; collapse any repeated values so I only see each one represented once, and show me how many instances of each value there are; show me only the data that includes "plus".

4. How many hypermutable mutants have been recorded in **Ara-3**?

KCG: cut -f6 -d',' ecoli_metadata_composite.csv | sort | uniq -c | grep 'plus'  
      6 plus

- only show the sixth column, which you identify using the commas to know where each column ends, of the file; sort the values; collapse any repeated values so I only see each one represented once, and show me how many instances of each value there are; show me only the data that includes "plus".