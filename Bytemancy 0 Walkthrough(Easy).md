## Prerequisites:
Enter the below command in the terminal to connect to the instance.
```bash
nc candy-mountain.picoctf.net 57342
```

After connecting to the instance we get below output:
```bash
┌──(tanush㉿kali)-[~/Downloads]
└─$ nc candy-mountain.picoctf.net 57342
⊹──────[ BYTEMANCY-0 ]──────⊹
☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐

Send me ASCII DECIMAL 101, 101, 101, side-by-side, no space.

☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐
⊹─────────────⟡─────────────⊹
==> 

```
here we know that the number 101 decimal number refers to 'e' and based on the above hint we need to enter ***'eee'*** as input (without any spaces).
## Final Flag:
```text
picoCTF{pr1n74813_ch4r5_62006ed0}
```
