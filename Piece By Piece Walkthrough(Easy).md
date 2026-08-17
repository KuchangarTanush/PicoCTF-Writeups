
## Prerequisites:
Connect to the instance through the SSH credentials provided in the instance.
After we login using the SSH credentials we see below information:
```bash                                                                     
┌──(tanush㉿kali)-[~]
└─$ ssh ctf-player@dolphin-cove.picoctf.net -p 52539
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@dolphin-cove.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 7.0.0-1009-aws x86_64)

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

ctf-player@pico-chall$ ls
instructions.txt  part_aa  part_ab  part_ac  part_ad  part_ae
ctf-player@pico-chall$ ls -al
total 28
drwxr-xr-x 1 ctf-player ctf-player  20 Aug 17 09:34 .
drwxr-xr-x 1 root       root        24 Feb  4  2026 ..
drwx------ 2 ctf-player ctf-player  34 Aug 17 09:34 .cache
-rw-r--r-- 1 root       root        67 Feb  4  2026 .profile
-rw-r--r-- 1 ctf-player ctf-player 282 Feb  4  2026 instructions.txt
-rw-r--r-- 1 ctf-player ctf-player  51 Feb  4  2026 part_aa
-rw-r--r-- 1 ctf-player ctf-player  51 Feb  4  2026 part_ab
-rw-r--r-- 1 ctf-player ctf-player  51 Feb  4  2026 part_ac
-rw-r--r-- 1 ctf-player ctf-player  51 Feb  4  2026 part_ad
-rw-r--r-- 1 ctf-player ctf-player  35 Feb  4  2026 part_ae
ctf-player@pico-chall$ 

```
here we are able to see 5 files let us explore them, First lets see instructions.txt file:
```bash
ctf-player@pico-chall$ cat instructions.txt 
Hint:

- The flag is split into multiple parts as a zipped file.
- Use Linux commands to combine the parts into one file.
- The zip file is password protected. Use this "supersecret" password to extract the zip file.
- After unzipping, check the extracted text file for the flag.
```
her we obtain an hint that the file is split into different parts and is protected by a password, we need to combine the files and then use the password to obtain the flag.
Use below command to combine files present:
```bash
ctf-player@pico-chall$  cat part_* > combined_file
```
this helps combine the file names that start with part into a file named combined file, then use an extraction method to extract the flag, here i am using unzip to extract the flag from the combined file and then we can use cat to display the flag:
```bash
ctf-player@pico-chall$ unzip combined_file 
Archive:  combined_file
[combined_file] flag.txt password: 
 extracting: flag.txt
```
## Final Flag:
```text
picoCTF{z1p_and_spl1t_f1l3s_4r3_fun_28d309dc}
```