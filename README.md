# Linux-Introduction-Course

## What is Linux?

Linux is a family of open-source Unix-like operating systems based on the Linux kernel, created by Linus Torvalds in 1991. It is most used operating system on servers.

**Key Features of Linux:**

- **Open-Source:** Anyone can view, modify, and distribute the source code.
- **Secure and Stable:** Linux is widely used in servers due to its robustness.
- **Versatile:** Linux runs on various hardware platforms, from desktops to supercomputers.

**Why Use Linux?**

- It’s free and community-driven.
- Offers excellent performance and customization options.
- Provides extensive developer tools and scripting capabilities.


## Linux Distributions and Package Management

A **Linux distribution (distro)** is a customized version of Linux that combines the Linux kernel with specific software, configurations, and package managers.

**Popular Linux Distributions:**

1. **Debian-based:** Debian, Ubuntu, Linux Mint
    - Package Manager: `apt`
    - Example command: `sudo apt install package_name`
2. **Red Hat-based:** Red Hat Enterprise Linux (RHEL), CentOS, Fedora
    - While CentOS/RHEL are mostly used in servers, Fedora is more user-friendly approach to RHEL-based distros
    - Package Manager: `dnf` or `yum`
    - Example command: `sudo dnf install package_name`
3. **Arch-based:** Arch Linux (use if you love pain & suffering)
    - Package Manager: `pacman`
    - Example command: `sudo pacman -S package_name`


**How Package Formats Are Different:**

- **Debian (.deb):** Precompiled binaries for Debian-based systems.
- **Red Hat (.rpm):** Red Hat-based binary format.
- **Source Packages:** Some distros like Gentoo compile software from source, allowing optimization for your hardware.
### Crazy big linux distribution tree

https://en.wikipedia.org/wiki/List_of_Linux_distributions#/media/File:Linux_Distribution_Timeline.svg

## What is Ubuntu?

Ubuntu is one of the most popular Linux distributions, based on Debian. It is designed to be user-friendly and is widely used for development, education, and production-ready systems

**Key Features of Ubuntu:**

- **User-Friendly:** Aimed at beginners, with a graphical user interface (GUI) and pre-installed software.
- **Long-Term Support (LTS):** LTS versions receive five years of updates and support.
- **Community Support:** A vibrant community and extensive documentation.
- **Wide Application:** Great for servers, desktops, and cloud computing.

**Common Use Cases:**

- Development and programming.
- Running web servers and databases.
- Hosting virtual machines and containers.


## What is Bash?

Bash (**B**ourne **A**gain **SH**ell) is the default command-line shell for most Linux distributions. It allows users to interact with the system and automate tasks through scripting.

**Why Use Bash?**

- Pre-installed on almost all Linux systems.
- Supports complex scripts with loops, conditions, and functions.
- Compatible with numerous Unix utilities.

**Common Bash Features:**

- **Variables:** Store data for use in scripts or commands.
- **Redirection:** Direct output/input to/from files or other commands.
- **Job Control:** Manage background and foreground processes.


## So, let's learn how to use terminal

Every command in bash has its own options. Options are used to modify behavior of that command. As an example, let's take  `rm` command, which is used for removing things around file system.

Let's say we have `test-1` directory and 2 files/folders inside of it, if you try to use `rm -fv` to remove folder and contents inside of it, you'll fail and get this error:

`rm: cannot remove 'test-1': Is a directory`

`-f` - force (ignore nonexistent files and arguments)
`-v` - verbose (shows what is being done)

But, if you use `rm -rvf test-1`, it will remove folder itself and all contents inside of that folder.
You can always access options of specific command with `command --help`, Example:

- `rm --help`
- `ls --help`
OR
- `man rm`
- `man ls`

`man` means manual and it'll show you:
- description
- authors
- naming
- usage
- etc.
about that specific command

Also every command in bash has its own opening. rm (remove), ls (list), and etc.

### **Basic Navigation**

- `pwd` - print working directory
	- Prints current working directory (the folder you're in)
	
- `ls` - list
	- Lists all files and folders in the current directory
	- Except files that starts with `.`, because in most of the UNIX-based operating systems you can hide any file with adding dot in front of file name (MacOS, Linux, BSD)
	- Options for `ls`
		- `-l` - long (display file metadata)
		- `-t` - time (sorting based on modified time)
		- `-r` - reverse (reverse the order of the sort)
	- If you use `ls -ltr`, you'll see last modified at the end of the list, but if you don't use `-r` then you'll see last modified on top of the list
	
- `cd` - change directory
	- Changes the current directory to the specified one.
	- `cd ~` - back to the home folder
	- `cd ..` - will go one folder back
		- if use this command in `/home/user/Downloads/folder/` you will go back to the `/home/user/Downloads/`
	- `cd test_1/` - enter test_1 folder (if it exists in your current directory)
	- `cd -` - go back to the previous folder


**TIP:** Use `zoxide` instead of `cd`. It's written in Rust, faster than `cd` and you don’t need to be in a specific location to jump to a directory. It learns your usage patterns and lets you quickly navigate to frequently used directories.

### **File Management**

- `mkdir folder_name` - make directory
	- Creates folder in your current directory
	- Options for `mkdir`
		- `-v` - verbose (print a message for each created directory)
		- `-m` - mode (set file mode for user permissions)
	
- `rm file or folder name` - remove
	- Removes file/directory you enter
	- Options for `rm`
		- `-r` - recursive. remove directories and their contents recursively  
		- `-v` - verbose. show what has been done.
		- `-f` - force. ignore non-existent files
		- `-I` - interactive. used for removing three or more files
		- `-d` - dir (directory). remove empty directories
	
- `touch file_name`
	- Generally used for creating files.
	- Options for `touch`
		- Generally (at least in my experience) I haven't used any options with `touch`. It exists, but generally not used.
	
- `mv` - move
	- You can move files around directories and/or move files to different file
	- Options for `mv`
		- `-b` - backup. make a backup of each existing destination file
		- `-f` - force. don't prompt before overwriting
	
- `cat file_name` - concatenate file and print on the standard output
	- Generally used for printing content of the file
	- Options for `cat`
		- `-n` - number. show numbers for every line for file
	
- `cp` - copy file or directory
	- Used to copy files or directories from one location to another.
	- Options for `cp`
		- `-r` - recursive. copy directories and their contents
		- `-v` - verbose. show the files being copied
		- `-i` - interactive. prompt before overwriting files
		- `-f` - force. overwrite files without prompting
		- `-u` - update. copy only if the source is newer or doesn’t exist

### **Text Manipulation and Viewing**

- `less file_name`
  - Opens the file in a viewer, allowing you to scroll through the content without editing it.

- `more file_name`
  - Similar to `less`, but only allows forward navigation.

- `head file_name`
  - Displays the first few lines of a file.
  - Options for `head`:
    - `-n` - Specify the number of lines to display (default is 10).

- `tail file_name`
  - Displays the last few lines of a file.
  - Options for `tail`:
    - `-n` - Specify the number of lines to display.
    - `-f` - Follow the file, displaying new lines as they are added (useful for logs).

- `grep pattern file_name`
  - Searches for lines in a file that match the specified pattern.
  - Options for `grep`:
    - `-i` - Ignore case.
    - `-v` - Invert match (show lines that do not match the pattern).
    - `-r` - Recursive search in directories.

### **Permissions and Ownership**

- `chmod mode file_name`
  - Changes file permissions.
  - Modes can be specified numerically (e.g., `chmod 755`) or symbolically (e.g., `chmod u+x`).

- `chown user:group file_name`
  - Changes the ownership of a file or directory.
  - Example: `chown user1:group1 myfile`.


**Permission Symbols:**
- `r` - Read
- `w` - Write
- `x` - Execute
- Example: `-rwxr-xr--`
  - Owner: Read, Write, Execute
	  - Admin - opus/ (Owner)
  - Group: Read, Execute
	- Researchers - opus/  (read, write, execute)
	- Developers - opus/ (read)
	- Students - X
  - Others: Read

- `drwxr-xr-x`
	- d - directory
	- r - read
	- w - write
	- x - execute

- Example:
  - 755
    - 7 - owner
    - 5 - group
    - 5 - others

- 0 = no permissions whatsoever; this person cannot read, write, or execute the file
- 1 = execute only
- 2 = write only
- 3 = write and execute (1+2)
- 4 = read only
- 5 = read and execute (4+1)
- 6 = read and write (4+2)
- 7 = read and write and execute (4+2+1)

### **Process Management**
- `ps`
  - Displays active processes.
  - Options for `ps`:
    - `-e` - Show all processes.
    - `-f` - Full format listing.

- `top`
  - Interactive process viewer showing CPU/memory usage.

- `htop` or `btop` (this one is cooler)
  - A more user-friendly version of `top` (requires installation).

- `kill pid`
  - Terminates a process by its process ID.

- `killall process_name`
  - Terminates all processes with a specific name.

## Tools and Links
- https://github.com/eld4niz/helixis/tree/main - Helix tutorial and config
- https://www.redhat.com/en/blog/navigating-filesystem-linux-terminal - Red Hat File Navigation Tutorial

