## Prerequisites
- First Start the instance and open the instance in the command shell
```bash
- `nc foggy-cliff.picoctf.net 63295`
```

After the shell opens enter "base64"
we get output as:
```bash
zsh: corrupt history file /home/tanush/.zsh_history
┌──(tanush㉿kali)-[~]
└─$  nc foggy-cliff.picoctf.net 63295
===Welcome to the Text Transformations Challenge!===

Your goal: step by step, recover the original flag.
At each step, you'll see the transformed flag and a hint.
Enter the correct Linux command to reverse the last transformation.

--- Step 1 ---
Current flag: KW5xOW45OG43LWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj
Hint: Base64 encoded the string.
Enter the Linux command to reverse it: echo "KW5xOW45OG43LWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj" | base64 -d
Incorrect. Try again.
Output: [Error] Command not allowed.
Hint: Try reversing: base64

```
we also receive a hint for next step
Then type "base64 -d" this can help in reversing we get output as :
```bash
Enter the Linux command to reverse it: base64 -d
Correct!

--- Step 2 ---
Current flag: )nq9n98n7-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc
Hint: Reversed the text.
Enter the Linux command to reverse it: rev
Correct!
```

then we use "rev" to reverse the obtained flag

```bash
--- Step 3 ---
Current flag: cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-7n89n9qn)
Hint: Replaced underscores with dashes.
Enter the Linux command to reverse it: re '-' '_'
Incorrect. Try again.
Output: [Error] Command not allowed.
Hint: Try reversing: tr '_' '-'
```
```
then use "tr '-' '_'" to replace dashes with underscore 
```

then using the below code replace brackets with curly brackets.

```bash
--- Step 4 ---
Current flag: cvpbPGS(Eriref1at_g3kg_Ge4afs0ez@g10af_7n89n9qn)
Hint: Replaced curly braces with parentheses.
Enter the Linux command to reverse it: tr '()' '{}'
Correct!

--- Step 5 ---
Current flag: cvpbPGS{Eriref1at_g3kg_Ge4afs0ez@g10af_7n89n9qn}
Hint: Applied ROT13 to letters.
```
then to convert or apply rot use below command:
```bash

Enter the Linux command to reverse it: tr 'a-zA-Z' 'n-za-mN-ZA-M'
Correct!

Congratulations! You've recovered the original flag:
>>> picoCTF{Revers1ng_t3xt_Tr4nsf0rm@t10ns_7a89a9da}
```

### Final Flag:
```
picoCTF{Revers1ng_t3xt_Tr4nsf0rm@t10ns_7a89a9da}
```
