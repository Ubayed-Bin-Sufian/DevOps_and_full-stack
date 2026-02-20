# Linux Commads

## Basic commands

`echo "Hello World"` (Outputs Hello World) <br>
`sudo` (Allows you to run commands with superuser privileges; sudo: superuser do) <br>
`whoami` (Displays the current user) <br>
`sudo whoami` (Displays the current user with superuser privileges) <br>
`history` (Shows command history) <br>
`clear` & `Ctrl + L` (Clears the terminal screen) <br>
`pwd` (Prints the current working directory; pwd: print working directory) <br>
`ls` (Lists files and directories in the current directory) <br>
`ls /` (Lists files and directories in the root directory) <br>
`cd <directory>` (Changes the current directory to the specified directory) <br>
`cd ..` (Moves up one directory level) <br>
`cd ~` (Moves to the home directory) <br>
`cat <file>` (Displays the contents of a file) <br>
`head -n <file>` (Displays the first n lines of a file) <br>
`tail -n <file>` (Displays the last n lines of a file) <br
`cd ../..` (Moves up two directory levels) <br>
`command1; command2` (Executes command1 and then command2) <br>
`command1 && command2` (Executes command2 only if command1 is successful) <br>
`less <file>` (Allows you to view the contents of a file one page at a time) <br>
`less -N <file>` (Displays line numbers. Use the arrow keys to scroll line by line, Spacebar to move forward one page, 'b' to go back one page, and q to quit.) <br>
`touch <file>` (Creates an empty file or updates the timestamp of an existing file) <br>
`touch <file1> <file2> <file3>` (Creates multiple empty files) <br>
`mkdir <directory>` (Creates a new directory) <br>
`mv <old_file> <new_file>` (Renames a file) <br>
`mv <file> <directory>` (Moves a file to a different directory) <br>
`mv <file> ~` (moves from current directory to the home directory) <br>
`mv <file> <directory>/<new_file_name>` (Moves a file to a different directory and renames it if necessary) <br>
`rm <file>` (Deletes a file) <br>
`rm -r <directory>` (Deletes a directory and its contents recursively) <br>
`cp <source_file> <destination_file>` (Copies a file) <br>
`cp -R <source_directory> <destination_directory>` (Copies a directory and its contents recursively; in Linux both -r and -R will work) <br>
`grep <pattern> <file>` (Searches for a specific pattern in a file and displays the matching lines; global regular expression print) <br>
`grep <pattern> <file1> <file2>` (Searches for a specific pattern in multiple files and displays the matching lines) <br>
`grep -r <pattern> .` (Searches for a specific pattern in all files within the current directory and its subdirectories recursively) <br>
`grep -r <pattern> /path/to/directory` (Searches for a specific pattern in all files within the specified directory and its subdirectories recursively) <br>
`find <directory> -name <file_name>` (Searches for a specific file name within the specified directory and its subdirectories) <br>
`find <directory> -name <"pattern">` (Searches for files and directories that match a specific pattern eg: files ending with .txt within the specified directory and its subdirectories) <br>
`find <directory> -name <"*pattern*">` (Searches for files and directories that match a specific pattern with wildcards within the specified directory and its subdirectories) <br>

## Tips and Tricks

- Use `Tab` for auto-completion of commands and file names.

## Glossary 

- **Terminal**: A text-based interface used to interact with the operating system.
- **Shell**: A program that interprets commands and acts as an intermediary between the user and the operating system.
- **REPL**: Read-Eval-Print-Loop, an interactive programming environment that takes user inputs, evaluates them, and returns the result.
- **variables**: Named storage locations in memory that hold data values.
- **file**: A dump of raw binary data: 1's and 0's. The bytes in a file can represent anything: text, images, videos, etc.
- **directory**: A folder in a file system that contains files and other directories.
- **root directory**: The top-level directory in a file system hierarchy, denoted by a forward slash (/).
- **home directory**: The default directory assigned to a user for storing personal files, typically located at /home/username.
- **relative path**: A file or directory path that is specified in relation to the current working directory.
- **absolute path**: A complete file or directory path that starts from the root directory and specifies the full location of a file or directory.