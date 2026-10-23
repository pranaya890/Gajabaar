# OverTheWire Bandit — Levels 0 to 30

## Bandit Level 0 → Level 1

### Level Goal

The password was stored in a file called `readme` in the home directory.

### Solving Steps
1. Connected to the Bandit server using SSH.
2. Used `ls` to see the files.
3. Found `readme` and read it with `cat`.
4. Used the password to log in as `bandit1`.

### Commands Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

### What I Learned
This was my introduction to the Bandit environment. I practiced basic SSH login and learned how `ls` and `cat` are used from the terminal.

### Flag

`6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`

## Bandit Level 1 → Level 2

### Level Goal

The password was stored in a file named `-`.

### Solving Steps

1. Logged in as `bandit1`.
2. Listed the files and found `-`.
3. Used `./-` instead of simply `-`.
4. Read the file and used the result to log in as `bandit2`.

### Commands Used

```bash
ls
cat ./-
```

### What I Learned

A filename beginning with `-` can be interpreted as an option by a command. Using `./` makes it clear that I am referring to a file in the current directory.

### Flag

`PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

## Bandit Level 2 → Level 3

### Level Goal

The password was stored in a file whose name contained spaces.

### Solving Steps

1. Listed the files in the home directory.
2. Found the file with spaces in its name.
3. Put the filename inside quotes so the shell treated it as one argument.
4. Read the file and used the password to continue.

### Commands Used

```bash
ls
cat "spaces in this filename"
```

### What I Learned

The shell normally treats spaces as separators. Quoting a filename is an easy way to work with filenames containing spaces.

### Flag

`7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME`

## Bandit Level 3 → Level 4

### Level Goal

The password was inside a hidden file in the `inhere` directory.

### Solving Steps

1. Entered the `inhere` directory.
2. Used `ls -la` to include hidden files.
3. Found the hidden file.
4. Read it to get the next password.

### Commands Used

```bash
cd inhere
ls -la
cat ...Hiding-From-You
```

### What I Learned

Linux hides files whose names start with `.` from a normal `ls` listing. The `-a` option displays them.

### Flag

`xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq`

## Bandit Level 4 → Level 5

### Level Goal

The password was in the only human-readable file inside `inhere`.

### Solving Steps

1. Entered `inhere`.
2. Checked the files to find the readable one.
3. Used text searching to identify the 32-character password.
4. Read the correct file.

### Commands Used

```bash
cd inhere
grep -rEo '\b[a-zA-Z0-9]{32}\b' .
```

### What I Learned

I learned that tools such as `grep` can be combined with regular expressions to search through many files instead of checking them one by one.
Resources used: https://regex101.com/ and used hit and trial to write the regular expression

### Flag

`6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG`

## Bandit Level 5 → Level 6

### Level Goal

The password was in a file somewhere under `inhere` with specific properties: 1033 bytes and not executable.

### Solving Steps

1. Searched recursively through the directory.
2. Used file properties to narrow down the results.
3. Identified the correct file.
4. Read the file.

### Commands Used

```bash
cd inhere
find . -type f -size 1033c ! -executable
cat <file>
```

### What I Learned

`find` is very useful when a file is hidden somewhere in a large directory structure. It can filter files by size, type, permissions and other properties.

### Flag

`pXa26xhMWaC2SvDotA4r9EgZkulOeSBW`

## Bandit Level 6 → Level 7

### Level Goal

The password was stored somewhere on the system in a file owned by `bandit7`, belonging to group `bandit6`, and exactly 33 bytes long.

### Solving Steps

1. Searched the whole filesystem with `find`.
2. Added filters for the owner, group and file size.
3. Redirected permission errors to `/dev/null`.
4. Read the matching file.

### Commands Used

```bash
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

### What I Learned

I learned how `find` can search the entire filesystem and how `2>/dev/null` can keep permission errors from cluttering the output.

### Flag

`Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3`

## Bandit Level 7 → Level 8

### Level Goal

The password was stored in `data.txt` next to the word `millionth`.

### Solving Steps

1. Opened `data.txt` with a text search.
2. Used `grep` to search for `millionth`.
3. Took the value from that line.

### Commands Used

```bash
grep "millionth" data.txt
```

### What I Learned

`grep` is one of the most useful commands for quickly finding specific information inside large text files.

### Flag

`VR1ljMayciFxbnUokuQmJFw6QC9VKtub`

## Bandit Level 8 → Level 9

### Level Goal

The password was the only line in `data.txt` that appeared once.

### Solving Steps

1. Sorted the file so identical lines were next to each other.
2. Used `uniq -u` to show the unique line.
3. Used that value for the next login.

### Commands Used

```bash
sort data.txt | uniq -u
```

### What I Learned

`uniq` works best when duplicate lines are next to each other, which is why `sort` is commonly used before it.

### Flag

`EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl`

## Bandit Level 9 → Level 10

### Level Goal

The password was hidden among readable strings in a file containing binary-looking data.

### Solving Steps

1. Used `strings` to extract readable text.
2. Filtered the result for lines containing `=`.
3. Found the password among the readable strings.

### Commands Used

```bash
strings data.txt | grep "="
```

### What I Learned

`strings` is useful when a file contains binary data but also has readable text hidden inside it.

### Flag

`pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro`

## Bandit Level 10 → Level 11

### Level Goal

The password was stored as Base64-encoded text in `data.txt`.

### Solving Steps

1. Read the contents of `data.txt`.
2. Recognized that the data was Base64 encoded.
3. Used the `base64` command with the decode option.

### Commands Used

```bash
base64 -d data.txt
```

### What I Learned

Base64 is an encoding method, not encryption. The `base64 -d` command can decode it back to readable text.

### Flag

`GROozWPO8QyN0mGrjUkID0WCYkZiQxrN`

## Bandit Level 11 → Level 12

### Level Goal

The password was encoded using ROT13.

### Solving Steps

1. Read the encoded text.
2. Recognized the ROT13 pattern.
3. Used `tr` to rotate the alphabet back by 13 positions.

### Commands Used

```bash
cat data.txt
cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
```

Alternatively I used cyberchef and dcode.fr to directly convert ROT13 
### What I Learned

ROT13 is a simple substitution cipher where every letter is shifted by 13 positions. `tr` can be used to perform this character substitution.

### Flag

`qQYQiHOBPR8zR61qxYqX45quvihF2uzk`

## Bandit Level 12 → Level 13

### Level Goal

The password was inside a file that had been converted to a hexdump and then compressed several times.

### Solving Steps

1. Created a temporary directory for the work.
2. Reversed the hexdump using `xxd -r`.
3. Used `file` to identify the compression format.
4. Renamed the file when necessary so the decompression tools recognized it.
5. Repeated the process through the gzip, bzip2 and tar layers.
6. Read the final output.

### Commands Used

```bash
mktemp -d
cp data.txt /tmp/<directory>
cd /tmp/<directory>
xxd -r data.txt data
file data
mv data data.gz
gzip -d data.gz
```

The same `file` → rename → decompress/extract process was repeated for the remaining layers using `gzip`, `bzip2` and `tar`.

### What I Learned

This level taught me how to identify file types and work through multiple compression layers. It also showed me why `file` is useful when I don't know what a file actually contains.

### Flag

`aaWecNkG4FhxJQxz07uiwzVP6bJiYS65`

## Bandit Level 13 → Level 14

### Level Goal

Instead of giving a normal password, the level provided an SSH private key for accessing `bandit14`

### Solving Steps

1. Found `sshkey.private`.
2. Used the private key for SSH authentication.
3. Logged in as `bandit14`.
4. Read the password file from the `bandit14` account.

### Commands Used

```bash
chmod 700 sshkey.private
ssh bandit.labs.overthewire.org -p 2220 -l bandit14 -i sshkey.private
cat /etc/bandit_pass/bandit14
```

### What I Learned

SSH does not always require a password. A private key can also be used for authentication. I also learned that SSH expects private keys to have restricted permissions.

### Flag

`aaWecNkG4FhxJQxz07uiwzVP6bJiYS65`

## Bandit Level 14 → Level 15

### Level Goal

The current password had to be submitted to a service running on localhost port `30000`.

### Solving Steps

1. Connected to the service using Netcat.
2. Entered the current password.
3. The service returned the password for the next level.

### Commands Used

```bash
nc localhost 30000
```

### What I Learned

I got some practical experience with Netcat and learned how a client can communicate with a service listening on a particular TCP port.

### Flag

`pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7`

## Bandit Level 15 → Level 16

### Level Goal

The password had to be submitted to port `30001`, but this time the connection used SSL/TLS.

### Solving Steps

1. Connected to the SSL-enabled service.
2. Submitted the current password.
3. Received the next password.

### Commands Used

```bash
ncat --ssl localhost 30001
```

### What I Learned

A normal Netcat connection is not enough when the service expects SSL/TLS. I learned how `ncat --ssl` can establish an encrypted connection.

### Flag

`kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V`

## Bandit Level 16 → Level 17

### Level Goal

I had to find an open port between `31000` and `32000`, identify the SSL service and use it to obtain an SSH private key.

### Solving Steps

1. Scanned the port range with Nmap.
2. Identified the listening services.
3. Tested the appropriate port using SSL.
4. Saved the returned private key.
5. Used the key to access `bandit17`.
    

### Commands Used

```bash
nmap localhost -p 31000-32000
ncat --ssl localhost 31790
```

### What I Learned

This level gave me practice with port scanning and service identification. It also connected the earlier SSH-key concept with network enumeration.

### Flag

`pWXMAZoxGC8JmDMfmT5MGEsobMM3vnj2`

## Bandit Level 17 → Level 18

### Level Goal

The password was the new entry that appeared when comparing `passwords.old` and `passwords.new`.

### Solving Steps

1. Compared the two files.
2. Used sorting and `uniq` to identify the different lines.
3. Identified the new password.

### Commands Used

```bash
sort passwords.new passwords.old | uniq -u
```

### What I Learned

`diff`, `sort` and `uniq` are useful when comparing large files and looking for small changes.

### Flag

`OQxXZjELndr90zuhOTDYBEomI0SZITXI`

## Bandit Level 18 → Level 19

### Level Goal

The normal login shell immediately logged me out, so I had to execute a command without starting the normal interactive Bash shell.

### Solving Steps

1. Connected through SSH while specifying `/bin/sh`.
2. Listed the files.
3. Read `readme`.
4. Used the resulting password to continue.

### Commands Used

```bash
ssh bandit.labs.overthewire.org -p 2220 -l bandit18 /bin/sh
ls
cat readme
```

### What I Learned

I learned that SSH can execute a command directly instead of always opening the user's default interactive shell. This was also a good introduction to how shell startup files can affect a login.

### Flag

`KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI`

## Bandit Level 19 → Level 20

### Level Goal

A setuid program called `bandit20-do` could execute commands with the privileges of `bandit20`.

### Solving Steps

1. Found the `bandit20-do` executable.
2. Tested what it could do.
3. Used it to read the `bandit20` password file.

### Commands Used

```bash
ls
./bandit20-do id
./bandit20-do cat /etc/bandit_pass/bandit20
```

### What I Learned

This was my first direct experience with a setuid executable. I learned that file permissions can cause a program to run with the privileges of its owner.

### Flag

`4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA`

## Bandit Level 20 → Level 21

### Level Goal

A setuid program called `suconnect` connected to a local port and returned the next password if the correct current password was supplied.

### Solving Steps

1. Opened a listener using Netcat.
2. Sent the current password through the listener.
3. Used a second terminal to run `suconnect`.
4. Received the next password from the service.

### Commands Used

Terminal 1:

```bash
echo "<current-password>" | nc -lvp 12355
```

Terminal 2:

```bash
./suconnect 12355
```

### What I Learned

I learned how a simple TCP listener works and how two local processes can communicate through a port.

### Flag

`bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY`

## Bandit Level 21 → Level 22

### Level Goal

A cron job was automatically running a script and storing the next password somewhere in `/tmp`.

### Solving Steps

1. Checked the cron configuration.
2. Found the script being executed.
3. Read the script to understand what it did.
4. Located the temporary file containing the password.

### Commands Used

```bash
cd /etc/cron.d
cat cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t706lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

### What I Learned

I learned how cron jobs work and how reading the script behind an automated task can reveal what the system is doing.

### Flag

`RYVux2rHEm9tiXHmLFzuR7Vhx6AZQMEz`

## Bandit Level 22 → Level 23

### Level Goal

Another cron job generated the password file name using an MD5 hash.

### Solving Steps

1. Read the cron configuration.
2. Read the script being executed.
3. Followed the script's logic to see how the filename was generated.
4. Recreated the MD5 calculation.
5. Read the resulting file.

### Commands Used

```bash
cat /etc/cron.d/cronjob_bandit23
cat /usr/bin/cronjob_bandit23.sh
echo "I am user bandit23" | md5sum
cat /tmp/<generated-file>
```

### What I Learned

This level made me look more closely at scripts instead of blindly running commands. I also practiced using `md5sum` from the terminal.

### Flag

`gKXDTAXnIz3OBxiPjRZ2uqutUlPZrBsw`

## Bandit Level 23 → Level 24

### Level Goal

A cron job executed scripts placed in a particular directory as `bandit24`.

### Solving Steps

1. Read the cron configuration and the script.
2. Understood where the cron job looked for scripts.
3. Created a small shell script that copied the `bandit24` password to a temporary location.
4. Made the script executable.
5. Waited for the cron job to execute it.
6. Read the resulting file.

### Commands Used

```bash
cat /etc/cron.d/cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh
nano /var/spool/bandit24/foo/myjob.sh
chmod +x /var/spool/bandit24/foo/myjob.sh
cat /tmp/bandit24_password
```

### What I Learned

I learned how scheduled jobs can execute scripts automatically and why understanding the execution user and file permissions is important.

### Flag

`hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv`

## Bandit Level 24 → Level 25

### Level Goal

A service on port `30002` required the current password together with a four-digit PIN.

### Solving Steps

1. Connected to the service to understand its expected input.
2. Generated the possible four-digit PIN values.
3. Combined them with the current password.
4. Sent the inputs to the service.
5. Identified the successful response.

### Commands Used

```bash
nc localhost 30002
```

### What I Learned

This level showed me how automation can handle repetitive input in a controlled CTF environment. I also practiced shell loops and Netcat.

### Flag

`SoHfqMOEqIX2IYKVciZxvgpR9a2Djx4P`

## Bandit Level 25 → Level 26

### Level Goal

The `bandit26` account used a restricted shell, so I had to find a way to obtain a usable shell.

### Solving Steps

1. Found the SSH private key for `bandit26`.
2. Checked the account's configured shell.
3. Investigated the `showtext` script.
4. Used the behavior of `more` to reach an editor.
5. Used the editor's shell functionality to obtain a shell
6. Read the password for `bandit26`.

### Commands Used

```bash
cat /etc/passwd | grep bandit26
cat /usr/bin/showtext
ssh -i bandit26.sshkey bandit26@localhost -p 2220
```

Inside the editor:

```vim
:set shell=/bin/bash
:shell
```

Then:

```bash
cat /etc/bandit_pass/bandit26
```

### What I Learned

This was one of the more interesting levels because the main challenge was understanding how the restricted environment worked. I learned that programs such as editors can have shell-related functionality.

### Flag

`jHdv2ELQhT22BkprMNDjybZDAkw1zeBJ`

## Bandit Level 26 → Level 27

### Level Goal

After getting a shell as `bandit26`, I had to use the provided setuid program to access the `bandit27` password.

### Solving Steps

1. Obtained a shell as `bandit26`.
2. Found `bandit27-do`.
3. Used the program to execute `cat` with the required privileges.
4. Retrieved the next password.

### Commands Used

```bash
ls
./bandit27-do id
./bandit27-do cat /etc/bandit_pass/bandit27
```

### What I Learned

This reinforced the concept of setuid programs and showed me how the same privilege mechanism can appear in different forms.

### Flag

`STJLJBRRphMxKB392CT4iOr5CbzPU9ER`

## Bandit Level 27 → Level 28

### Level Goal

The password was hidden inside a Git repository.

### Solving Steps

1. Created a temporary directory.
2. Cloned the repository.
3. Entered the repository.
4. Checked the README.
5. Found the password for the next level.

### Commands Used

```bash
mktemp -d
cd /tmp/<directory>
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
cd repo
cat README
```

### What I Learned

I got my first proper experience with Git inside Bandit. I also learned that repositories can contain information that isn't obvious from the main filesystem.

### Flag

`y8Yd2ssKcpHpud7UvOSOxwamRMzIGIeQ`

## Bandit Level 28 → Level 29

### Level Goal

The password had been removed from the current README but was still present in the Git history.

### Solving Steps

1. Cloned the repository.
2. Checked the current README.
3. Looked through the Git commit history.
4. Inspected an earlier commit.
5. Found the old password.

### Commands Used

```bash
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
cd repo
cat README.md
git log
git show <commit>
```

### What I Learned

Deleting a secret from the latest version of a Git repository does not necessarily remove it from the repository's history. This is an important lesson for real-world security.

### Flag

`Em7eGtqaMySwNFjCpwzzHhLhospOcdt0`

## Bandit Level 29 → Level 30

### Level Goal

The password was stored in a different Git branch instead of the default branch.

### Solving Steps

1. Cloned the repository.
2. Checked the README on the default branch.
3. Listed all branches.
4. Found the `dev` branch.
5. Switched to it and checked the README again.
6. Found the password.

### Commands Used

```bash
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
cat README.md
git branch -a
git checkout dev
cat README.md
```

### What I Learned

I learned that important information can exist in branches that aren't part of the main/default branch. Checking Git branches is therefore useful when auditing a repository.

### Flag

`jq9Dfg2rXsfYsWMgFuKlXhphjdH7USgX`

## Bandit Level 30 → Level 31

### Level Goal

The password was hidden in a Git tag.

### Solving Steps

1. Cloned the repository.
2. Checked the normal files and didn't find anything useful.
3. Listed the Git tags.
4. Found the `secret` tag.
5. Used `git show` to inspect it.
6. Found the password.

### Commands Used

```bash
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
cd repo
cat README.md
git tag
git show secret
```

### What I Learned

Git doesn't only store information in files and branches. Tags and other Git objects can also contain useful information. This level made me think beyond the normal working tree.

### Flag

`82NkymblpGBYmIXG6ZQ8YldBYstHpfUf`