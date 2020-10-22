# Retired-Boxes
## Available Reports
* Active (**SMB**, **LDAP**, **KERBEROS**, **HASHCAT**, **GPP**)
* Shocker (**SHELLSHOCK**, **Perl** and **Bash** Reverse Shell, **LinEnum**, **TTY** Shells)
* Bashed (**PHPBASH**, **Python Reverse Shells**)

## Cheat Sheet
### General
[Reverse Shells](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
### Windows
**Port 139**: SMB originally ran on top of **NetBIOS** using port 139. NetBIOS is an older transport layer that allows Windows computers to talk to each other on the same network.


**Port 445**: Later versions of **SMB** (after Windows 2000) began to use port 445 on top of a TCP stack. Using TCP allows SMB to work over the internet.

**Port 135**: Remote Procedure Call (**RPC**) dynamic port allocation is used by server applications and remote administration applications such as Dynamic Host Configuration Protocol (DHCP) Manager, Windows Internet Name Service (WINS) Manager, and so on. 
