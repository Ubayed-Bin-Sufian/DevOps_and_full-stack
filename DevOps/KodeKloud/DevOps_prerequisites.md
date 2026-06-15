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

#### Download VirualBox for Linux hosts

Please refer to the official VirtualBox website for the latest version and installation instructions for your specific Linux distribution: https://www.virtualbox.org/wiki/Linux_Downloads

As i use linux mint, i will provide the instructions for installing VirtualBox on Linux Mint 22.3 (Zena).

#### Installing VirtualBox on Linux Mint 22.3 (Zena) using official repositories

This is the latest version of Linux Mint I had when writing this blog.

For system information, you can use the following commands:

- `cat /etc/os-release`: This command displays the contents of the os-release file, which contains information about the operating system, including the name, version, and other relevant details. It is another way to check the version of Linux Mint you are using.

Q: Which VirtualBox repo to use?

A: Linux Mint 22.3 is based on:

- **Ubuntu Codename:** `noble` (Ubuntu 24.04 LTS base)
- **Architecture:** amd64

So we use: **Ubuntu 24.04 (noble) repository**

**Steps to install VirtualBox on Linux Mint 22.3 (Zena):**

1. Add Oracle VirtualBox Repository Key

As per official guide:

```bash
wget -O- https://www.virtualbox.org/download/oracle_vbox_2016.asc | \
sudo gpg --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg --dearmor
```

2. Add Repository (Ubuntu base = noble)

Since Linux Mint 22.3 is based on **Ubuntu 24.04 (noble)** (can be found out through `cat /etc/os-release` ):

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian noble contrib" | \
sudo tee /etc/apt/sources.list.d/virtualbox.list
```

3. Install VirtualBox

```bash
sudo apt-get update
sudo apt-get install virtualbox-7.1
```

4. Verify Installation

```bash
virtualbox --help
```

#### Setting up Oracle VirtualBox

1. Open Oracle VirtualBox from the applications menu.
2. Click on "New" to create a new virtual machine.
3. Follow the prompts to configure the virtual machine, including selecting the operating system, allocating memory, and creating a virtual hard disk. For base memory, it is recommended to allocate at least 2GB (2048 MB) for a Linux VM, but you can allocate more if your system has enough resources. I selected 1GB (1024 MB) for my VM. For hard disk, we can allocate some space for the VM to store its files and data and install the OS manually through a CD drive. OR we can use a pre-configured virtual machine image that already has the OS installed. We can find it from [osbox.org](https://www.osboxes.org/).
4. I preferred to use a pre-configured virtual machine image for linux mint 22.1 Xia. I have downloaded the .7z file. After extracting it, I got a .vmdk file which is the virtual hard disk image. We will use this .vmdk file to create a new virtual machine in VirtualBox.
5. When prompted for hard disk, select "Use an existing virtual hard disk file" and browse to the location of the extracted .vmdk file and select it.
6. Before powering on, right click on the created VM and go to settings. Under "Network", select "Bridged Adapter" to allow the VM to connect to the same network as your host machine. This will enable the VM to have its own IP address and access the internet.
7. Once the virtual machine is created, start in Normal Start.
8. The VM will boot up and you can log in using the credentials provided by osboxes.org (username: osboxes, password: osboxes.org).

**[For installation of VirtualBox on windows and macOS, please refer to the youtube video mentioned in Reference section below]**

### Virtual Box Connectivity

In this section, we will learn about
- How to connect and ssh into a vm
- why can't i access the server on my vm
- what's port mapping?

When a vm is downloaded and installed, we can start the vm using:
1. **Normal start**: It gives a console to the vm. we can see the ui and if the image has a GUI, we can see and use it. In DevOps world, it's better to work with CLI access instead of GUI. If the console is closed, the vm must be shut down or suspended.

2. **Headless start**: In this mode, the vm starts but the console windows will not be opened. The vm can only be accessed using ssh or remote desktop tools.

3. **Detachable start**: Starts the vm in normal mode, but closing the console does not shut down the vm. In addition to normal mode, the vm has the option to run in the background.

Depending on what os has been used on the guest system we have different ways of connecting to it for example say we
had a windows system to remotely connect to the windows system without using the console you could use the some kind of
remote desktop clients such as the one provided by microsoft. now if the guest has a linux operating system such as linux mint,  centos, etc we can connect to it remotely through ssh using ssh clients like the terminal app in linux or mac and tools like putty
in windows.

Even the vms are within our laptop (host) think of them as separate machines connected to the same network so whatever you need for one system to connect to another system you would need these vms configured with ip addresses and the relevant services must be configured and running on. On windows, the remote desktop service needs to be running and on linux the ssh service needs to be running so make sure ssh server is installed and is in a running state in the vm (guest system). If configured you can ssh into the vm from the host system using the terminal on the host and the ip address of the remote vm.

#### How do you configure ssh services and ip addresses on the vm?

Use the console to perform initial configuration it's a common practice to use the console to perform initial configurations and then once ssh is enabled switch over to the terminal for all future interactions.

If you run into issues connecting to a vm check to **make sure that the vm has an ip address set and you are using the right ip address and that ssh service on the remote vm is running**.

There are two approaches of networking when deploying vms:

1. Bridged adapter : the vm becomes part of the external network and it gets an ip address assigned to it you can simply ssh to it as you would ssh to another system in your network.
Eg: `ssh username@ip_address -p port_number`
2. NAT : it doesn't connect to the external network and so does not get an ip address on the external network that we can use ssh
to. If you had multiple vms you will see that all vms configured with nat are isolated and they all get the same ip address assigned and they cannot reach each other however with network address translation they can reach the external world so you should have internet connectivity if your host has internet connectivity you can verify that by trying to ping an external website. To ssh into the guest, first verify using `service sshd status` to see the service is running. Now, we need to set up port forwarding. In the Oracle Virtual Box, settings of the vm created --> Network --> Advanced; Port forwarding --> Add a new rule. The default port for SSH is port 22. The ssh service listens on port 22 on the vm but we also have an ssh service on our host that uses port 22. so we cannot forward 22 on our host to the vm so we will configure another port say port 2222 on the host to forward to port 22 on the vm so we add a rule for that and we name it ssh port. Now we can ssh into the vm using the forwarded port

Q: How to check and set ip addresses?

A: Different operating systems have different device names and commands may differ. Refer to OS documentations for setting it.

#### Start SSH service

To check if the daemon is running, run `sshd status command` if it's not running run the `service sshd start` command to start it well.

**[For connecting to a vm on windows and macOS, please refer to the youtube video mentioned in Reference section below]**

### Virtual Box Networking

In this section we will discuss,

- Understand various types of networking - NAT, bridged, host only and what do they mean and when to use what type of network
- how multiple vms connect each other
- how to troubleshoot issues where you can't reach the internet

#### A Computer Can Have More Than One Door to the Network

When we think about connecting a computer to the internet, we usually imagine just one connection — maybe Wi-Fi.

But a computer can actually have **multiple network interfaces**, and each one acts like its own separate **door** to the network.

Let me show you using my own laptop.

When I ran:

```bash
ip addr show
```

I got this:

```bash
ubayed@ubayed-HP-ProBook-450-G4:~$ ip addr show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8

2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500
    link/ether 3c:52:82:df:af:68

3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.0.105/24
```

At first glance, this looks technical. But there’s a simple story here.

---

#### Meet the three characters

#### 1. `lo` — The computer talking to itself

The **loopback interface** (`lo`) is special.

```bash
inet 127.0.0.1/8
```

This is the famous **localhost** address.
Think of it as your laptop looking into a mirror.

When an application talks to `127.0.0.1`, it is not going out to the network — it is talking back to the same machine.

---

#### 2. `enp1s0` — The unused Ethernet port

Next:

```bash
2: enp1s0
state DOWN
NO-CARRIER
```

This is my **wired Ethernet adapter**.
It exists, but no cable is plugged in.

Imagine a door in your house that exists but is closed — nobody can enter through it.

That is why there is **no IP address** assigned here.

---

#### 3. `wlp2s0` — The active Wi-Fi connection

Finally:

```bash
3: wlp2s0
inet 192.168.0.105/24
state UP
```

This is my **wireless adapter**.

This one is connected to my home Wi-Fi, so my router (through DHCP) assigned it an IP:

```bash
192.168.0.105
```

This is the address other devices on my home network can use to reach my laptop.

---

#### What if both were connected?

Now imagine I plug in an Ethernet cable while Wi-Fi is still on.

Suddenly my laptop could look like this:

```text
enp1s0  -> 192.168.0.110
wlp2s0  -> 192.168.0.105
```

Same laptop.

Two interfaces.

Two IP addresses.

Two different doors into the same machine.

Other devices could reach me using **either address**.

---

#### The big lesson

A computer is not assigned an IP address.

An **interface** is assigned an IP address.

That is an important distinction.

Your laptop may have:

- one Wi-Fi adapter
- one Ethernet adapter
- a VPN tunnel
- virtual machine adapters
- docker bridges
- loopback

Each can have its **own IP address**.

So when someone says:

> "What is your computer's IP?"

The more accurate question is:

> "Which interface are you talking about?"

### Glossary

- A network interface is the part of a computer that allows it to communicate on a network.
- A network adapter is the hardware (or virtual hardware) that provides that interface.

```
Hardware (adapter)  --->  Operating System sees it as ---> Interface
```


Think of your laptop as a small building. Inside that building, VirtualBox creates multiple “virtual computers” (VMs).

Each VM:
- Has its own network card (adapter)
- Can connect to a “network type” you choose
- Can have up to 4 network adapters (but usually 1 is enough)

Now the key question is:

> “Which network is this VM plugged into?”

That choice defines everything.

---

# 1. Host-Only Network (Private Lab Inside Your Laptop)

## 🧩 Concept

A **Host-Only network** is like creating a private LAN inside your laptop.

- Only your host machine + VMs can talk
- No internet access by default
- Completely isolated from the outside world

---

## 🌐 Example Setup

Imagine this network:


Host machine: 192.168.5.1
VM1: 192.168.5.2
VM2: 192.168.5.3
VM3: 192.168.5.4


All machines:
- Can ping each other
- Share files/services internally
- Cannot access the internet

---

## ⚙️ How it works in VirtualBox

1. Go to **File → Host Network Manager**
2. Create a new host-only network
3. VirtualBox creates a virtual adapter (like `vboxnet0`)
4. Your host gets an IP like `192.168.5.1`
5. Attach VMs to **Host-Only Adapter**

---

## 🔥 Use Case

- Testing microservices locally
- Simulating private networks
- Database + backend interaction in isolation

# 2. NAT Network (Private Network + Internet Access)

## 🧩 Concept

A **NAT Network** is like a private LAN with a built-in router to the internet.

- VMs can talk to each other
- VMs can access the internet
- External systems still cannot directly access VMs

---

## 🌍 How it works (important mental model)

When a VM sends a request:

1. VM sends packet with its private IP (e.g. `10.0.2.4`)
2. VirtualBox NAT engine replaces it with host IP
3. Request goes to internet / external system
4. Response comes back to host
5. NAT engine forwards it back to correct VM

This is called:

> **Network Address Translation (NAT)**

---

## 🌐 Example


VM1 → 10.0.2.4
VM2 → 10.0.2.5
VM3 → 10.0.2.6


All share:
- Internet access
- Internal communication (within NAT network)

---

## ⚙️ Setup

1. Go to **VirtualBox Preferences → Network**
2. Create a **NAT Network**
3. Attach VM → Network → “NAT Network”

---

## 🔥 Use Case

- Running development environments with internet access
- Package installs (apt, npm, pip)
- APIs + database testing with external services

---

# 3. NAT (Default VM Mode)

## 🧩 Concept

This is similar to NAT Network but simpler and more isolated.

- VM can access internet
- VM cannot talk to other VMs (by default)
- Each VM behaves like it has its own mini-router

---

## ⚠️ Key Difference vs NAT Network

| Feature | NAT | NAT Network |
|--------|-----|-------------|
| Internet access | ✅ | ✅ |
| VM-to-VM communication | ❌ | ✅ |
| Shared network | ❌ | ✅ |

---

## 🔥 Use Case

- Single VM development
- Safer isolation
- Quick setup without networking complexity

---

# 4. Bridged Network (VM becomes a real machine on your LAN)

## 🧩 Concept

Bridged networking connects your VM directly to your physical network.

> The VM behaves like a real computer on your Wi-Fi/router.

---

## 🌍 Example

If your home network is:


Router: 192.168.1.1
Laptop: 192.168.1.10
Phone: 192.168.1.20


Then VM becomes:


VM: 192.168.1.30


Your router sees it as a real device.

---

## ⚙️ What happens internally

- VM gets IP from your router (via DHCP)
- Same subnet as your laptop
- Fully visible to other devices

---

## 🔥 Use Case

- Hosting services (web servers, APIs)
- Testing real network behavior
- Accessing VM from another machine on LAN

---

# 5. Internet Connectivity Summary

## 🌐 NAT / NAT Network
- Internet works automatically
- Uses host as gateway

## 🌐 Bridged
- Internet works via router directly

## 🚫 Host-Only
- No internet by default

---

## 🛠 If Host-Only needs internet

You have two options:

### Option A: Enable IP forwarding on host
Make your laptop act like a router.

### Option B (simpler): Add second adapter
- Adapter 1 → Host-Only (private network)
- Adapter 2 → NAT (internet)

This is the most common real-world setup.

---

# 6. Port Forwarding (Access VM Services from Outside)

## 🧩 Concept

Port forwarding is like:

> “If someone knocks on this door (port), send them to this VM service.”

---

## 🌐 Example

You have:
- VM running web server on port `80`
- VM is behind NAT (not directly reachable)

You configure:


Host Port 8080 → VM Port 80


Now:


http://localhost:8080
→ forwarded to VM:80


---

## 🔐 SSH Example


Host Port 2222 → VM Port 22


Then you can SSH:

```bash
ssh user@localhost -p 2222
```

Even without knowing VM IP.

## 🔥 Use Case
- Accessing web apps inside NAT VM
- Debugging microservices
- Running multiple VMs with different exposed ports

## Introduction to Vagrant

In the previous sections, we learned how to create and configure virtual machines manually using VirtualBox. The typical process involved:

* Downloading an operating system image from a website such as OSBoxes.
* Creating a new virtual machine.
* Configuring networking (Host-Only, NAT, Bridged, etc.).
* Setting up port forwarding rules.
* Booting the virtual machine.
* Repeating the same steps for every additional VM.

While this approach works, it quickly becomes repetitive and time-consuming when working with multiple virtual machines.

### What is Vagrant?

Vagrant is an open-source tool that automates the creation and management of virtual machine environments. Instead of manually performing all the setup tasks, Vagrant allows you to define your infrastructure as code and provision virtual machines with a single command.

With Vagrant, you can:

* Automatically download operating system images.
* Create and configure virtual machines.
* Configure networking and port forwarding.
* Provision software and dependencies.
* Recreate identical environments across different machines.

This makes Vagrant particularly useful for DevOps engineers, developers, and anyone working with multi-VM lab environments.

### Installing Vagrant

To get started, download and install Vagrant from the official website:

https://developer.hashicorp.com/vagrant

Choose the version that matches your operating system and complete the installation process.

### Understanding Vagrant Boxes

The first step in creating a Vagrant environment is selecting a **box**.

A **Vagrant Box** is a packaged virtual machine image that contains:

* A preconfigured operating system.
* Metadata required by Vagrant.
* Configuration scripts and settings needed to create the environment.

You can browse publicly available boxes on [Vagrant Cloud](https://portal.cloud.hashicorp.com/vagrant/discover) and choose one that matches your requirements.

For example, to initialize a CentOS 7 environment:

```bash
vagrant init centos/7
```

This command creates a file named `Vagrantfile` in the current directory.

### The Vagrantfile

The `Vagrantfile` is the heart of a Vagrant environment. It contains configuration instructions that define how the virtual machine should be created and customized.

Using the `Vagrantfile`, you can configure:

* VM resources (CPU and memory)
* Networking settings
* Port forwarding
* Shared folders
* Provisioning scripts

We will explore these configurations in more detail later.

### Starting a Virtual Machine

Once the environment has been initialized, start the virtual machine with:

```bash
vagrant up
```

When executed, Vagrant automatically:

1. Downloads the required box if it is not already available locally.
2. Creates the virtual machine using the selected provider (such as VirtualBox).
3. Applies networking and port-forwarding configurations.
4. Boots the virtual machine.
5. Waits until the machine is ready for use.

All of these steps are completed through a single command, significantly reducing the manual effort required to create and manage virtual machines.

### Why Use Vagrant?

Vagrant shines when working with complex environments that contain multiple virtual machines. Instead of manually configuring each VM, you can describe the entire setup in code and reproduce it whenever needed.

Benefits of Vagrant include:

* Consistent development environments.
* Faster environment setup.
* Infrastructure as Code (IaC) practices.
* Easy sharing of environments among team members.
* Simplified management of multi-VM labs.

For anyone learning DevOps, Vagrant provides an excellent way to build reproducible local infrastructure without repeatedly performing manual VirtualBox configurations.

## Common Vagrant Commands

Once Vagrant is installed, you can view all available commands by running:

```bash
vagrant
```

This displays a list of commands that help you create, manage, and interact with your virtual machines.

### Managing Vagrant Boxes

To manage installed Vagrant boxes, use:

```bash
vagrant box
```

This command provides subcommands for tasks such as listing, adding, updating, and removing boxes from your local system.

### Initializing and Starting a VM

To create a new Vagrant environment:

```bash
vagrant init <box-name>
```

For example:

```bash
vagrant init centos/7
```

To create and start the virtual machine:

```bash
vagrant up
```

This command downloads the box (if necessary), creates the VM, applies the configuration from the `Vagrantfile`, and starts the machine.

### Suspending and Resuming a VM

If you want to temporarily pause a virtual machine without shutting it down completely, use:

```bash
vagrant suspend
```

To continue from where the machine was suspended:

```bash
vagrant resume
```

This is similar to putting a laptop into sleep mode and waking it up later.

### Stopping a VM

To gracefully shut down a running virtual machine:

```bash
vagrant halt
```

The VM remains available on disk and can be started again using `vagrant up`.

### Destroying a VM

To stop and permanently remove a virtual machine:

```bash
vagrant destroy
```

This command deletes the VM created by Vagrant but does not remove the box image itself.

> **Note:** Any data stored inside the VM that is not backed up elsewhere will be lost.

### Checking VM Status

To check the current state of a Vagrant-managed machine:

```bash
vagrant status
```

This command shows whether the VM is running, stopped, suspended, or not yet created.

### Reloading Configuration Changes

After making changes to the `Vagrantfile`, apply the updated configuration using:

```bash
vagrant reload
```

This restarts the VM and reloads the new settings.

### Working with Snapshots

Vagrant also supports snapshots, allowing you to save and restore the state of a virtual machine.

Create a snapshot:

```bash
vagrant snapshot save <snapshot-name>
```

Restore a snapshot:

```bash
vagrant snapshot restore <snapshot-name>
```

Snapshots are useful when experimenting with software installations or system configurations, as they allow you to quickly revert to a known working state.

### Connecting to a VM via SSH

One of the most convenient Vagrant features is simplified SSH access.

To connect to a running VM:

```bash
vagrant ssh
```

Vagrant automatically:

* Detects the correct SSH port.
* Uses the appropriate SSH configuration.
* Handles SSH key-based authentication.

As a result, you can access the virtual machine without manually remembering IP addresses, ports, usernames, or SSH keys.

This greatly simplifies working with development and testing environments.

## Understanding the Vagrantfile

The heart of every Vagrant project is the **Vagrantfile**. When you run the `vagrant init` command, Vagrant creates this file in your current directory.

A basic `Vagrantfile` looks something like this:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
end
```

The file begins with a configuration block, and within that block, the box (operating system image) to be used is specified. In this example, the VM will be created using the `centos/7` box.

Although the default `Vagrantfile` contains only a few lines, it is highly customizable. By modifying this file, you can define exactly how your virtual machine should be created and configured.

One of the biggest advantages of Vagrant is that the entire environment configuration is stored as code. This means you can share the `Vagrantfile` with teammates, and everyone can create an identical environment simply by running:

```bash
vagrant up
```

### Configuring Port Forwarding

Port forwarding allows services running inside the virtual machine to be accessed from the host machine.

For example, the following configuration forwards port `8080` on the host to port `80` inside the VM:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.network "forwarded_port",
    guest: 80,
    host: 8080
end
```

With this configuration, accessing `localhost:8080` on the host machine will forward traffic to port `80` inside the virtual machine.

### Syncing Files Between Host and VM

Vagrant can automatically synchronize directories between the host machine and the guest VM.

```ruby
config.vm.synced_folder "./app", "/var/www/html"
```

This allows files created or modified on the host machine to become immediately available inside the virtual machine.

Shared folders are especially useful for software development, where source code is edited on the host and executed inside the VM.

### Configuring CPU and Memory

You can customize hardware resources such as CPU and RAM using a provider-specific configuration block.

For VirtualBox:

```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = "2048"
  vb.cpus = 2
end
```

This configuration allocates:

* 2 GB of RAM
* 2 CPU cores

to the virtual machine.

### Running Provisioning Scripts

Provisioning allows you to automatically configure the VM after it is created.

For example, you can run a shell script during startup:

```ruby
config.vm.provision "shell", inline: <<-SHELL
  yum update -y
  yum install -y nginx
SHELL
```

When `vagrant up` is executed, Vagrant creates the VM and then runs the provisioning script automatically.

This eliminates repetitive manual setup tasks and ensures every environment is configured consistently.

### Creating Multi-VM Environments

A single `Vagrantfile` can define multiple virtual machines.

For example, you might create:

* A web server VM
* A database VM
* A monitoring VM

all from the same configuration file.

This makes Vagrant an excellent tool for building local lab environments that simulate real-world infrastructure.

### Beyond VirtualBox

Although VirtualBox is the most commonly used provider with Vagrant, it is not the only option.

Vagrant supports multiple virtualization platforms, including:

* VMware Workstation
* VMware Fusion
* Microsoft Hyper-V
* VirtualBox

This flexibility allows you to use the same Vagrant workflow regardless of your preferred virtualization technology.

## Why Learn Vagrant?

Vagrant brings the principles of **Infrastructure as Code (IaC)** to local development environments.

Instead of manually creating virtual machines and configuring networking every time, you can define everything in a `Vagrantfile` and recreate the entire environment with a single command.

Benefits include:

* Reproducible environments
* Faster setup times
* Consistent configurations across teams
* Easy sharing of lab environments
* Automated provisioning and configuration

Once a `Vagrantfile` is created, rebuilding the entire environment becomes as simple as:

```bash
vagrant up
```

This makes Vagrant a valuable tool for anyone learning DevOps, system administration, or infrastructure automation.

