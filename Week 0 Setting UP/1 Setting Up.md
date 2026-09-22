
## Kali Linux 
Kali Linux is a Debian-based Linux distribution commonly used for cybersecurity, penetration testing, digital forensics, and security research.

## My Setup

Kali Linux is already installed on my system, so I did not need to perform a fresh installation for this program.

## Verify the Installation

Check the Kali version:

```bash
cat /etc/os-release
```

![[Pasted image 20260922223250.png]]

Check the kernel:

```bash
uname -a
```
![[Pasted image 20260922223356.png]]
Check the current user:

```bash
whoami
```

![[Pasted image 20260922223407.png]]

## Notes

My existing Kali installation can be used for the program. I will use the terminal extensively for Linux commands, Git, Python development, and cybersecurity exercises.

## 2. Updating the system

``` Bash
sudo apt update sudo apt -y upgrade
```

![[Pasted image 20260922223609.png]]
![[Pasted image 20260922223609.png]]

## 3. Installing uv
- `uv` is a fast Python package and project manager developed by Astral. It can manage Python versions, virtual environments, dependencies, and project execution.
- 