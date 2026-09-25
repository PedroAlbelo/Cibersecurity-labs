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

### PWD - Print working directory

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