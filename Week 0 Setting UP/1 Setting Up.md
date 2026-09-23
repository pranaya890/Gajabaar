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

_After installation, I will verify that Kali Linux is working correctly._