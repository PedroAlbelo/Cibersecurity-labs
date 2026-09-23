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