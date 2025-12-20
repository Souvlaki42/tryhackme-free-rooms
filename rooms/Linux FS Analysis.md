---
completed_at: 2025-09-28
url: https://tryhackme.com/room/linuxfilesystemanalysis
tags:
  - intro-rooms
  - security
  - linux
  - file-system
cssclasses:
  - first-fit
---
## 📝 Notes



## 🛠️ Tools Used

`md5sum`, `stat`, `who`, `exiftool`, `strings`

`getent group <name or id>`: get details about a group like its name and members list

`last`, `lastlog`, `lastb`: commands that list login attempts

`sudo debsums -e -s`: Lists altered Debian package binaries compared by MD5

`sudo chkrootkit`, `sudo rkhunter -c -sk`: Check a machine for rootkits
### Find command
**Arguments:** path
**Flags:**
- *-user:* The user that owns the files/directory you look for
- *-group:* The group that includes the users you are looking for
- *-type:* Type of inode you look for: f, d, etc...
- *-cmin:* Created/Updated within the last 5 minutes, with flag *-5*
- *-perm*: Permission combinations like *-o+w*
- *-u=s*: Executables with the SUID bit set
## 📚 & Further Reading