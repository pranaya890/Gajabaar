# Week 0: Setting Up

## Goal

Set up the required environment for the program, including Kali Linux, Python development tools, Obsidian, and Git.


## 1. Installing Kali Linux

Kali Linux is a Debian-based Linux distribution commonly used for cybersecurity, penetration testing, digital forensics, and security research.

For now, I am installing Kali Linux will be installed as a virtual machine using VirtualBox.

### Why use a Virtual Machine?

A virtual machine allows Kali Linux to run inside another operating system without replacing the existing operating system.

This provides an isolated environment where I can practice Linux and cybersecurity concepts.

### Installation Method

- Virtualization software: VirtualBox
- Operating system: Kali Linux
- Installation type: Virtual Machine

### Installation Steps

### Virtual Box

``` Bash
sudo apt install virtualbox
#verification
VBoxManage --version
```

![[Pasted image 20260923123300.png]]

### Kali Linux
- Download kali linux iso file from https://www.kali.org/get-kali/#kali-platforms
- installer image > installer
- Step 3 — Import Kali into VirtualBox
1. Open **VirtualBox**.
2. Click **File → Import Appliance**.
3. Select the Kali VirtualBox file you downloaded. It will usually be an `.ova` file.
4. Click **Next**.
5. Review the VM settings.
6. Choose where you want the VM to be stored.
7. Click **Import**.
8. Wait for the import to finish.
>[!Important] use bridge adapter in network, so that kali machine gets seperate ip address and can be connected from any device on the network

-  Step 4 : Start Kali After the import:
1. Select the **Kali Linux** VM in VirtualBox.
2. Click **Start**.
3. Kali should boot to its login screen.
4. Log in using the credentials provided with the Kali image/download instructions
### Verification

I used the following commands to verify that Kali Linux was working correctly.

#### Check current user

```
whoami
```

This displays the username of the currently logged-in user.
``` Shell
┌──(ph3nix㉿kali)-[~]
└─$ whoami
ph3nix

```

#### Check Kali Linux version

```
cat /etc/os-release
```

This displays information about the operating system, including the distribution and version.

``` shell
┌──(ph3nix㉿kali)-[~]
└─$ cat /etc/os-release                              
PRETTY_NAME="Kali GNU/Linux Rolling"
NAME="Kali GNU/Linux"
VERSION_ID="2026.3"
VERSION="2026.3"
VERSION_CODENAME=kali-rolling
ID=kali
ID_LIKE=debian
HOME_URL="https://www.kali.org/"
SUPPORT_URL="https://forums.kali.org/"
BUG_REPORT_URL="https://bugs.kali.org/"
ANSI_COLOR="1;31"

```
#### Check the kernel

```
uname -a
```

This displays information about the Linux kernel and system architecture.

``` Shell
┌──(ph3nix㉿kali)-[~]
└─$ uname -a
Linux kali 6.19.14+kali-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.19.14-1+kali1 (2026-05-05) x86_64 GNU/Linux

```
#### Check network interfaces

```
ip addr
```

This displays the available network interfaces and their IP addresses.

``` shell
┌──(ph3nix㉿kali)-[~]
└─$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:4b:5e:0b brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.97/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0
       valid_lft 85501sec preferred_lft 85501sec
    inet6 2400:1a00:4b2a:3a21::31/128 scope global dynamic noprefixroute 
       valid_lft 899sec preferred_lft 899sec
    inet6 2400:1a00:4b2a:3a21:fc29:9cd3:5fd9:5f66/64 scope global temporary dynamic 
       valid_lft 716sec preferred_lft 716sec
    inet6 2400:1a00:4b2a:3a21:a00:27ff:fe4b:5e0b/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 716sec preferred_lft 716sec
    inet6 fe80::a00:27ff:fe4b:5e0b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
                                                  
```


### Installing Git

Git is required for version control and will be used to track the progress of my notes and submit the Obsidian vault through GitHub.

I installed Git using:

```
sudo apt install git
```

I then verified the installation:

```
git --version
```

``` Shell
sudo apt install git      
git is already the newest version (1:2.53.0-1).
Summary:                    
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 2

┌──(ph3nix㉿kali)-[~]
└─$ git --version
git version 2.53.0

```
### Result

Kali Linux was successfully installed in VirtualBox, updated, and configured with Git.

## What I Learned

- Kali Linux can be run safely inside a virtual machine.
- VirtualBox can be used to manage and run virtual machines.
- Basic Linux commands can be used to inspect the operating system and system configuration.
- `ip addr` can be used to inspect network interfaces.

### UV
- extremely fast python package and package  manager written in rust
- single tool replaces pip, pipx etc
- 10-100x faster than pip

### Installing UV
Docs: `https://docs.astral.sh/uv/getting-started/installation/?utm_source=chatgpt.com#standalone-installer`

Downloading Package
``` Shell
curl -LsSf https://astral.sh/uv/0.12.21/install.sh | sh
```

``` Shell
┌──(ph3nix㉿kali)-[~]
└─$ uv --version
uv 0.12.21 (x86_64-unknown-linux-gnu)
```

### Displaying Hello World using UV
