# Linux Fundamentals

This section documents my practical study of Linux fundamentals through explanations and notes, with an essential focus on system administration and cybersecurity. The need for these fundamentals has changed due to Linux's widespread use in servers, cloud infrastructure, containers, and cybersecurity tools. Understanding Linux fundamentals is therefore essential.

The goal is to develop a solid understanding of the Linux operating system, the command-line environment, the file system, the shell, system information, and basic troubleshooting.

### Environment

Linux: Ubuntu/Kali Linux/Debian
Shell: Bash
Architecture: x86_64
Environment: Isolated local lab

---

### 1. Identifying the System

Essentially, this is a way to recognize the machine if the user wants to access more information about it using the terminal.

`uname` - displays the operating system (kernel) name.
`uname -a` - displays all system information together (operating system, hostname, architecture, and date).
`uname -r` - shows only the kernel release version.
`uname -m` - reveals the machine's hardware architecture.
`hostname` - displays the name the machine uses to identify itself on the network.
`hostnamectl` - provides a structured panel with all the hostname, virtualization, and operating system information.
`whoami` - tells you which user is logged in.
`id` - shows the detailed identity of the current user, including their User ID and which groups they belong to.
`uptime` - indicates how long the machine has been continuously powered on.
`date` - displays the system date and time.

Finally, it's a basic feature that's most commonly used when the user doesn't yet have much knowledge of the computer they're using or tends to access many machines simultaneously.

---

## Linux Navigation System

Navigating the Linux file system is fundamental for any system administration, leading to an understanding of the best solutions for network operation or cybersecurity problems, which are generally managed through command lines.

So, initially it's interesting to mention that Linux uses a hierarchical file system structure that starts at the `root directory`:

`/`

Note: all user files and data are organized under this `root directory`:

The second interesting command to learn is:

### pwd - Print working directory

Although a simple command, it's useful because it displays the absolute path of the directory where the user is currently located.

`pwd`

This is useful for navigating the system or executing commands that use relative paths.

### ls - List directory contents

In a way, the `ls` command is used to display files and directories:

`ls`

and it also has some options used such as:

`ls -l`

to display information provided about the files, including permissions, ownership, size, and modification data.

`ls -a`

to display all files, including hidden files whose names originate with `..`.

`ls -lh`

is used to display the size of files in a human-readable format.

And it's also possible to combine the options:

`ls -lah`

This is useful during system administration and security investigations, as it allows you to simultaneously display hidden files, ownership, and file size.

---

### cd - Change Directory

In short, this command is used to navigate between directories. How?

Example:


`cd /etc`

This command will take the shell to the `etc` directory.

To return to the initial directory, the user will use:


`cd ~`

And in the same logic, to go to the parent directory:


`cd ..`

And to return to the previously accessed directory:


`cd -`

Understanding directory navigation is essential when inspecting configuration files, applications, or even system resources.

---

### Absolute and Relative Paths

Linux supports two types of paths: absolute and relative.

- An absolute path starts at the root of the file system (/).

Example:

/var/log/syslog

meanwhile, a relative path starts at the user's current working directory. How?

For example, if the directory is:

`/home/user`

the path:

`Documents/report.txt`

would be represented by:

`/home/user/Documents/report.txt`

Understanding this difference between absolute and relative paths helps to avoid errors when working with files, scripts, and administrative commands.

---

### find - Search the Filesystem

The `find` command searches directories/folders/subdirectories for specific conditions defined by the user. How?

Example:

`find/etc -name ".conf"`

This command creates files with the `.conf` extension in `/etc`.

You can also search only for `common files` like this:

`find /var/log -type f`

or search only for directories:

`find /home -type d`

search starting from the current directory:


`find . -name ".txt"`

This last command is important because it can be used to locate configuration files/suspicious files or files with specific attributes.

---

### locate - Quickly locate files

The locate command offers another method for finding files. Unlike `find`, which searches directly in the file system, `locate` searches a pre-generated database containing indexed filenames.

Example:

`locate ssh_config`

Therefore, `locate` can be effectively faster unless you are looking for a recently created file, as there is a chance it may not yet be in the database.

Note: Depending on the Linux distribution being used, the database can be updated with:

`sudo updatedb`

---

### Important Linux Directories

Understanding the Linux file system hierarchy is essential, as different types of information are stored in specific directories.

`/etc`

The /etc directory contains system-wide configuration files.

Examples include:

`/etc/passwd`
`/etc/group`
`/etc/hosts`
`/etc/hostname`
`/etc/resolv.conf`
`/etc/ssh/`

Note: The /etc directory ends up being extremely useful due to its content containing user configurations, networks, authentication, and more.

Example related to this:

`ls -lah /etc`

---

### /var

The /var directory stores data that is changed while the system is running. So, applications, system services, and databases can store operational information within /var.

It generally contains:

`/var/log`
`/var/cache`
`/var/lib`
`/var/tmp`

Also, if you need to look at a larger scale:

`ls -lah /var`

---

### /var/log

It is one of the most important directories from a cybersecurity perspective, as it traditionally contains system and application logs that are fundamental for anomaly or bug analysis.

Example:

`ls -lah /var/log`

Depending on the Linux distribution, this directory may contain information related to:

- authentication attempts;

- system services, application errors;

- package management;

- kernel activity;

- among others

---

### Practical Example of Navigation

A simple workflow for exploring a Linux system could be:

`pwd`
`ls -lah`
`cd /etc`
`pwd`
`ls -lah`
`cd /var/log`
`ls -lah`
`cd ~`

To search for SSH-related configuration files:

`find /etc -iname "*ssh*"`

To search for log files:

`find /var/log -type f -name "*.log"`

Note: These commands demonstrate how file navigation and discovery can be combined during system administration and troubleshooting.

---

## File Manipulation & File Analyzation

File manipulation within Linux is necessary for organizing and creating directories, thus making things easier for users already familiar with terminal tools.

### mkdir - Creating Directories

mkdir essentially means "make directory," its function is to create a new folder within Linux itself:

usually being:

`mkdir laboratory`

and this can be verified with `ls`, thus seeing "laboratory" written as such.

To enter it, as seen before, simply type `cd laboratory` and to confirm, type `pwd` -> (example: /home/user/laboratory)

Note: It is also possible to create several directories at once, for example:

`mkdir logs scripts evidence reports`

and then inside "laboratory" you will be able to see several folders like the ones mentioned above.

- Interesting detail:

If you run `mkdir cybersecurity/linux/fundamentals`, an error will occur if any of these folders do not exist.

At this point, it's important to add:

`mkdir -p cybersecurity/linux/fundamentals`

because the -p option will also create the necessary parent directories.

---

### touch - creating empty files and changing timestamps

The most commonly used command to create empty files is `touch`.

So, to better explain, an example would be:

`touch notes.txt`

and then, using `ls`, it's possible to see:

notes.txt

Following the same logic as shown in mkdir, it's also possible to create a sequence of files like this:

`touch notes.txt report.txt evidence.txt`

Thus creating a sequence of files as well.

Note: To quickly automate the creation of multiple files, you can write:

`touch file{1..5}.txt`

This will create multiple files: file.1.txt, file.2.txt, and so on until the fifth file. This ends up being a facilitator for enthusiasts or workers in the field. The only catch is that it doesn't create content within the file.

Timestamps in relation to touch

In simpler terms, it works as a quick analysis that you can request from any document via a command. Within this, you can analyze:

`mtime` - Modification Time: indicates when the file content was modified.

`atime` - Access Time: indicates when the file was accessed.

and `ctime` - Change Time: indicates when the file metadata was altered.

This ends up being very interesting for forensic areas, incidents, malware analysis, and other functions in the cybersecurity field.

To execute:

`stat report.txt`

This way, all the information I mentioned above can be retrieved.

Access, modify, change, Birth

- Using touch, it's possible to update this information.

`touch -a file.txt`

(thus changing the access time)

It is also possible to modify:

`touch -d "2026-01-01 00:01" evidence.txt`

Note: This is a way to change the time metadata. Therefore, during investigations, it is important not to automatically assume the timestamps of any file.

---

### cat - View and combine file contents

`cat` comes from `concatenate`, its main function is to read and concatenate files, although many people primarily use it to display the contents of files in the terminal.

So for example

`cat notes.txt`

will appear in Output -> `Laboratory`

---

### cp - copy files

cp comes from:

`copy`

it is used to copy files and directories, serving as a backup.

`cp report.txt`

or copying directory:

`cp documents backups/`

---

### mv - move

mv comes from `move`, it is mainly used to move files/directories and rename files/directories.

Example:

`mv report.txt documents/`

And then, in this way, the file `report.txt` becomes `documents/`

This can also be used to rename a file;

`mv report.txt final-report.txt`

and thus becoming the final file `final-report.txt`

---

### rm - remove

As the name suggests, this command removes files and directories. It's important to use it carefully because when using this command, the file is deleted without going through a recycle bin.

For example:

`rm file.txt`

This will delete the written file.

It's also possible to make it interactive and authenticate whether or not to delete the file by adding:

`rm -i file.txt`

This will cause the terminal to ask if it can remove what was written.

---

### less - Reading large files

Generally used to open files in the terminal without dumping the contents all at once.

For example:

`less Downloads/`

This allows you to view logs, configuration files, reports, very large files, and you can exit less when you enter it by pressing the `q` key.

---
### head - First lines
Used to show the beginning of a file.

Example:

`head file.txt`

note: This will show the first 10 lines of the file, which is useful for discovering how the file starts, its format, and if the content appears correctly.

### tail - last lines

Does the opposite of `head`, as it shows the last 10 lines of a file, thus being useful for a similar purpose to head.

`tail file.txt`

---

### grep - pattern search

This command is important when it comes to Linux administration or searching and filtering text within files and command outputs.

The most basic use would be:

`grep "ERROR" system.log`

This will search all lines in `system.log` that contain the keyword: ERROR.

It essentially works like a search tool for information that the user wants to filter.

---