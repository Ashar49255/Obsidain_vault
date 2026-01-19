# Linux Complete Concise Cheat Sheet

---

## 1. Basic Navigation Commands

- `pwd` – show current directory
    
- `ls` – list files and directories
    
- `ls -l` – long listing with permissions
    
- `ls -a` – show hidden files
    
- `cd <dir>` – change directory
    
- `cd ..` – move one level up
    
- `cd ~` – go to home directory
    

---

## 2. File & Directory Management

- `touch file` – create empty file
    
- `mkdir dir` – create directory
    
- `mkdir -p a/b/c` – create nested directories
    
- `rm file` – delete file
    
- `rm -r dir` – delete directory recursively
    
- `rm -rf dir` – force delete
    
- `cp file1 file2` – copy file
    
- `cp -r dir1 dir2` – copy directory
    
- `mv old new` – move/rename file or directory
    
- `stat file` – detailed file info
    

---

## 3. Viewing File Content

- `cat file` – view file content
    
- `less file` – scrollable view
    
- `more file` – basic paged view
    
- `head file` – first 10 lines
    
- `tail file` – last 10 lines
    
- `tail -f file` – live log monitoring
    

---

## 4. File Permissions & Ownership

### Permission Format

`-rwxr-xr--`

- Owner | Group | Others
    
- r = read, w = write, x = execute
    

### Commands

- `chmod 755 file` – change permissions
    
- `chmod u+x file` – add execute to owner
    
- `chmod o-r file` – remove read from others
    
- `chown user file` – change owner
    
- `chown user:group file` – change owner & group
    
- `ls -l` – check permissions
    

---

## 5. Users & Groups Management

- `useradd username` – add user
    
- `adduser username` – interactive user add
    
- `userdel username` – delete user
    
- `groupadd groupname` – add group
    
- `groupdel groupname` – delete group
    
- `usermod -aG group user` – add user to group
    
- `id user` – user & group info
    
- `whoami` – current user
    
- `who` – logged-in users
    
- `cat /etc/passwd` – user list
    
- `cat /etc/group` – group list
    

---

## 6. Process & System Monitoring

- `top` – real-time processes
    
- `htop` – advanced process viewer
    
- `ps aux` – all running processes
    
- `kill PID` – stop process
    
- `kill -9 PID` – force kill
    
- `uptime` – system running time
    
- `free -h` – memory usage
    
- `df -h` – disk usage
    
- `du -sh dir` – directory size
    

---

## 7. Networking Commands

- `ip a` – IP address info
    
- `ping google.com` – connectivity test
    
- `traceroute google.com` – network path
    
- `netstat -tulnp` – open ports
    
- `ss -tulnp` – socket statistics
    
- `scp file user@ip:/path` – secure copy
    
- `rsync -av src dest` – sync files
    

---

## 8. Archive & Compression

- `tar -cvf file.tar dir` – create tar
    
- `tar -xvf file.tar` – extract tar
    
- `tar -czvf file.tar.gz dir` – tar + gzip
    
- `zip file.zip file` – zip file
    
- `unzip file.zip` – unzip
    

---

## 9. Editors

- `nano file` – simple editor
    
- `vi file` – advanced editor
    

### Nano Shortcuts

- Ctrl+O save
    
- Ctrl+X exit
    

---

## 10. Redirection & Pipes

- `>` overwrite output
    
- `>>` append output
    
- `<` input redirection
    
- `|` pipe output to next command
    

Examples:

- `ls > file.txt`
    
- `cat file | grep word`
    

---

## 11. Search & Find

- `grep -r word dir` – recursive search
    

---

## 12. Links

- `ln file hardlink` – hard link
    
- `ln -s file softlink` – symbolic link
    
- `ls -li` – check inode
    

---

## 13. Mounting & fstab

- `mount` – mounted filesystems
    
- `lsblk` – block devices
    
- `/etc/fstab` – permanent mounts
    

---

## 14. Package Management (Ubuntu)

- `apt update` – update repo
    
- `apt install pkg` – install package
    
- `apt remove pkg` – remove package
    
- `apt autoremove` – clean unused
    

---

## 15. Shutdown & Reboot

- `shutdown now`
    
- `shutdown -r now`
    
- `reboot`
    
- `poweroff`
    

---

## 16. Useful Shortcuts

- Ctrl+C – stop command
    
- Ctrl+Z – pause process
    
- fg – resume process
    
- clear – clear screen
    
- history – command history
    

---

## Quick Revision List

- Permissions: rwx | owner group other
    
- Stop ping: Ctrl+C
    
- Root access: sudo
    
- Logs: /var/log
    
- Config files: /etc
    
- Home dirs: /home
    

---

End of Linux Cheat Sheet