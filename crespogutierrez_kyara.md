# **February 6th, 2026**

## Tab key will fill out command automatically with the information provided#
E.g. "cd g [press tab]" will fill out automatically with "cd gen711-811"

## pwd = print working directory, aka a folder#
"/home/users/kac1224/gen711-811" means that pwd gen711 is inside pwd kac, which is insie pwd users, inside pwd home.

## ls = list
+ Lists pwd's and files within current pwd.
+ ls -F = gives out empty pwd's.
+ man ls = pulls out entire ls manual, but google might be better to find specific commands.
+ ls *[wanted search] = lists results that contain wanted search at the *end* **ONLY**.
+ ls [wanted search]* =lists results that contain wanted search at the *beginning* **ONLY**.

## ctrl z = cancels command, does not undo

## clear = deletes all previous commands

## cd "directory" = opens wanted directory
+ E.g. cd gen711-811, cd shell_data, cd $HOME
+ cd ../ = gets you out of a directory, adding more ../ will bring you to the next outer directory
+ cd ~ = brings you to home directory

## head + file = opens up only the first few lines of the file

## grep + '[wanted search]' = looks up wanted search among the entire pwd you are currently in
+ Sort of like a ctrl+F, but for coding
+ E.g. grep '@' will look for any "at symbols"
+ Adding "^" before the wanted search will give out results with the wanted search at the beginning of the line **ONLY**.

## [command] | wc -l = counts the number of lines brought up by the command
+ wc (without -l) will give out: lines, words, characters

## [command] > file-[name] = will pull up results from command into a new file