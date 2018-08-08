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

## Getting Help
`man command` The `man` or 'manual' command takes a parameter of another command to provide you more information about it.

e.g. `man less` show information about the `less` command and how to use it.

## Streams, Pipes and Redirection
### Streams
Every program on your computer has at least three "standard streams" associated with it. Streams are just channels used to connect the input and the output of the program to the environment (usually the terminal). The keyboard is referred to as an input stream. By reading from the input stream your program can read what you have typed on the keyboard. The screen is referred to as an output stream. By sending data to the output stream, a program can print something on the screen. There is also an error stream that is usually sent to the display as well but is used only to print error messages.

The input stream is usually called stdin and has number 0. The output stream is stdout (#1) and the error stream is called stderr (#2).

### Pipes
Pipes allow you to redirect streams. For example:

`cat file | less` feed the output stream of `cat file` (the contents of _file_) to the imput stream of `less` so that you can navigate the contents of _file_ using the `less` capabilities.

`ls -lA | less` move up and down the list of files and folders as if the output were a normal file.

### Redirection
We can redirect the output stream of a command to a file. Consider this example.

`cat file_1 > file_2` The greater-than symbol writes the output stream of the command on the left to the file on the right. If the file on the right doesn't exist it is created, If it does exisit, it is overwritten.

## Wildcards
All terminal commands accept wildcards. '*' means any.

`ls *.txt` lists all files with the extension 'txt'

## Find Files
`find . -name "*.txt" -print` find all files, starting with the current directory, with any name that ends in .txt and print it to the screen.

Another cool feature of the "find" command is that, if you have additional directories inside the directory you search in, it will go into those directories as well and continue the search. Therefore, this is how we'd print out every text file in our home directory:

`cd ~`

`find . -name "*.txt" -print`

The first command you already know - to change directories into your home directory. The second command is just using the find command again to tell it to go through and print all text files in the Home directory, plus any other directories inside your home directory.

`cd ~/Music`

`find . -name *.mp3 -print > myMusic.txt`

creates a text document _myMusic.txt_ that lists out every mp3 file in your Music directory.

## Grep
Grep allows us to search inside a file's content.

`grep word files` Grep takes 2 parameters, the word that you are searching for and the file(s) to search in.

e.g. `grep binary *.txt` lists all files (with extension '.txt') that contain the word _binary_ along with an extract containing the word.

e.g. `find ~ -name "*.txt" -print | grep README` This command will find all 'txt' files form the home directory but instead of printing them, all filenames will be redirected to grep. Grep, in turn, will only print those filenames that include "readme".

Grep actually takes a regular expression as the first parameter to search for. [RegExr](http://regexr.com/) is a great tool to use for regular expressions.

