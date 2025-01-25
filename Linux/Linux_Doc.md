## Linux File System
![Reference Image](/Linux/screenshort/filesystem.jpg)

### 1. / (Root Directory)
The topmost directory in the Linux file system. All other files and directories are contained within this.

### 2. /bin
- Contains essential user binaries (programs) like bash, ls, cp, mv, cat, grep, su, touch  etc.
- These are necessary for the system to function in single-user mode.

```bash
root@habib-VirtualBox:/# cd bin/

root@habib-VirtualBox:/bin# ls 
```
![Reference Image](/Linux/screenshort/1.png)

### 3. /boot
- Contains the kernel, initial RAM disk, and bootloader files.


### 4. /dev
### 5. /etc

- Linux version 
```bash
root@habib-VirtualBox:/# cd etc/
```
```bash
root@habib-VirtualBox:/etc# cat os-release 

PRETTY_NAME="Ubuntu 24.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.1 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo
```

### 6. /home
### 7. /lib
### 8. /media
### 9. /mnt
### 10. /opt
### 11. /proc
### 12. /root
### 13. /run
### 14. /sbin
### 15. /srv
### 16. /sys
### 17. /tmp
### 18. /usr
### 19. /var


## Basic Commands: 
## ls :
- Lists files and directories in the current directory.

```bash
root@habib-VirtualBox:/# ls
```
- Displays details like permissions, owner, group, file size, and modification time.

```bash
root@habib-VirtualBox:/# ls -l
```
- Shows all files, including hidden ones (files beginning with .).

```bash
root@habib-VirtualBox:/# ls -a
```
- Lists all files, including hidden ones, with detailed information.
```bash
root@habib-VirtualBox:/# ls -la
```
- Shows file sizes in a human-readable format (e.g., KB, MB).
```bash
root@habib-VirtualBox:/# ls -lh
```
- Sorts files by modification time, with the most recent first.
```bash
root@habib-VirtualBox:/# ls -lt
```
- Displays the listing in reverse order (can combine with other options, e.g., ls -ltr).
```bash
root@habib-VirtualBox:/# ls -lr
```
- Lists contents of directories and their subdirectories recursively.
```bash
root@habib-VirtualBox:/# ls -R
```
- Appends indicators to files:
   - / for directories
   - "*" for executable files
   - @ for symbolic links

```bash
root@habib-VirtualBox:/# ls -F
```
- Displays only directories in the current location.
```bash
root@habib-VirtualBox:/# ls -d */
```
- Sorts files by size, with the largest first.
```bash
root@habib-VirtualBox:/# ls -lS
```
- Displays the inode number of each file
```bash
root@habib-VirtualBox:/# ls -lS
```
## cd
## mv
## rm
## mkdir:
## cat:
# touch:
## grep : 