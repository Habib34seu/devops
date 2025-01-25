## Linux File System
![Reference Image](/Linux/screenshort/filesystem.jpg)

### 1. / (Root Directory)
The topmost directory in the Linux file system. All other files and directories are contained within this.

### 2. /bin
- Contains essential user binaries (programs) like ls, cp, mv, cat, grep, su, touch  etc.
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
