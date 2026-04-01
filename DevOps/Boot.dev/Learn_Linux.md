# Linux Commads

## Basic commands

`echo "Hello World"` (Outputs Hello World) <br>
`echo $PATH` (Displays the value of the PATH environment variable, which is a list of directories that the shell searches for executable files) <br>
`echo $?` (Displays the exit status of the last executed command) <br>
`sudo` (Allows you to run commands with superuser privileges; sudo: superuser do. It is used when the user is not the owner of the file or dir.) <br>
`whoami` (Displays the current user) <br>
`sudo whoami` (Displays the current user with superuser privileges) <br>
`history` (Shows command history) <br>
`clear` & `Ctrl + L` (Clears the terminal screen) <br>
`pwd` (Prints the current working directory; pwd: print working directory) <br>
`ls` (Lists files and directories in the current directory) <br>
`ls /` (Lists files and directories in the root directory) <br>
`ls -l` (Lists files and directories in long format, showing permissions, ownership, size, and modification date) <br>
`ls -a ~` (Lists all files and directories in the home directory, including hidden ones that start with a dot) <br>
`cd <directory>` (Changes the current directory to the specified directory) <br>
`cd ..` (Moves up one directory level) <br>
`cd ~` (Moves to the home directory) <br>
`cat <file>` (Displays the contents of a file) <br>
`head -n <file>` (Displays the first n lines of a file) <br>
`tail -n <file>` (Displays the last n lines of a file) <br>
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
`grep -R <pattern> --exclude-dir=<dir_name>` (Searches for a specific pattern in all files within the specified directory and its subdirectories recursively, excluding the specified directory) <br>
`find <directory> -name <file_name>` (Searches for a specific file name within the specified directory and its subdirectories) <br>
`find <directory> -name <"pattern">` (Searches for files and directories that match a specific pattern eg: files ending with .txt within the specified directory and its subdirectories) <br>
`find <directory> -name <"*pattern*">` (Searches for files and directories that match a specific pattern with wildcards within the specified directory and its subdirectories) <br>
`chmod -R <permissions> <directory>` (Changes the permissions of a directory and all its contents recursively; [chmod](https://www.ibm.com/docs/en/aix/7.3.0?topic=c-chmod-command): change mode) <br>
`sudo chown -R <user>:<group> <directory>` (Changes the ownership of a directory and all its contents recursively; [chown](https://www.ibm.com/docs/en/aix/7.3.0?topic=c-chown-command): change owner) <br> 
`which <command>` (Shows the full path of a command) <br>
`#! interpreter [optional-arg]` (Shebang line used at the beginning of a script to specify the interpreter to be used for executing the script) <br>
`env` (Displays the current environment variables) <br>
`export <VAR_NAME>=<value>` (Sets an environment variable) <br>
`unset <VAR_NAME>` (Unsets an environment variable) or `export <VAR_NAME>=""` <br>
`export PATH="$PATH:/path/to/new"` (Adds a new directory to the PATH environment variable where `$PATH` part is a reference to the existing `PATH` variable, `:` separates the existing directories from the new directory that we are adding, and `/path/to/new` is the new directory to add) **NOTE:** This works for the current terminal session, but if you want to make it permanent, you need to add it to your shell's configuration file (e.g., `~/.bashrc` or `~/.zshrc`) <br>
`man <command>` (Displays the manual page for a command, providing detailed information about its usage, options, and examples; reference: [man](https://www.ibm.com/docs/en/aix/7.3.0?topic=m-man-command)) <br>
`man ls` (Displays the manual page for the `ls` command) **NOTE:** You can search for specific keywords within the manual page by pressing `/` followed by the keyword and pressing `Enter`. Use `n` to go to the next occurrence and `N` to go to the previous occurrence. Press `q` to exit the manual page. <br>
`wc <file>` (Counts the number of lines, words, and characters in a file; word count) <br>
`--help / -h` (Displays a brief help message for a command, showing its usage and available options) <br>
`kill <PID>` (Terminates a process with the specified Process ID; reference: [kill](https://www.ibm.com/docs/en/aix/7.3.0?topic=k-kill-command)) <br>
`ps aux` (Displays a detailed list of all running processes, including their Process IDs, resource usage, and other information; ps: process status, a: all users, u: user-oriented format, x: processes without a terminal; reference: [ps command](https://www.ibm.com/docs/en/zos/3.2.0?topic=jobs-using-ps-command)) <br>
`ps aux | grep <process_name>` (Filters the list of running processes to show only those that match the specified process name) <br>
`ps aux | head -n 5` (Displays only the first 5 lines of the list of running processes) <br>
`top` (Displays a real-time, dynamic view of the system's resource usage, including CPU and memory usage, as well as a list of running processes; reference: [top command](https://man7.org/linux/man-pages/man1/top.1.html)) Press M to sort by memory usage <br>

### Permissions

The permissions of an individual file or directory are visually represented as a 10-character string:
```
drwxrwxrwx
```

The first one just tells you whether you're looking at a file or a directory:
-  -: Regular file (e.g. `-rwxrwxrwx`)
-   d: Directory (e.g. `drwxrwxrwx`)

The next 9 characters are broken up into 3 sets of rwx and represent the permissions themselves for the "owner", "group", and "others", in order. 

- r: read permission (allows you to read the contents of the file or list (`ls`) the contents of a directory)
- w: write permission (allows you to modify the contents of the file or add/remove files in a directory)
- x: execute permission (allows you to run the file as a program or access a directory and its contents (`cd` into it))
- The first 3 characters are **"owner"** permissions. The "owner" is usually just the user who created the file or directory, but it can be manually changed.
- The next 3 characters are **"group"** permissions. A "group" is a collection of users that can be assigned permissions to files and directories. A user can belong to multiple groups, and a file or directory can have permissions assigned to multiple groups.
- The last 3 characters are **"others"** permissions. "Others" refers to all users who are not the owner and do not belong to the group associated with the file or directory

Here are some full examples:

- `rwxrwxrwx`: A file where everyone can do everything
- `rwxr-xr-x`: A file where everyone can read and execute, but only the owner can write
- `drwxr-xr-x`: A directory where everyone can read (ls the contents) and execute (cd into it), but only the owner can write (modify the contents)
- `drwx------`: A directory where only the owner can read, write and execute


### Unix Philosophy

The Unix Philosophy is a simple set of principles that have guided the development of Unix-like operating systems for decades. It can be summarized as:

1. Write programs that do one thing and do it well. eg: `ls` is a program that lists files and directories, while `grep` is a program that searches for patterns in text. 
2. Write programs to work together.Eg: You can use pipes (`|`) to connect the output of one program to the input of another program, allowing you to create powerful command combinations. For example, `ls -l | grep "Jan"` lists files in long format and then filters the output to show only lines containing "Jan".
3. Write programs to handle text streams, because that is a universal interface.


## Tips and Tricks

- Use `Tab` for auto-completion of commands and file names.
- To run a shell script, you can use `./script.sh` if the script is in the current directory and has execute permissions.
- Some modern systems prevent you from deleting everything by mistake with `rm -rf /` by making it a protected command. However, you can still force it with `rm -rf --no-preserve-root /`, so be very careful when using `rm -rf` and always double-check the path you're deleting.
- `sh` program is compiled executable. On the other hand, `.sh` extension is used for shell scripts, which are interpreted and run by `sh` or another shell interpreter.
- When using nano, you can save and exit by pressing `Ctrl + O` to write the changes to the file, then `Enter` to confirm the file name, and finally `Ctrl + X` to exit the editor.
- `Ctrl + C` is used to interrupt a running command or process in the terminal. This sends a "SIGINT (signal interrupt)" to the process, which typically causes it to terminate.


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
- **program**: A set of instructions that can be executed by a computer to perform a specific task. Programs can be written in various programming languages and can be compiled or interpreted.
- **compiled program**: A program that has been translated from source code into machine code, which can be directly executed by the computer's hardware. Examples of programming languages that typically produce compiled programs include C, C++, Go and Rust.
- **interpreted program**: A program that is executed line by line by an interpreter, which reads the source code and performs the specified actions without the need for a separate compilation step. Examples of programming languages that typically produce interpreted programs include Python, JavaScript, Ruby and shell scripts.
- **executable**: A file that can be run as a program or script.
- **shell script**: A text file containing a series of commands that can be executed by the shell. extensions: .sh, .bash, .zsh, etc.
- **root user**: The superuser account in a Unix-like operating system that has full administrative privileges and can perform any action on the system.
- **shebang**: The first line of a script that specifies the interpreter to be used to execute the script. It starts with `#!` followed by the path to the interpreter (e.g., `#!/bin/bash`).
- **Three types of shells:** `sh` (Bourne shell), `bash` (Bourne Again SHell), and `zsh` (Z shell). 
  - `sh` is the original Unix shell, which is simple and widely available but lacks some features found in more modern shells.
  - `bash` is an enhanced version of `sh` that includes additional features such as command-line editing, improved scripting capabilities, and better support for arrays and functions. It is the default shell on many Linux distributions.
  - `zsh` is another popular shell that offers even more features and customization options than `bash`, including advanced tab completion, improved globbing, and a powerful plugin system.
- **configuration file**: A file used to store settings and preferences for a program or system. In the context of shells, configuration files (e.g., `.bashrc`, `.zshrc`) are used to customize the behavior of the shell, such as setting environment variables, defining aliases, and configuring the prompt.
- **flags**: Options that can be added to commands to modify their behavior. Flags are typically preceded by a hyphen (-) for single-letter flags (e.g., `-l`) or two hyphens (--) for longer, more descriptive flags (e.g., `--recursive`). Reference: [flags](https://www.ibm.com/docs/en/aix/7.3.0?topic=names-command-flags)
- **positional arguments**: Arguments that are passed to a command in a specific order. The meaning of each argument is determined by its position in the command. For example, in the command `cp source_file destination_file`, `source_file` is the first positional argument and `destination_file` is the second positional argument. The `cd` command takes a single positional argument that specifies the directory to change to. Other commands, like `ls`, can take multiple positional arguments (e.g., `ls dir1 dir2`) to specify multiple directories to list.
- **curl**: A command-line tool used to transfer data from or to a server, supporting various protocols such as HTTP, HTTPS, FTP, and more. It is commonly used for making HTTP requests and downloading files from the internet.
- **exit status**: A numerical value returned by a command or program upon completion, indicating whether it executed successfully or encountered an error. An exit status of 0 typically indicates success, while a non-zero exit status indicates an error or failure. You can check the exit status of the last executed command using the special variable `$?` in the shell. Also called "exit value" or "exit code".
- **standard output (stdout)**: The default destination for output from a command or program, which is typically the terminal or console. Standard output can be redirected to a file or another command using the `>` operator.
- **standard error (stderr)**: The default destination for error messages from a command or program, which is also typically the terminal or console. Standard error can be redirected to a file or another command using the `2>` operator. Eg: `command > output.txt 2> error.txt` (redirects standard output to `output.txt` and standard error to `error.txt`). Real life example: `./process_transactions.sh ../transactions/2020.csv 2> /tmp/worldbanc.log` (runs the `process_transactions.sh` script with the specified CSV file as an argument and redirects any error messages to a log file in the `/tmp` directory).
- **standard input (stdin)**: The default source of input for a command or program, which is typically the keyboard. Standard input can be redirected from a file or another command using the `<` operator. Eg: `command < input.txt` (redirects standard input from `input.txt`).
- **pipe**: A mechanism for connecting the output of one command to the input of another command, allowing you to chain commands together. The pipe operator is represented by the vertical bar (`|`). For example, `ls -l | grep "Jan"` (lists files in long format and then filters the output to show only lines containing "Jan").
- **text stream**: A sequence of characters that can be processed by commands and programs. In the context of the Unix Philosophy, programs are designed to handle text streams, which allows for greater flexibility and interoperability between different commands and programs.
- **package manager**: A tool that automates the process of installing, updating, and managing software packages on a system. Examples include `apt` for Debian-based systems, `yum` for Red Hat-based systems, and `brew` for macOS.