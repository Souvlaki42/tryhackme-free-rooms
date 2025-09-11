- Google dorks
- Duckduckgo bangs
- Shodan - a search engine for devices connected to the Internet
- Censys - a search engine for internet-connected hosts, websites, certificates, and other Internet assets
- VirusTotal - website that provides a virus-scanning service for files using multiple antivirus engines
- Have I been pwned - it tells you if an email address has appeared in a leaked data breach
- NVD CVE - dictionary of vulnerabilities
- Exploit DB - list of exploit codes from various authors
- GitHub, Linkedin, Facebook etc
- SOC
- TCP, IP, MAC, UDP, HTTP, FTP, SMTP etc
- Day 21 of  [Advent of Cyber 2](https://tryhackme.com/room/adventofcyber2) (NTFS ADS practice)
- NTFS, Permissions, ADS, FAT16, FAT36
- Windows, System32, %windir%
- **Administrator** & **Standard User**
- https://www.howtogeek.com/405806/windows-task-manager-the-complete-guide/
- https://tryhackme.com/jr/btwindowsinternals
- https://docs.microsoft.com/en-us/troubleshoot/windows-client/performance/system-configuration-utility-troubleshoot-configuration-errors
- Windows Troubleshooting - control.exe
- https://learn.microsoft.com/en-us/windows/win32/eventlog/event-types
- https://docs.microsoft.com/en-us/windows/win32/eventlog/eventlog-key
- https://tryhackme.com/room/windowseventlogs
- https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources#:~:text=Hardware%20resources%20are%20the%20assignable,of%20bus%2Drelative%20memory%20addresses
- https://ss64.com/nt/
- https://docs.microsoft.com/en-us/troubleshoot/windows-server/performance/windows-registry-advanced-users
- https://msrc.microsoft.com/update-guide
- https://support.microsoft.com/en-us/windows/windows-update-faq-8a903416-6f45-0718-f5c7-375e92dddeb2
- https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/best-practices-configuring
- https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview
- https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview
- Volume Shadow Copy Service, Bitlocker
- **Bonus**: If you wish to interact hands-on with VSS, I suggest exploring Day 23 of [Advent of Cyber 2](https://tryhackme.com/room/adventofcyber2).
- Further reading material:

- [Antimalware Scan Interface](https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal)[](https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal)
- [Credential Guard](https://docs.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard-manage)[](https://docs.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard-manage)
- [Windows 10 Hello](https://support.microsoft.com/en-us/windows/learn-about-windows-hello-and-set-it-up-dae28983-8242-bb2a-d3d1-87c9d265a5f0#:~:text=Windows%2010,in%20with%20just%20your%20PIN.)
- [CSO Online - The best new Windows 10 security features](https://www.csoonline.com/article/3253899/the-best-new-windows-10-security-features.html)

**Note**: Attackers use built-in Windows tools and utilities in an attempt to go undetected within the victim environment.  This tactic is known as Living Off The Land. Refer to the following resource [here](https://lolbas-project.github.io/) to learn more about this.

## Active Directory
Domain controllers
Domain users (People services)
Domain machines
Security Groups

| Security Group     | Description                                                                                                                                               |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Domain Admins      | Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs. |
| Server Operators   | Users in this group can administer Domain Controllers. They cannot change any administrative group memberships.                                           |
| Backup Operators   | Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers.                    |
| Account Operators  | Users in this group can create or modify other accounts in the domain.                                                                                    |
| Domain Users       | Includes all existing user accounts in the domain.                                                                                                        |
| Domain Computers   | Includes all existing computers in the domain.                                                                                                            |
| Domain Controllers | Includes all existing DCs on the domain.                                                                                                                  |

https://docs.microsoft.com/en-us/windows/security/identity-protection/access-control/active-directory-security-groups

Organizational units

Windows PowerShell (As Phillip)

```powershell
PS C:\Users\phillip> Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

New Password: *********

VERBOSE: Performing the operation "Set-ADAccountPassword" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```

Since we wouldn't want Sophie to keep on using a password we know, we can also force a password reset at the next logon with the following command:

Windows PowerShell (as Phillip)

```powershell
PS C:\Users\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose

VERBOSE: Performing the operation "Set" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```

**Security Filtering**

Kerberos Authentication
NetNTLM Authentication

Trees & Forests

https://tryhackme.com/room/activedirectoryhardening
https://tryhackme.com/module/hacking-active-directory