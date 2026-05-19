Linux Notes — Basic Commands and Comprehensive Overview
Table of Contents
Introduction to Linux
Linux Architecture
Linux Distributions
Linux File System Structure
Navigating the Terminal
File and Directory Management
Viewing and Editing Files
User and Permission Management
Process Management
Package Management
Networking Basics
Disk and Storage Management
Compression and Archiving
Environment Variables
Shell Scripting Basics
Important System Commands
Linux Services and Logs
SSH and Remote Access
Basic Security Practices
Linux Best Practices
Useful Command Cheat Sheet
Conclusion
---
1. Introduction to Linux
Linux is an open-source operating system based on Unix. It is widely used in:
Servers
Cloud computing
Cybersecurity
Embedded systems
Android devices
Software development
Key Features
Open-source
Multi-user
Multitasking
Secure and stable
Highly customizable
---
2. Linux Architecture
Linux architecture consists of:
```text
+----------------------+
|      Applications    |
+----------------------+
|         Shell        |
+----------------------+
|        Kernel        |
+----------------------+
|       Hardware       |
+----------------------+
```
Components
Kernel
The core of Linux that manages:
CPU
Memory
Devices
Processes
Shell
Interface between user and kernel.
Examples:
Bash
Zsh
Fish
File System
Organizes files and directories.
---
3. Linux Distributions
A Linux distribution (distro) is a version of Linux packaged with software.
Distribution	Purpose
Ubuntu	Beginner-friendly
Debian	Stable servers
Fedora	Latest technologies
Kali Linux	Penetration testing
Arch Linux	Advanced users
---
4. Linux File System Structure
Directory	Purpose
`/`	Root directory
`/home`	User files
`/etc`	Configuration files
`/bin`	Essential commands
`/var`	Logs and variable data
`/tmp`	Temporary files
`/usr`	User programs
---
5. Navigating the Terminal
Basic Commands
Show Current Directory
```bash
pwd
```
List Files
```bash
ls
ls -l
ls -a
```
Change Directory
```bash
cd foldername
cd ..
cd ~
```
---
6. File and Directory Management
Create File
```bash
touch file.txt
```
Create Folder
```bash
mkdir folder
```
Copy Files
```bash
cp file1.txt file2.txt
```
Move or Rename
```bash
mv old.txt new.txt
```
Delete File
```bash
rm file.txt
```
---
7. Viewing and Editing Files
Display File Content
```bash
cat file.txt
```
View Large Files
```bash
less file.txt
```
Text Editors
```bash
nano file.txt
vim file.txt
```
---
8. User and Permission Management
Create User
```bash
sudo useradd username
```
Set Password
```bash
sudo passwd username
```
Change Permissions
```bash
chmod 755 file.sh
```
Change Ownership
```bash
chown user:group file.txt
```
---
9. Process Management
View Processes
```bash
ps aux
```
Monitor Processes
```bash
top
```
Kill Process
```bash
kill PID
kill -9 PID
```
---
10. Package Management
Ubuntu/Debian
```bash
sudo apt update
sudo apt upgrade
sudo apt install nginx
```
Fedora
```bash
sudo dnf install nginx
```
---
11. Networking Basics
Check IP Address
```bash
ip a
```
Test Connectivity
```bash
ping google.com
```
Download Files
```bash
wget URL
curl URL
```
---
12. Disk and Storage Management
Disk Usage
```bash
df -h
```
Folder Size
```bash
du -sh folder
```
---
13. Compression and Archiving
Create Archive
```bash
tar -cvf archive.tar folder/
```
Extract Archive
```bash
tar -xvf archive.tar
```
Zip Files
```bash
zip archive.zip file.txt
```
---
14. Environment Variables
Create Variable
```bash
NAME="John"
echo $NAME
```
Export Variable
```bash
export NAME="John"
```
---
15. Shell Scripting Basics
Example Script
```bash
#!/bin/bash

echo "Hello World"
```
Make Executable
```bash
chmod +x script.sh
```
Run Script
```bash
./script.sh
```
---
16. Important System Commands
```bash
uname -a
whoami
date
uptime
free -h
```
---
17. Linux Services and Logs
Manage Services
```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl enable nginx
```
View Logs
```bash
journalctl
journalctl -f
```
---
18. SSH and Remote Access
SSH Connection
```bash
ssh user@ipaddress
```
Secure Copy
```bash
scp file.txt user@ip:/path
```
Generate SSH Key
```bash
ssh-keygen
```
---
19. Basic Security Practices
Update System
```bash
sudo apt update && sudo apt upgrade
```
Firewall
```bash
sudo ufw enable
sudo ufw status
```
---
20. Linux Best Practices
Avoid using root unnecessarily
Backup important files
Keep software updated
Learn command-line basics
Monitor logs regularly
---
21. Useful Command Cheat Sheet
Command	Description
`pwd`	Show current directory
`ls`	List files
`cd`	Change directory
`mkdir`	Create directory
`rm`	Remove files
`cp`	Copy files
`mv`	Move/rename files
`cat`	Display file
`top`	Monitor processes
`chmod`	Change permissions
`ping`	Test network
`ssh`	Remote login
---
22. Conclusion
Linux is a powerful and flexible operating system widely used in servers, cloud computing, software development, and cybersecurity.
Understanding Linux basics such as:
File systems
Commands
Permissions
Networking
Shell scripting
is essential for IT and system administration careers.
Regular practice with Linux commands and terminal usage improves proficiency and troubleshooting skills.
---
Additional Practice Commands
```bash
history
clear
man ls
echo "Hello Linux"
grep "word" file.txt
find /home -name "*.txt"
```
