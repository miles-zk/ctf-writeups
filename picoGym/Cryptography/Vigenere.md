## Vigenere - Medium - (02/25/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/316?category=2&difficulty=2&page=1)

This challenge gave us a .txt file containing the following encrypted message:
```
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_f85729e7}
```
The clue gives us the key "CYLAB", which should produce the flag for us when we put it into an [online Vignere decryption tool](https://www.dcode.fr/vigenere-cipher).

![Vignere Cipher Tool](https://i.imgur.com/Uumbu6b.png)

This produces the flag: **picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_d85729g7}**
