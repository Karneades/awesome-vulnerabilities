# Awesome Vulnerabilities

Collection of awesome and fascinating vulnerabilities. From sneaky persistence, to time of check to time of use vulnerabilities, to vulnerabilities where a awesome combination of multiple factors leades to privilege escaltion.

snagit ,
av symbolic link timeing ( toctou)
race conditions
ios xml parsing


## Time of Check to Time of Use (TOCTOU)

* [psychicpaper](https://siguza.github.io/psychicpaper/) - `I dubbed it “psychic paper” because, just like the item by that name that Doctor Who likes to carry, it allows you get past security checks and make others believe you have a wide range of credentials that you shouldn’t have.`. Exploiting the difference of the XML parsers in iOS and macOS allowed having more permissions than allowed by using comment tags inside the permission manifest (called _Entitlement_ in Apple terms). `So simple, in fact, that the PoC I tweeted out looks like an absolute joke. But it’s 100% real.`

## Privilege Escalation / Privileged Writes

* [CVE-2015-0057: One-Bit To Rule Them All: Bypassing Windows’ 10 Protections using a Single Bit](https://breakingmalware.com/vulnerabilities/one-bit-rule-bypassing-windows-10-protections-using-single-bit/) - The local privilege escalation vulnerability (CVE-2015-0057) could give attackers total control of the victims' machines. The flaw existed in the graphical user interface (GUI) component of the Win32k.sys module within the Windows Kernel which, among other things, manages vertical and horizontal Windows' scroll bars. The flaw actually resides in the xxxEnableWndSBArrows function which could alter the state of both scroll bars through a call.
* [CVE-2019-13382: Local Privilege Escalation in SnagIt](https://enigma0x3.net/2019/07/24/cve-2019-13382-privilege-escalation-in-snagit/) - Awesome combination of high-privilege service and user-writable directories. When the [TechSmith Uploader Service] checks for [invalid] presentations, it will move the file out of the QueuedPresentations folder and into the InvalidPresentations folder. When it does so, the service will hit the symbolic link 
and write the new file into a protected location with permissions that allow the low privileged user 
full control over the contents, resulting in Elevation of Privilege to NT AUTHORITY\SYSTEM.
* [PrintDemon: Print Spooler Privilege Escalation, Persistence & Stealth (CVE-2020-1048 & more)](https://windows-internals.com/printdemon-cve-2020-1048/) - Using one PowerShell command leads to persistence and priviledge escalation. In the words of the author of the blog post: `This bug is so simple that it’s almost embarrassing once you realize all it would’ve taken is a PowerShell command.`.
* [Exploiting (Almost) Every Antivirus Software](https://www.rack911labs.com/research/exploiting-almost-every-antivirus-software/) - RACK911 Labs has come up with a unique but simple method of using directory junctions (Windows) and symlinks (macOS & Linux) to turn almost every antivirus software into self-destructive tools. When an unknown file is saved to the hard drive, the antivirus software will usually perform a “real time scan” either instantly or within a couple of minutes. If the unknown file is determined to be a suspected threat, the file will then be automatically quarantined and moved to a secure location pending further user instructions or it will simply be deleted. What most antivirus software fail to take into consideration is the small window of time between the initial file scan that detects the malicious file and the cleanup operation that takes place immediately after. A malicious local user or malware author is often able to perform a race condition via a directory junction (Windows) or a symlink (Linux & macOS) that leverages the privileged file operations to disable the antivirus software or interfere with the operating system to render it useless, etc.
* [Faxing Your Way to SYSTEM](https://windows-internals.com/faxing-your-way-to-system/) - DLL side loading leads to priviledge escalation when using fax service (and the DLL for the spooler).
