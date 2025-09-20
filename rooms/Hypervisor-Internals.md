---
completed_at: 2025-09-14
url: https://tryhackme.com/r/room/hypervisorinternals
tags:
  - basic-rooms
  - hypervisors
  - internals
---
## 📝 Notes
|   |   |
|---|---|
|**Type**|**Description**|
|Bridged|This type allows for a VM to appear as if it is another device on the host network. For example, the guest VM will obtain an IP address on the same network as the host.|
|NAT|With this type, all guest network activity appears as if it originates from the host.|
|Host-only|Host-only will only allow the guest to be accessible from the host itself.|
|Specific|The "specific" type allows you to manually assign what vNIC is used by the guest. Hypervisors allow you to create vNICs, where you can specify what subnet and address range is used.<br><br>For example, you can create a vNIC that assigns IP addresses on 10.10.10.0/24, and then configure each guest to use that vNIC so that they will all be placed on 10.10.10.0/24 and can communicate with each other.


|   |   |
|---|---|
|**Feature**|**Description**|
|Enhanced performance|Guest additions allow the guest to use optimised drivers, (such as network adapters and disk drives (SATA, SCSI, NVME, etc.)).|
|Shared folders|Shared folders allow easy file exchange between the host and guest. This allows both environments to access specific folders that will be mounted within the guest.|
|Shared clipboard|Much like shared folders, a shared clipboard allows the guest and host to access one another's clipboard, allowing files, text, and images to be shared.|
|Improved graphics|Graphical drivers are installed to allow enhancements such as dynamic resolution. Hypervisors such as VMware allow for 3D acceleration, making better use of the host's graphics card to improve graphics performance.|
|USB devices|Guest additions also allow the guest to access the host's USB devices. For example, you can mount a host's webcam to the guest. Please note, in most cases, you are unable to access the device on the host whilst the guest has it attached.|
## 🛠️ Tools Used



## 📚 & Further Reading


https://www.microsoft.com/en-us/msrc/bounty-hyper-v?rtc=1
https://www.broadcom.com/support/vmware-security-advisories
https://tryhackme.com/r/room/virtualizationandcontainers