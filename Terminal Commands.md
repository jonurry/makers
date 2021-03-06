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

## Word Count
`wc [-clmw] [file ...]`

The wc utility displays the number of lines, words, and bytes contained in each input file, or standard input (if no file is specified) to the standard output.

e.g. `find ~ -name "*.txt" -print | grep README | wc -l` will find all of the .txt files from the home diroctory containing the word _README_ and display the number of lines in which that word occurs.

## Permissions
Every file and folder has permissions. Permissions are split into 3 classes (user, group and other). These are further subdivided into 3 permissions (read, write, execute).
### User
The owner of the file or folder. There can be only one owner. If the user accessing the file or folder is the owner then user permissions apply.
#### whoami
Too find out which user you are use `whoami`
### Group
Each user belongs to one or more groups. If the user accessing the file or folder belongs to a group then these permissions apply.
### Other
This class applies to all users that are not the owner or belong to a group.
### Determine permissions
`ls -l' will list the files in long format and show the permissions.
### Understanding Permission Syntax
File and folder permissions are broken down as follows using a 10 character representation:
1. the type of file '-' for files, 'd' for directories
2. read access for the user class, 'r' read access, '-' no access
3. write access for the user class, 'w' read access, '-' no access
4. execute access for the user class, 'x' read access, '-' no access
5. read access for the group class, 'r' read access, '-' no access
6. write access for the group class, 'w' read access, '-' no access
7. execute access for the group class, 'x' read access, '-' no access
8. read access for the user other, 'r' read access, '-' no access
9. write access for the user other, 'w' read access, '-' no access
10. execute access for the user other, 'x' read access, '-' no access

e.g. `-r-x-r--r--` the file can be read and execured by the owner, and read buy members of a group or others.

e.g. `drw-------` the directory can be read and changed by the owner but no other user has any access at all.

### Changing Permissions
Use the `chmod` command to alter permissions.

e.g. `chmod u+w readme.txt` give the user a write permission on a file "readme.txt"

Here, "u" stands for user ("g" for group, "o" for others and "a" for all), "+" means that we're adding the permission ("-" means we're removing it) and "w" stands for "write". You can combine several permissions.

e.g. `chmod a-rx readme.txt` to remove read and execute permissions from all users.

## Which
Finds the location of a program in the user's path

e.g. `which ruby` will show the path to the ruby program executable

## Shebang #!
A shebang is located in the first line of a file and instructs the command line as to which program should be used to execute the contents of the file. e.g.

```ruby
#!/usr/bin/env ruby
puts "Hello, World!"
```

tells the command line to find the ruby program from the environment and use it to execute the rest of the file's contents.

## Superuser Mode
Allows any command to be executed as the root user. The root user has access to everything and do anything. Execute any command as root by typing `sudo` before the commmand. You will need to know the root (administrator) password.

e.g. `sudo rm inaccessibleFile` remove an inaacessible file that you don't have permission to access.

## Environment
The enviromnent stores key/value pairs that describe the environment that programs run in. e.g. there's environment variables for the home directory and the temporary directory.

`env` lists all environment variables and their values

`$ echo $HOME` shows the location of the home directory

`$ echo $TMPDIR` shows the location of the temporary directory

Environment variables created in this way are only available for the lifetime of the current shell console. They will be deleted when the shell closes and are not available to other concurrent shell instances.

### Echo
The `echo` command prints its input to the screen

e.g. `echo "Hi, there!"` prints "Hi, there!" to the output stream (screen by default)

The output stream can be redirected to a file, for example, to save text to a file:

`echo "save me to a file" > echoText.txt`

### PATH
PATH is an environment variable. It contains a colon-separated list of directories where the shell will be looking for the programs you ask it to run. To see the contents of the PATH:

`echo $PATH`

When you run a program from the command line the shell will look for the program's executable file in each directory specified in the PATH in turn until it finds it. If it doesn't, `command not found` will be returned.

When switching ruby versions using `rvm` it updates the PATH and changes the names of the ruby directories to be those for the specified version. e.g. `rvm use 1.9.3`.

### Setting environment variables
Create a new environment variable by using the `export` command:

e.g. `export SEASON=Winter`

Add a path to the PATH environment variable:

`export PATH=$PATH:/Users/jon`

Store a private key used by an open source code module so that the code can be freely shared without compromising your private password/key:

`export SECRET_KEY=12345abcde`

Then, in your Ruby code, read the value:

`secret_key = ENV['SECRET_KEY']`

### Profiles
Profiles are loaded whenever a shell is loaded. They contain configurations that are applied to the shell. You can alter the profiles to create permemant environment variables that are loaded into every shell instance. You can edit the _.bash_profile_ in the user's home directory:

e.g. `echo "export SEASON=winter" >> ~/.bash_profile` will add the SEASON environment variable to the end of the bash profile file.

_Note:_ `>>` means append to the end of the file, `>` means overwrite the contents of the file.

### Processes
`ps` to see the running processes in the shell

`ps x` to see all of the running processes on the computer

`ps x | grep process_name` to filter the list of running processes to a particular application or process name

`ps x | grep process_name | wc -l` to count the number of filtered processes

