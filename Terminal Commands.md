# Terminal Commands
## Date
`date` Shows the current date, time and time zone

e.g. `Tue  7 Aug 2018 13:55:06 BST`

## List Files
`ls` Lists all the folders and files in the current directory.

## Change Directory
`cd` Change directory (or folder)

`cd ..` Change to the parent directory

`cd directory_name` e.g. `cd Documents` Changes to the Documents directory

## Print Working Directory
`pwd` Shows the full path of the directory that we are currently working in

## Listing hidden files (using switches)
`ls -lA` List all files including hidden ones

Switches can be applied one by one or combined

`ls -l` list files in long format (incl. size, creation date, owner, etc)

`ls -A` list all files (incl. hidden)

`ls -lA` list all files incl. hidden in long format

`ls -Al` list all files incl. hidden in long format

## Creating Files
`touch file_name` create a new empty file in the current directory with the name *file_name*

e.g. `touch worksheet` creates a file called _worksheet_ in the current directory

## Removing Files
`rm file_name` remove file in the current directory with the name *file_name*

e.g. `rm worksheet` removes a file called _worksheet_ in the current directory

_Note:_ it is difficult to restore files that have been removed using `rm`

### Removing files interactive
`rm -i` removes files in the current directory but prompts the user as to whether they want to delete each file in turn. Useful if you only want to keep a few files but delete others.

### Removing files forcefully
`rm -f` will forcefully remove a file even if it protected.

## Create Directory
`mkdir directory_name` make (or create) a directory with the name *directory_name* in the current working directory

e.g. `mkdir Example`

## Remove Directory
`rmdir directory_name` removes (or deletes) a directory with the name *directory_name* from the current working directory

e.g. `rmdir Example`

_Note:_ Only works with empty directories

### Remove directory and all files within
`rm -r directory_name` removes (or deletes) a directory with the name *directory_name* from the current working directory as well as all of the files and folders within that directory, recursively. The `-r` switch indicates the recursive operation. 

e.g. `rm -r SomeDir`

## Copy File
`cp [path_1/]file_1 [path_2/]file_2` makes a copy of _file_1_ and names it _file_2_ (paths are optional, if omitted assume same directory)

## Move File
`mv [path_1/]file_1 [path_2/]file_2` moves _file_1_ and names it _file_2_ (paths are optional, if omitted assume same directory)

### Rename File
Using the move file command `mv` we can rename a file by simply using a different file name

e.g. `mv [path/]file_1 [path/]file_2` renames file_1 as file_2

## Concatenate
### View file contents
`cat file` view the contents of file

e.g. `cat readme.txt`

### Insert text into file
`cat > someMoreText` opens a text prompt where whatever the user types is stored in the file _someMoreText_. Exit using `ctrl-c`.

### Merge contents of files
`cat file_1 file_2 > merged_file` merge the contents of _file_1_ with _file_2_ and store it in _merged_file_

## View Contents of long files
### less
`less file` Using the "less" command, you're able to scroll up and down with your keyboard to view the entire document. When you're ready to finish viewing, just type "q"

e.g. `less longText.txt` view the contents of _longText.txt_

### head
`head [-n] file` view the first 'n' lines of _file_. 'n' is a positive integer. If omitted, defaults to first 10 lines.

e.g. `head -3 longText.txt` show the first 3 lines of the contents of _longText.txt_.

### tail
`tail [-n] file` view the last 'n' lines of _file_. 'n' is a positive integer. If omitted, defaults to last 10 lines.

e.g. `tail -3 longText.txt` show the last 3 lines of the contents of _longText.txt_.

### Monitor log files
`tail -f file.log` Show the last 10 entries in the log file and then monitor for new entries. As soon as the log file is updated the entry will appear in the console. Ctrl-C to stop monitoring.

e.g. `tail -f /private/var/log/system.log` to montor the OS X system log.

