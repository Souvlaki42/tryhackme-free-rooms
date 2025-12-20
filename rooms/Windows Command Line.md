---
completed_at: 2025-09-12
url: https://tryhackme.com/r/room/windowscommandline
tags:
  - intro-rooms
  - cmd
  - command-line
  - windows
cssclasses:
  - first-fit
---
## 📝 Notes
- `set`: Get a list of all defined variables.
- `ver`: Get system version.
- `systeminfo`: Get system info.
- `<command 1> | <command 2>`: send output of command 1 to input of command 2.
- `help <command?>`: get info about a command or a list of all command.
- `cls`: Clear the screen.
- `ipconfig (/all)`: get IP information and get optionally more of it.
- `ping <address>`: send ICMP request and look for alive response.
- `tracert <address>`: try and list the router list to reach address.
- `nslookup <address> <dns_address?>`: gives the IP address of a hostname (address) based on an optional DNS server or default.
- `netstat`: get list of current connections.
- `cd <path>`: go to any other path including ../.. etc.
- `dir (/a) (/s)`: list contents of current directory + /a for hidden stuff + /s for going down the whole tree of subdirectories.
- `tree`: visually represent subdirectories.
- `mkdir <path>`: make a new directory in that path.
- `rmdir <path>`: remove the directory in that path, if it's not empty.
- `type <path>` and `more <path>`: viewers for file contents (more is better for longer files).
- `copy <location 1> <location 2>`: copy file from location 1 to location 2.
- `move <location 1> <location 2>`: move file from location 1 to location 2.
- `del <path>` or `erase <path>`: delete files and directories.
- `echo <message?>`: Print a message to the screen or default.
- `<command> > <path>`: Write output of command to the file in path.
- `tasklist /FI "imagename eq <process name>"`: Get PIDs of the process names.
- `taskkill /PID <PID>`: Kill the process assigned the PID referenced.
- `chkdsk`: checks the file system and disk volumes for errors and bad sectors.
- `driverquery`: displays a list of installed device drivers.
- `sfc /scannow`: scans system files for corruption and repairs them if possible.
- `shutdown (/...args)`: Shutdown, restart etc depending on the flags passed.

## 🛠️ Tools Used



## 📚 & Further Reading


