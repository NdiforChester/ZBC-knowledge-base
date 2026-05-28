# Linux Fundamentals

Linux is an open-source operating system family based on Unix ideas. It is widely used for servers, cloud infrastructure, networking devices, cybersecurity tools, containers, embedded systems, and developer workstations.

New engineers should learn Linux because most production infrastructure depends on it. AWS EC2 instances, Docker containers, Kubernetes nodes, CI/CD runners, and many security tools run on Linux.

## 1. What Linux Is

Linux usually refers to a complete operating system distribution built around the Linux kernel.

The kernel is the core part of the operating system. It manages hardware, memory, processes, filesystems, devices, and networking. A distribution adds user tools, package managers, system services, shells, and default configuration.

Common Linux distributions include:

| Distribution | Common use |
| --- | --- |
| Ubuntu | Beginner-friendly desktops and servers |
| Debian | Stable servers |
| Red Hat Enterprise Linux | Enterprise production systems |
| Fedora | Newer Linux technologies |
| CentOS Stream | Red Hat-related server learning |
| Kali Linux | Security testing labs |

## 2. Why Linux Matters

Linux is important in engineering because it is:

- Open source and customizable.
- Stable for long-running servers.
- Efficient on small or large systems.
- Secure through users, groups, permissions, and process isolation.
- Automation-friendly through the command line and scripting.
- Common across cloud, DevOps, networking, and security roles.

## 3. Linux Architecture

Linux can be understood as layers:

```text
Applications
Shell and system tools
Kernel
Hardware
```

### Hardware

Hardware includes CPU, memory, disks, network cards, keyboards, and other physical or virtual devices.

### Kernel

The kernel manages system resources and provides controlled access to hardware. It handles:

- Process scheduling.
- Memory management.
- Device drivers.
- Filesystems.
- Network communication.
- Security boundaries.

### Shell

The shell is the command interpreter. It accepts commands from users or scripts and asks the operating system to perform actions.

Common shells include:

- Bash
- Zsh
- Fish

### Applications

Applications are the programs users run, such as `ssh`, `nginx`, `docker`, `vim`, browsers, and monitoring tools.

## 4. Filesystem Structure

Linux organizes files from a single root directory: `/`.

| Directory | Purpose |
| --- | --- |
| `/` | Root of the filesystem |
| `/home` | User home directories |
| `/etc` | System and application configuration |
| `/bin` | Essential user commands |
| `/sbin` | System administration commands |
| `/var` | Logs, caches, and changing application data |
| `/tmp` | Temporary files |
| `/usr` | Installed programs and shared resources |
| `/opt` | Optional third-party applications |

Linux treats many things as files, including regular files, directories, devices, and process information. This makes system behavior consistent and scriptable.

## 5. Essential Commands

### Navigation

```bash
pwd
ls
ls -la
cd /etc
cd ..
cd ~
```

### File and Directory Management

```bash
touch notes.txt
mkdir projects
cp notes.txt backup-notes.txt
mv backup-notes.txt projects/
rm notes.txt
rm -r old-folder
```

Use `rm` carefully. Deleted files are not moved to a recycle bin by default.

### Viewing Files

```bash
cat file.txt
less /var/log/syslog
head file.txt
tail file.txt
tail -f /var/log/syslog
```

### Searching

```bash
grep "error" app.log
find /var/log -name "*.log"
```

## 6. Users, Groups, and Permissions

Linux is a multi-user system. Users and groups control who can read, write, or execute files.

View file permissions:

```bash
ls -l script.sh
```

Example output:

```text
-rwxr-xr-- 1 alice devops 1200 May 28 10:00 script.sh
```

Permission groups:

- Owner permissions.
- Group permissions.
- Other user permissions.

Permission types:

- `r`: read.
- `w`: write.
- `x`: execute.

Common permission commands:

```bash
chmod 755 script.sh
chmod +x deploy.sh
chown alice:devops notes.txt
```

Use `sudo` when a command requires administrative privileges:

```bash
sudo systemctl restart nginx
```

## 7. Processes and Services

A process is a running program. Linux engineers frequently inspect and manage processes.

```bash
ps aux
top
kill <pid>
```

Services are background programs managed by the system. On many modern Linux distributions, `systemd` manages services.

```bash
systemctl status nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl restart nginx
```

## 8. Packages

Package managers install, update, and remove software.

Ubuntu and Debian:

```bash
sudo apt update
sudo apt install nginx
sudo apt remove nginx
```

Fedora and Red Hat-related systems:

```bash
sudo dnf install nginx
sudo dnf remove nginx
```

## 9. Networking Basics

Common networking commands:

```bash
ip addr
ping example.com
curl https://example.com
ss -tulpn
traceroute example.com
```

Useful checks:

- Use `ip addr` to confirm the machine has an IP address.
- Use `ping` to test basic network reachability.
- Use `curl` to test HTTP services.
- Use `ss -tulpn` to see listening ports.

## 10. Logs and Troubleshooting

Logs help engineers diagnose failures.

Common log locations:

```text
/var/log/syslog
/var/log/auth.log
/var/log/nginx/
/var/log/messages
```

Useful commands:

```bash
journalctl -xe
journalctl -u nginx
tail -f /var/log/syslog
```

## 11. Beginner to Intermediate Practice Path

1. Navigate the filesystem without a graphical interface.
2. Create, move, copy, and delete files safely.
3. Read logs with `less`, `tail`, and `journalctl`.
4. Explain permissions from `ls -l` output.
5. Install and manage a package.
6. Start, stop, and inspect a service.
7. Write a small Bash script.
8. Troubleshoot a network or service issue from the command line.

## 12. Common Mistakes to Avoid

- Running commands with `sudo` without understanding the effect.
- Using `rm -rf` carelessly.
- Editing production configuration without a backup.
- Ignoring logs when troubleshooting.
- Hardcoding secrets in scripts.
- Changing permissions to `777` instead of fixing ownership or specific access.
