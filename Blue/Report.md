# [Blue - 10.10.10.40](https://www.hackthebox.eu/home/machines/profile/51)

1. Run a simple nmap scan to reveal ports:
![Simple nmap scan result](https://raw.githubusercontent.com/SirCouchus/HackTheBox-Write-ups/master/Blue/Images/simple-nmap.png)
  - Microsoft Remote Procedure Call - 135 (TCP)
  - NetBIOS - 139 (TCP)
  - Microsoft DS - 445 (TCP)

2. I run a more detailed nmap scan to discover service versions:
![Detailed nmap scan](https://raw.githubusercontent.com/SirCouchus/HackTheBox-Write-ups/master/Blue/Images/detailed-nmap.png)
  - PC name is Haris-PC - Haris could be a potential username at some point
  - Windows 7 is the OS version - outdated and vulnerable
  - Server Message Block - signing is enabled but not required

3. I use Metasploit to conduct a search on whether port 445 (Microsoft DS) is vulnerable to MS17-010 exploit. This exploit was detailed by Microsoft and the official bulletin can be found here: https://docs.microsoft.com/en-us/security-updates/securitybulletins/2017/ms17-010
[!Metasploit vulnerability scan](https://raw.githubusercontent.com/SirCouchus/HackTheBox-Write-ups/master/Blue/Images/metasploit-vulnerable.png)
The Machine is in fact **VULNERABLE** to this exploit

4. I use Metasploit to run the *Eternal Blue* exploit against our desired machine:
![Metasploit exploit execution](https://raw.githubusercontent.com/SirCouchus/HackTheBox-Write-ups/master/Blue/Images/metasploit-exploit.png)

5. I have successfully gained access to the machine. As noted earlier, the user's name is Haris, and so we can cd into the /Users/ directory and enter Haris's Desktop where the users.txt file is stored. We can also travel to /Users/Administrator and steal the root.txt from the Admin Desktop, finally giving us the root hash:
![Root credentials](https://raw.githubusercontent.com/SirCouchus/HackTheBox-Write-ups/master/Blue/Images/got-root.png)

6. To summarise, we have a user hash:
**4c546aea7dbee75cbd71de245c8deea9**
and an Admin hash:
**ff548eb71e920ff6c08843ce9df4e717**
