# DevOps Prerequisites

## Who is it for?

- Non-Computer Science or IT background
- Starters in DevOps/cloud journey

## What will it cover?

- Linux basics
- Setting up lab environment
- Virtual Box 
- Vagrant
- Linux networking
- JSON/YAML file structure

## Why is it important?

- DevOps is a culture and practice that requires a strong foundation in various tools and technologies.
- Understanding the basics of Linux and setting up a lab environment is crucial for hands-on experience.
- Familiarity with tools like Virtual Box and Vagrant will help in creating and managing virtual environments for testing and development.
- Knowledge of Linux networking is essential for troubleshooting and managing network configurations.
- Understanding JSON/YAML file structure is important for working with configuration files and automation scripts in DevOps.

## Basic Linux Commands

According to the Stack Overflow Developer Survey 2024, Linux is the most commonly used operating system among developers, and it's also one of the most loved. Most of the industry tools and platforms are built on Linux, making it essential for DevOps professionals to have a good understanding of Linux commands and operations.

### Shell Types

- **Bourne Shell (sh)**: The original Unix shell, which is still widely used for scripting.
- **C Shell (csh/tcsh)**: Known for its C-like syntax, often used in interactive use.
- **Z Shell (zsh)**: An extended version of the Bourne Shell with many improvements, popular among developers for its features and customization options.
- **Bourne Again Shell (bash)**: The most widely used shell, which is an enhanced version of the Bourne Shell, offering features like command history and job control.

`echo $SHELL` - This command will display the current shell being used.

### Basic Commands

- `echo <message>`: Prints the message to the terminal. Also used to display the value of environment variables. In scripts and configuration files, it can be used to print information or debug messages.
- `ls`: Lists files and directories.
- `cd`: Change directory.
- `pwd`: Print working directory.
- `mkdir`: Create a new directory.
- `cd new_dir; mkdir sub_dir; pwd`: Multiple commands in one line. *;* is used to separate commands, allowing you to execute them sequentially.

### Directory Management

- To create a dir hierarchy asia/bangladesh/dhaka:
    - `mkdir asia`
    - `mkdir asia/bangladesh`
    - `mkdir asia/bangladesh/dhaka`
    - `mkdir -p asia/bangladesh/dhaka` (using *-p* flag to create parent directories if they don't exist)
- `rm -r asia`: Remove a directory and its contents recursively.
- `cp -r my_dir /tmp/my_dir_copy`: Copy a directory and its contents recursively.

### File Management

- `touch file.txt`: Create an empty file or update the timestamp of an existing file.
- `cat > file.txt`:  After running this command, the prompt will appear and you can type the content. Hit the Enter key for a new line and press `Ctrl + D` to save and exit.
- `cat file.txt`: Display the content of the file.
- `cp file.txt /tmp/file_copy.txt`: Copy a file to a new location.
- `mv file.txt /tmp/file_moved.txt`: Move or rename a file. To rename a file, you can use the same command with the new name in the same directory, e.g., `mv file.txt new_file.txt`.
- `rm file.txt`: Remove a file.

### User Management

- `whoami`: Display the current user.
- `id`: Display user ID and group information.
- `su username`: Switch to another user account. You will be prompted to enter the password for the specified user. Same machine, different user.
- `ssh username@hostname`: Connect to a remote server using SSH. You will be prompted to enter the password for the specified user on the remote server. Different machine, login remotely.
- Every linux system has a super user called the **root user**. The root user has full administrative privileges and can perform any action on the system. In production or enterprise environments, acces to root user is often restricted for security reasons, and users are given specific permissions to perform their tasks. 
- If a normal user needs to perform administrative tasks, they can use the `sudo` command to execute commands with elevated privileges such as installing software, modifying system configurations, or managing user accounts. The root user can grant them sudo privileges by adding their username into the **/etc/sudoers** file or by adding them to a group that has sudo privileges (e.g., the "sudo" group on Debian-based systems). Now, the user can run commands with `sudo` to perform administrative tasks without needing to log in as the root user. The user needs to enter their own password to confirm the action, and the system will log the command for auditing purposes.

### Download files

- `curl -O https://www.digitalocean.com/robots.txt`: Download a file from the specified URL and save it with the custom name. Without the *-o* flag, the content will be displayed in the terminal instead of being saved to a file. `curl`; "Client URL".
- `wget https://example.com/file.txt -O file.txt`: Download a file from the specified URL and save it with a custom name. `wget`; "World Wide Web get".