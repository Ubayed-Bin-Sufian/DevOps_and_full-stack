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

### Check OS version

- `ls /etc/*release*`: This command lists the contents of the /etc directory that match the pattern *release*, which typically includes files that contain information about the operating system version and distribution. The output may vary depending on the Linux distribution being used, but it often includes files like `os-release`, `lsb-release`, or `redhat-release` that provide details about the OS version, name, and other relevant information.
- `cat /etc/*release*`: This command displays the contents of the files in the /etc directory that match the pattern *release*. These files usually contain information about the operating system version and distribution. By running this command, you can see details such as the OS name, version number, and other relevant information about the Linux distribution you are using.

### Package Managers

Package managers are tools that automate the process of installing, updating, configuring, and removing software packages on a computer. They help manage dependencies and ensure that the correct versions of software are installed. Different Linux distributions use different package managers. For example:
- Debian-based distributions (like Ubuntu) use `apt` (Advanced Package Tool).
- Red Hat-based distributions (like CentOS, Fedora) use `yum` or `dnf`.
- Arch Linux uses `pacman`.

#### apt (Advanced Package Tool)

`apt` is a package manager used in Debian-based Linux distributions that provides a high-level interface for managing software packages. It automatically resolves dependencies and allows you to easily install, update, and remove software packages. For example:
- `apt install package_name`: Install a package along with its dependencies.
- `apt remove package_name`: Remove a package.
- `apt update`: Update the package index to get the latest information about available packages.
- `apt upgrade`: Upgrade all installed packages to their latest versions.

#### Red Hat Package Manager (RPM)

A software is bundled into a package file with the .rpm extension. The `rpm` command is used to manage these packages, allowing you to install, update, remove, and query software on your system. For example:
- `rpm -i package.rpm`: Install a package.
- `rpm -e package_name`: Remove a package.
- `rpm -q package_name`: Query if a package is installed. 

It does not resolve dependencies automatically, so you may need to manually install any required packages before installing the main package. For example, if you try to install ansible using `rpm -i ansible.rpm` and it has dependencies like `python3` and `python3-pip`, you would need to install those dependencies first before installing ansible.

#### yum (Yellowdog Updater, Modified)

`yum` is a high level package manager used in Red Hat-based Linux distributions that uses RPM under the hood. It automatically resolves dependencies and allows you to easily install, update, and remove software packages. It searches software repositories that act as warehouses containing rpm packages. For example:
- `yum install package_name`: Install a package along with its dependencies.
- `yum remove package_name`: Remove a package.
- `yum update package_name`: Update a package to the latest version.

*How does yum find where a particular is located?* It looks into the repository configuration files located in `/etc/yum.repos.d/` directory. These files contain information about the repositories, including their URLs and the packages they contain. When you run a yum command, it checks these repositories for the requested package and its dependencies, and then downloads and installs them as needed. At times, the default set of repos may not have the software you need or may not have the latest version. So you need to configure additional repositories so yum can find those packages. Instructions to configure additional repositories are usually provided on the software vendor's website. 

- `yum repolist`: List all configured repositories and their status (enabled/disabled).
- `ls /etc/yum.repos.d/`: List the repository configuration files in the yum.repos.d directory. Each file corresponds to a repository and contains information about its name, base URL, and other settings. By checking these files, you can see which repositories are configured on your system and where yum will look for packages when you run installation or update commands.
- `cat /etc/yum.repos.d/<repo_file>.repo`: Display the contents of a specific repository configuration file. This file contains details about the repository, such as its name, base URL, and whether it is enabled or disabled. By examining this file, you can understand where yum will look for packages when you run installation or update commands, and you can also modify the repository settings if needed.
- `yum list <package_name>`: Check if a specific package is available in the configured repositories. 
- `yum --showduplicates list <package_name>`: Check for all available versions of a specific package in the configured repositories. This command will show you all the versions of the package that are available for installation, allowing you to choose which version you want to install or update to.

### Services

Services are background processes that run on a server to provide specific functionality, such as web hosting, database management, or file sharing.

Once software that runs in the background (e.g., web servers, databases) is installed, it needs to keep running reliably even after a reboot. Services ensure that these programs start automatically and in the correct order. For example, a database service should start before a web server that depends on it. Most background software is configured as a service during installation.

- `service <service_name> start`    : Start a service. (old command, still works in some distros)
- `systemctl start <service_name>`  : Start a service. (new command, used in most modern distros)
- `systemctl stop <service_name>`   : Stop a service.
- `systemctl status <service_name>` : Check the status of a service (whether it's running or not).
- `systemctl enable <service_name>` : Enable a service to start automatically at boot time.
- `systemctl disable <service_name>`: Disable a service from starting automatically at boot time.

#### How to configure a software/program as a service?

Most modern Linux distributions use systemd to manage services. Each service is defined using a unit file, which is a configuration file (with a `.service` extension) typically located in `/etc/systemd/system/`.

Steps to configure a software as a systemd service:
1. Create a unit file for the service. For example, if you want to create a service for a web application called "myapp", you would create a file named `myapp.service` in the `/etc/systemd/system/` directory.
2. To add additional metadata about the service, such as a description or dependencies, you can include a `[Unit]` section in the unit file.
3. Define a section caled `[Service]` in the unit file, where you specify the command to start the service and directive named `ExecStart` to specify the command that will be executed to start the service. If the application has other dependencies, commands or scripts to run before or after starting the main application, you can specify them using directives like `ExecStartPre` or `ExecStartPost`. If the app needs to be restarted if it crashes, you can use the `Restart` directive. 
4. To configure the service to start automatically at boot time, define a section called `[Install]` in the unit file. In this section, you can specify the target that the service should be associated with using the `WantedBy` directive. For example, if you want the service to start when the system reaches the multi-user target (which is a common target for services), you would add the following lines to the unit file.
5. After defining the `[Install]` section, you can enable the service to start at boot time using the `systemctl` command: `sudo systemctl enable myapp.service`
6. Save the unit file and reload the systemd manager configuration to recognize the new service: `sudo systemctl daemon-reload`
7. Start the service using the `systemctl` command: `sudo systemctl start myapp.service` 
8. Stop the service using the `systemctl` command: `sudo systemctl stop myapp.service`
9. Check the status of the service: `sudo systemctl status myapp.service`

Unit file contents:
```
[Unit]
Description=My Web Application Service

[Service]
ExecStart=/usr/bin/python3 /path/to/myapp.py
ExecStartPre=/usr/bin/echo "Starting myapp service..."
ExecStartPost=/usr/bin/echo "myapp service started successfully!"
Restart=always

[Install]
WantedBy=multi-user.target
```

## Vi Editor

`vi` is a powerful text editor that is commonly used in Linux environments. In devops and cloud environments, you will often need to edit configuration files, write scripts, or manage code directly on the server. Knowing how to use `vi` allows you to efficiently make changes to files without needing a graphical interface, which is especially important when working on remote servers via SSH. vi editor comes by default in most Linux distributions. Types of vi editors:
- `vi`: The original version of the editor.
- `vim` (Vi IMproved): An enhanced version of vi with additional features and improvements. It is widely used and often the default vi editor in many Linux distributions.
- `nvim` (Neovim): A modern fork of vim that aims to improve performance and add new features while maintaining compatibility with vim. It is gaining popularity among developers for its extensibility and improved user experience.
- `nano`: A simpler text editor that is easier for beginners to use. It provides a more user-friendly interface compared to vi and vim, making it a good choice for those who are new to command-line text editing.

### Basic vi Commands

Vi editor has two main modes: **command mode** and **insert mode**. When you open a file in vi, you start in command mode, where you can navigate through the file and execute commands. To edit the file, you need to switch to insert mode. Here are some basic commands to get started with vi editor:

- `vi filename`: Open a file in vi editor. This will open the specified file in command mode.
- `i`: Switch to insert mode to start editing the file. In insert mode, you can type and make changes to the file. To return to command mode from insert mode, press the `Esc` key.
- Use the arrow keys to navigate through the file in command mode. You can also use `h`, `j`, `k`, and `l` keys for left, down, up, and right navigation respectively.
- `x`: Delete the character under the cursor in command mode.
- `dd`: Delete the entire line where the cursor is located in command mode.
- `yy`: Copy the entire line where the cursor is located in command mode.
- `p`: Paste the copied line below the current line in command mode.
- `Ctrl + u`: Scroll up half a page in command mode.
- `Ctrl + d`: Scroll down half a page in command mode.
- `:`: Enter command-line mode in vi editor. In this mode, you can execute various commands to save, quit, or perform other actions on the file.
- `:w`: Save the changes made to the file in command-line mode.
- `:q`: Quit the vi editor in command-line mode. If you have unsaved changes, it will prompt you to save before quitting.
- `:wq`: Save the changes and quit the vi editor in command-line mode.
- `/search_term`: Search for a specific term in the file in command mode. This will highlight the occurrences of the search term in the file. You can navigate through the search results using `n` (next) and `N` (previous) commands in command mode.

## Virtualization

### what we'll cover?

- Setting up your lab (laptop vs cloud)
- Virtual Box
    - Deploying VMs
    - Multiple VMs
    - Networking and troubleshooting network issues
    - Snapshots and Restore VMs

### Setting up labs in laptop

There are two main options for setting up labs for practicing DevOps skills: using a local laptop or using cloud-based virtual machines such as AWS, Azure, or Google Cloud Platform.

We will focus on setting up labs in home environment using laptop or desktop computer. This approach allows you to have full control over your lab environment and is cost-effective since you can use your existing hardware. You can use virtualization software like VirtualBox to create and manage virtual machines on your local machine. 

#### What is a home lab environment? What are the things that we can do in it?

While learning devops and cloud technologies, we will come across various tools such as git for version control, Jenkins for continuous integration and deployment, Docker for containerization, Kubernetes for container orchestration, Ansible, Chef or Puppet for configuration management, programming frameworks like Python, Java or Node.js, and their dependent libraries, web servers like Apache, Nginx, tomcat servers, databases like MySQL or MongoDB, cloud management tools like AWS CLI, Azure CLI, Google Cloud SDK, differenct OS such as Ubuntu, CentOS, Red Hat, and many more. We can install all of these tools and technologies in our laptop, but it can create a mess and may lead to conflicts between different software versions, compatibility issues and performance degradation. For example, if you have a project that requires Python 3.8 but your system has Python 3.10 installed, it can cause compatibility issues.

One way to avoid this is to use virtual machines (VMs) to create isolated environments for each project or tool. This way, you can have different versions of software and tools installed in separate VMs without affecting your main system. If anything wrong happens in the VM, we can simply delete it and create a new one without worrying about breaking our main system. Or take a backup of the VM using snapshots and restore it to a previous state if needed. This allows us to experiment and learn different systems in different VMs and different OS in VMs irrespective of the OS of our main system. 

### Virtualization software

Virtualization software / hypervisors are tools that allow you to create and manage virtual machines on your physical hardware. They provide a layer of abstraction between the physical hardware and the virtual machines, allowing you to run multiple operating systems and applications on a single physical machine. 

Types of virtualization software:

1. **Type 1 Hypervisor (Bare-metal)**: This type of hypervisor runs directly on the physical hardware and manages the virtual machines. Examples include VMware ESXi, Microsoft Hyper-V, and Xen. Type 1 hypervisors are typically used in enterprise or production environments for server virtualization. They are used when we need large number of VMs, high performance, and better resource management. They require high resource requirements and they are expensive. 

2. **Type 2 Hypervisor (Hosted)**: This type of hypervisor runs on top of a host operating system and manages the virtual machines. Examples include Oracle VirtualBox, VMware Workstation, and Parallels Desktop. Type 2 hypervisors are commonly used for desktop virtualization and are suitable for home labs and development environments. They are easier to set up and use, and they are more cost-effective compared to Type 1 hypervisors. However, they may have performance overhead due to running on top of a host operating system.

We will be using Type 2 hypervisor, specifically Oracle VirtualBox, for our home lab environment. 

Comparison of Oracle VirtualBox and VMware Workstation:

| Feature                     | Oracle VirtualBox                 | VMware Workstation                |
|-----------------------------|-----------------------------------|-----------------------------------|
| Cost                        | Free and open-source              | Paid software with a free trial   |
| Platform Support             | Windows, macOS, Linux             | Windows, Linux                    |
| Performance                  | Good performance for most use cases | Generally better performance, especially for resource-intensive applications |
| User Interface              | User-friendly and intuitive       | User-friendly with more advanced features |
| Snapshot and Cloning        | Supports snapshots and cloning    | Supports snapshots and cloning    |
| Resource Management         | Good resource management features  | Advanced resource management features |

#### Installing VirtualBox on Linux Mint 22.3 (Zena)


This is the latest version of Linux Mint I had when writing this blog.