## Prerequisites:
Download the pdf file named "confidential.pdf" from the challenge.
Then we proceed to perform an exiftool scan to find for hidden information and we get below results:
```bash
┌──(tanush㉿kali)-[~/Downloads]
└─$ exiftool confidential.pdf
ExifTool Version Number         : 13.50
File Name                       : confidential.pdf
Directory                       : .
File Size                       : 183 kB
File Modification Date/Time     : 2026:07:10 08:58:22+00:00
File Access Date/Time           : 2026:07:10 09:01:13+00:00
File Inode Change Date/Time     : 2026:07:10 08:58:22+00:00
File Permissions                : -rw-rw-r--
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.7
Linearized                      : No
Page Count                      : 1
Producer                        : PyPDF2
Author                          : cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV84N2JlNjBjMH0=
```

we get an Base64 output from author name
by:
```bash
┌──(tanush㉿kali)-[~/Downloads]
└─$ echo "cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV84N2JlNjBjMH0=" | base64 -d
picoCTF{puzzl3d_m3tadata_f0und!_87be60c0}   
```
## Flag found:
```text
picoCTF{puzzl3d_m3tadata_f0und!_87be60c0} 
```
