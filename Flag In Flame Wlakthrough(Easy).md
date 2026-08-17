## Prerequisites:
Download the logs.txt file from the challenge.
then try to find the flags from the logs first we try to convert the logs.txt contents as it is BASE-64.
Use below command to decode it:
```bash                                                                         
┌──(tanush㉿kali)-[~/Downloads]
└─$ base64 -d logs.txt > decoded.png   
```
we get a png file then we extract the data present in the photo:
![[decoded.png]]
we have a string of letters which are hexadecimal we convert them into ascii string
```text
7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F62653836303237397D
```
we use below code to convert the HEX string into ASCII:
```bash
┌──(tanush㉿kali)-[~/Downloads]
└─$ echo "7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F62653836303237397D" | xxd -r -p
picoCTF{forensics_analysis_is_amazing_be860279}
```
## Flag Obtained:
```text
picoCTF{forensics_analysis_is_amazing_be860279} 
```
