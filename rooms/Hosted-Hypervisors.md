---
completed_at: 2025-09-21
url: https://tryhackme.com/room/hostedhypervisors
tags:
  - intro-rooms
  - windows
  - hypervisors
---
## 📝 Notes

Leftover network adapters

One of the tools is `VBoxManage`. We can find it in the default location `C:\Program Files\Oracle\VirtualBox`, and from there, we can find an executable called `VBoxManage.exe`. 

There are several uses for this tool; for example, we could start a VM from the command line with a command similar to the one below.  

`Vboxmanage.exe startvm {name of the vm}`  

We could also enable debug logs if we want more verbosity with the following command.  

`VBoxManage.exe debugvm {name of the vm} log --all`  

### VirtualBox Logs

|                        |                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **VirtualBox.xml**     | While this is not strictly a log file but rather a configuration file used by VirtualBox, we can get good information from it, like the interface IP used by the Hypervisor, the virtual interfaces used by a VM, uid, log locations, VM files location, etc. We need to be careful not to edit this file since the Hypervisors use it, and it could lead to failure if settings are not properly set. |
| **selectorwindow.log** | contains information about the VirtualBox process (usually the details used to install/start).                                                                                                                                                                                                                                                                                                         |
| **VboxSVC**            | saves information regarding the start/stop use of VirtualBox and also saves/deletes components.                                                                                                                                                                                                                                                                                                        |
| **Vbox.log**           | This file contains information such as the OS, with details about their architecture and installation dates (timestamps). It also contains information about the VM plugins and drivers that were implemented (audio, USB, etc.).                                                                                                                                                                      |
| **VBoxHardening.log**  | This file will provide us with information about the hardening performed on VirtualBox; this is focused on the memory management of the Hypervisor. While this information can be hard to read and is not well documented,  if we were looking for some memory manipulation (like an escapeVM attack), we could detect it here. Also, some security-related crashes will be visible in this file.      |

### VirtualBox Memory Dump
Finally, we'll maybe want to create a memory dump of a VM in VirtualBox; for that, we can use VBoxManage to create the image. We can do it by using cmd.exe and navigate to `C:\Program Files\Oracle\VirtualBox`, and execute the `VBoxManage` tool using the following syntax.

**Note**: Volatility2 is not installed on the VM. The below is just an example.

`VBoxManage.exe debugvm {name of the vm} dumpvmcore --filename={output file name}`  

After that, we need to use Volatility2; since this feature is not supported on Volatility3, the command to convert the core dump into a memory dump is the following:

`python vol.py -f {output file name} imagecopy -O {new output file name}`  

This will create a memory dump of the machine for us to investigate the internal memory of it.  

**Note**: It's also worth mentioning that you can inspect snapshots on the default directory. `C:\Users\user01\VirtualBox VMs\secretvm\Snapshots`. Also, the Virtual disk used by the VM can be found in the VM directory, and while it is not strictly a Hypervisor investigation, it can be helpful.

|   |   |
|---|---|
|**settings.ini**|This file contains configuration settings, such as printers and disks, which are applied globally across different VMs.|
|**config.ini**|Contains specific configurations like Auto-Update, access ports, and others.|
|**vmautostart.xml**|Contains configuration information on how Virtual Machines are supposed to start.
### VMware VM Memory Dump  

Finally, If we want to create a memory dump of a VM on a VMware workstation, we need to use or take a screenshot of the VM we want to dump the memory on, and then we need to use a tool to convert it to a memory dump. A commonly used tool for this is "vmss2core." The following command will allow us to dump the memory of a VM.  

`vmss2core -W {snampshot.vmss} {new name of dump.vmem}`
## 🛠️ Tools Used

`ipconfig`, `ifconfig`, `ip addr`, `get-netadapter`

`python vol.py -f ..\exercise.mem windows.netstat`
`python vol.py -f ..\exercise.mem windows.pslist`

## 📚 & Further Reading

- https://www.virtualbox.org/wiki/Build_instructions
- We can find more information about VboxManage [here](https://www.virtualbox.org/manual/ch08.html).

Needed writeup help on task 6 question 2.
Volatility 3 documentation about plugins: https://volatility3.readthedocs.io/en/stable/volatility3.plugins.html