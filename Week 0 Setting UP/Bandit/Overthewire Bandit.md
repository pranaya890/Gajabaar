
## Level 0

### Challenge

The goal of Level 0 is to log in to the Bandit server using SSH.

The connection details provided by OverTheWire are:

- Host: `bandit.labs.overthewire.org`
    
- Port: `2220`
    
- Username: `bandit0`
    

### Password
`bandit0`

### Solving Steps

1. Opened a terminal
2. Connected to the Bandit server using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

3. Entered the password provided by OverTheWire for Level 0.
4. Successfully logged into the Bandit server.

### Commands Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### What I Learned

- SSH is used to securely connect to a remote computer.
- The `ssh` command follows the general format:

```bash
ssh username@hostname -p port
```

- `bandit0` is the username.
- `bandit.labs.overthewire.org` is the remote host.
- `2220` is the SSH port used by Bandit instead of the default SSH port `22`.
- After connecting, commands are executed on the remote Bandit machine rather than my local Kali system.

---

## Bandit Level 0 → Level 1

## Level Goal

The password for the next level is stored in a file called `readme` located in the home directory.

The password found in this file is used to log into `bandit1` using SSH on port `2220`.

## Password

## Solving Steps

### 1. Log into Bandit Level 0

I connected to the Bandit server using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### 2. Check the current directory

```bash
pwd
```

The home directory contains the file needed for the challenge.

### 3. List the files

```bash
ls
```

The output showed a file named:

```text
readme
```

### 4. Read the file

I used `cat` to display its contents:

```bash
cat readme
```

The output contained the password for the next level.

### 5. Log into the next level

I used the discovered password to log into `bandit1`:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

## Commands Used

```bash
pwd
ls
cat readme
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

## What I Learned

- `pwd` displays the current working directory.
    
- `ls` lists files and directories.
    
- `cat` can be used to display the contents of a file.
    
- SSH can be used to connect to the next Bandit level.
    
- The Bandit challenges progressively introduce basic Linux commands and concepts.

Flag: `6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`

---
# Bandit Level 1 → Level 2

## Level Goal

The password for the next level is stored in a file called `-` located in the home directory.

The password found in this file is used to log into `bandit2` using SSH on port `2220`.

## Solving Steps

### 1. Log into Bandit Level 1

I connected to the Bandit server using SSH:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

### 2. List the files

```bash
ls
```

The output showed a file named:

```text
-
```

### 3. Read the file

A filename beginning with `-` can be interpreted as a command-line option.

Instead of:

```bash
cat -
```

I used an explicit path to specify that `-` is a file in the current directory:

```bash
cat ./-
```

This displayed the password for the next level.

### 4. Log into the next level

I used the discovered password to log into `bandit2`:

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

## Commands Used

```bash
ls
cat ./-
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

## What I Learned

- A Linux filename can begin with a hyphen (`-`).
- Many command-line tools interpret arguments beginning with `-` as options.
- `./-` explicitly refers to a file named `-` in the current directory.
- `cat ./-` can be used to read the contents of this file.
- SSH is used to move between the different Bandit levels.

Flag: `PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

# Bandit Level 2 → Level 3

## Level Goal

The password for the next level is stored in a file named `spaces in this filename` in the home directory.

## Solving Steps

1. Logged in as `bandit2` using SSH.
    
2. Listed the files in the home directory.
    
3. Identified the file whose name contains spaces.
    
4. Used quotes around the filename so the shell treated it as a single filename.
    
5. Read the file and obtained the password for the next level.
    
6. Logged in as `bandit3`.
    

## Commands Used

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
ls
cat "spaces in this filename"
cat ~/--spaces\ in\ this\ filename-- 
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

## What I Learned

- Filenames can contain spaces.
    
- The shell normally treats spaces as separators between arguments.
    
- Quoting a filename allows spaces to be treated as part of the filename.
    
- Double quotes can be used to work with filenames containing spaces.
    

## Flag
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME

# Bandit Level 3 → Level 4

## Level Goal

The password for the next level is stored in a hidden file inside the `inhere` directory.

## Solving Steps

1. Logged in as `bandit3` using SSH.
    
2. Listed the contents of the home directory.
    
3. Entered the `inhere` directory.
    
4. Listed the hidden files using `ls -la`.
    
5. Found the hidden file.
    
6. Read the file to obtain the password for the next level.
    
7. Logged in as `bandit4`.
    

## Commands Used

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -la
cat ...Hiding-From-You
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

## What I Learned

- Files beginning with `.` are hidden files in Linux.
    
- `ls` does not normally display hidden files.
    
- `ls -la` displays both normal and hidden files.
    
- `cd` is used to change directories.
    
- Hidden files can still be accessed normally when their filename is known.
    

## Flag
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq

