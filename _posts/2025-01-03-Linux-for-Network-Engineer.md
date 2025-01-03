---
layout: post
title: Linux for Network Engineer
subtitle: 
tags: [Linux]
#image: /img/markdown.jpg
#bigimg: /img/markdown.jpg
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---

- [What is a Kernel, and What does it Do?](#what-is-a-kernel-and-what-does-it-do)
- [What is an Operating System?](#what-is-an-operating-system)
- [What is the boot process ?](#what-is-the-boot-process-)
- [What is Linux Daemon?](#what-is-linux-daemon)
- [User Space vs Kernel Space](#user-space-vs-kernel-space)
- [How is Linux Used in the Enterprise?](#how-is-linux-used-in-the-enterprise)
- [How do I know What Type of Linux I am Using?](#how-do-i-know-what-type-of-linux-i-am-using)
  - [Where do I find the things ?](#where-do-i-find-the-things-)
  - [/bin, /sbin, /usr/sbin](#bin-sbin-usrsbin)
  - [/dev](#dev)
  - [/etc](#etc)
  - [/home](#home)
  - [/var](#var)
- [Where are the applications, and how do I run them?](#where-are-the-applications-and-how-do-i-run-them)


# What is a Kernel, and What does it Do?
The **kernel** is the special piece of the operating system that controls 
- the CPU hardware
- allocates memory 
- accesses data
- schedules processes 
- runs the applications
- protects them from each other

It is the first program loaded on the computer when the computer starts up. The most critical pieces of code in the kernel are loaded into protected areas of memory so that they cant be overwritten by other applications running in the operating system.

# What is an Operating System?

Hardware -> Kernel -> Operating System => Libraries, System Daemons, Shells, Tools


# What is the boot process ?
Note: Explain the booting process here

# What is Linux Daemon?
A **system daemon** in Linux is typically a background system process that awaits a specific set of conditions before jumping into action.

For example, your Linux system may have a daemon called *sshd*. This system daemon runs in the background and accepts authorized incoming requests to log into the Linux host.

System daemons do not interact with users and are not typically under the direct control of users, but rather of the system itself. 

# User Space vs Kernel Space 

Operating systems all execute their kernel in protected and restricted memory that is called **kernel space** to prevent the kernel from terminating and crashing the system. 

When a user runs an application or tool, that application or tool executes in what is called **user space**. By running these application seperate from kernel space, they cant tamper with the kernel resources and cause the system to panic(crash).

All applications, even system daemon processes that perform critical operating system functions, must make what is called a **system call** to the kernel space in order to access system resources such as *memory* or *network devices*.

Separating between user space and kernel space  is made to ensure that Linux is as reliable and secure an operating system as possible.

**Note:**  Figure 1.4

# How is Linux Used in the Enterprise?
- Automation and orchestration
- Server Virtualisation

The software that allows VMs to function is called a *hypervisor*. Linux includes an excellent hypervisor called **KVM**.

- Private Cloud
- Big Data
- Containers

# How do I know What Type of Linux I am Using?

The **uname** command shows the basic type of operating system you are using.

```bash
utku@# uname -a
Linux vmi1580390.contaboserver.net 5.15.0-113-generic #123-Ubuntu SMP Mon Jun 10 08:16:17 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```
**hostnamectl** command shows you the hostname of the linux server as well as the other system informations.

```bash
# hostnamectl 
 Static hostname: debian
       Icon name: computer-vm
         Chassis: vm
      Machine ID: 5120104a8a29sdfsdf190623b65910546
         Boot ID: f311csdfsdfsdfe4a06b274f2148c994dee
  Virtualization: kvm
Operating System: Ubuntu 22.04.4 LTS               
          Kernel: Linux 5.15.0-113-generic
    Architecture: x86-64
 Hardware Vendor: QEMU
  Hardware Model: Standard PC _i440FX + PIIX, 1996_
```

## Where do I find the things ? 

Files and folders. Interaction with and navigation of the linux file system is done up and down the tree with commands such as:

- pwd
- ls
- cd
- rm
- mkdir , rmdir

![Linux File System](../img/Linux_for_NE/linux_file_system.jpg)

## /bin, /sbin, /usr/sbin
Executable programs are stored.

## /dev 
Where files representing hardware devices are stored. Like floppy drive device /dev/fd0

## /etc
Where configuration files are stored.

## /home
Where user home directories are stored, one for each user

## /var
Where variable-length files, like log files, are stored.

# Where are the applications, and how do I run them?




