## Prerequisites:
use below command to connect to the instance:
```bash
 nc -vz mysterious-sea.picoctf.net 57798
```
this return below result:
```bash
┌──(tanush㉿kali)-[~]
└─$  nc -vz mysterious-sea.picoctf.net 57798
DNS fwd/rev mismatch: mysterious-sea.picoctf.net != ec2-3-130-79-223.us-east-2.compute.amazonaws.com
mysterious-sea.picoctf.net [3.130.79.223] 57798 (?) open
```
then based on the hint given use Smbclient (for windows) or Smbutil (For mac).
Use below command for listing shares

```bash
smbclient -L //3.130.79.223/shares -p 57798 --no-pass
```
we get below shares:

```bash
┌──(tanush㉿kali)-[~]
└─$ smbclient -L //3.130.79.223 -p 57798 --no-pass

        Sharename       Type      Comment
        ---------       ----      -------
        shares          Disk      Public Share With Guests
        IPC$            IPC       IPC Service (Samba 4.19.5-Ubuntu)
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 3.130.79.223 failed (Error NT_STATUS_IO_TIMEOUT)
Unable to connect with SMB1 -- no workgroup available
```
then we search in public shares using below command

```bash
smbclient //3.130.79.223/shares -p 57798 --no-pass
```

we get below result and then we use ***get*** command to download the flag:

```bash
┌──(tanush㉿kali)-[~]
└─$ smbclient //3.130.79.223/shares -p 57798 --no-pass
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Sat Mar  7 01:55:43 2026
  ..                                  D        0  Sat Mar  7 01:55:43 2026
  dummy.txt                           N     1142  Thu Feb  5 02:52:17 2026
  flag.txt                            N       37  Sat Mar  7 01:55:43 2026
65536 blocks of size 1024. 58640 blocks available
smb: \> cat flag.txt
cat: command not found
smb: \> get flag.txt
getting file \flag.txt of size 37 as flag.txt (0.0 KiloBytes/sec) (average 0.0 KiloBytes/sec)
smb: \> ^Z
zsh: suspended  smbclient //3.130.79.223/shares -p 57798 --no-pass
```
## Final Flag
```text
picoCTF{5mb_pr1nter_5h4re5_8a0df8e0}
```
