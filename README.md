# 42cursus - Born2beroot

## Table of Contents
1. [Introduction](#introduction)
    - [What is a Virtual Machine?](#Virtual-Machine)
    - [How do Virtual Machines work?](#Virtual-Machines-work)
    - [What is LVM?](#What-is-LVM?)
    - [What is AppArmor?](#What-is-AppArmor?)
    - [What is the difference between Apt and Aptitute?](#Apt-and-Aptitute)
    - [How to use SSH?](#How-to-use-SSH?)
    - [How to implement UFW with SSH?](#UFW-with-SSH)
    - [What is cron and what is wall?](#what-is-cron)
2. [Installation](#installation)
3. [*sudo*](#sudo)
    - [Step 1: Installing *sudo*](#step-1-installing-sudo)
    - [Step 2: Adding User to *sudo* Group](#step-2-adding-user-to-sudo-group)
    - [Step 3: Running *root*-Privileged Commands](#step-3-running-root-privileged-commands)
    - [Step 4: Configuring *sudo*](#step-4-configuring-sudo)
4. [SSH](#ssh)
    - [Step 1: Installing & Configuring SSH](#step-1-installing--configuring-ssh)
    - [Step 2: Installing & Configuring UFW](#step-2-installing--configuring-ufw)
    - [Step 3: Connecting to Server via SSH](#step-3-connecting-to-server-via-ssh)
5. [User Management](#user-management)
    - [Step 1: Setting Up a Strong Password Policy](#step-1-setting-up-a-strong-password-policy)
       - [Password Age](#password-age)
       - [Password Strength](#password-strength)
    - [Step 2: Creating a New User](#step-2-creating-a-new-user)
    - [Step 3: Creating a New Group](#step-3-creating-a-new-group)
6. [*cron*](#cron)
    - [Setting Up a *cron* Job](#setting-up-a-cron-job)
7. [Monitoring](#monitoring)
8. [Bonus](#bonus)
    - [Installation](#1-installation)
    - [Linux Lighttpd MariaDB PHP *(LLMP)* Stack](#2-linux-lighttpd-mariadb-php-llmp-stack)
       - [Step 1: Installing Lighttpd](#step-1-installing-lighttpd)
       - [Step 2: Installing & Configuring MariaDB](#step-2-installing--configuring-mariadb)
       - [Step 3: Installing PHP](#step-3-installing-php)
       - [Step 4: Downloading & Configuring WordPress](#step-4-downloading--configuring-wordpress)
       - [Step 5: Configuring Lighttpd](#step-5-configuring-lighttpd)
    - [File Transfer Protocol *(FTP)*](#3-file-transfer-protocol-ftp)
       - [Step 1: Installing & Configuring FTP](#step-1-installing--configuring-ftp)
       - [Step 2: Connecting to Server via FTP](#step-2-connecting-to-server-via-ftp)

8. [Submission and peer-evaluation for 1337/42 Students](#peereval)

9. [evalknowledge.txt](#evalknowledge)

## Introduction
You will create your first machine in VirtualBox (or UTM if you can’t use VirtualBox) under specific instructions. Then, at the end of this project, you will be able to set up your own operating system while implementing strict rules.

### <a name="Virtual-Machine">What is a Virtual Machine?</a>
A virtual machine is a **software capable of installing an Operating System within itself, making the OS think that it is hosted on a real computer**. With virtual machines we can create virtual devices that will behave in the same way as physical devices, using their own CPU, memory, network interface and storage. This is possible because **the virtual machine is hosted on a physical device**, which is the one that provides the hardware resources to the VM. The software program that creates virtual machines is **the hypervisor**. The hypervisor is responsible for isolating the VM resources from the system hardware and making the necessary implementations so that the VM can use these resources.<br>
The devices that provide the hardware resources are called **host machines or hosts**. The different virtual machines that can be assigned to a host are called **guests or guest machines**. The hypervisor uses a part of the host machine's CPU, storage, etc., and distributes them among the different VMs.<br>
<br>
There can be multiple virtual machines on the same host and each of these will be isolated from the rest of the system. Thanks to this, we can run different operating systems on our machines. For each virtual machine, we can run a different operating system distribution. Each of these operating systems will behave as if they were hosted on a physical device, so we will have the same experience when using an OS on a physical machine and on a virtual machine.

### <a name="Virtual-Machines-work">How do Virtual Machines work?</a>
Virtualization allows us to share a system with multiple virtual environments. The hypervisor manages the hardware system and separates the physical resources from the virtual environments. **The resources are managed following the needs, of the host to the guests.** When a user from a VM does a task that requires additional resources from the physical environment, the hypervisor manages the request so that the guest OS can access the resources of the physical environment.<br>
Once we know how they work, it is a good idea to see all the advantages we get from using virtual machines:
<ul>
 <li>Different guest machines hosted on our computer <b>can run different operating systems</b>, so we will have different OS working on the same machine.</li>
   <li>They provide an environment in which <b>to safely test unstable programs</b> to see if they will affect the system or not.</li>
   <li>We get <b>better use of shared resources.</b></li>
   <li>We <b>reduce costs</b> by reducing physical architecture.</li>
   <li>They are <b>easy to implement</b> because they provide mechanisms to clone a virtual machine to another physical device.</li>
</ul>
