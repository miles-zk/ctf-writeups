# Crypto Blitz #1 (02/25/2025)
Completed challenges:\
[morse-code](https://play.picoctf.org/practice/challenge/280?category=2&difficulty=2&page=2)\
[transposition-trial](https://play.picoctf.org/practice/challenge/312?category=2&difficulty=2&page=1)\
[Vigenere](https://play.picoctf.org/practice/challenge/316?category=2&difficulty=2&page=1)\
[ReadMyCert](https://play.picoctf.org/practice/challenge/367?category=2&difficulty=2&page=1)


## morse-code
In this challenge, we're given a .wav file that, as the name of the challenge entails, plays morse code when opened.
Upon opening the file in Audacity, we can start to break down the message being sent.

![Audacity Screenshot](https://i.imgur.com/twQGdKy.png)

Identifying each large bar as a -, each small bar as a ., and the larger spaces as a space, we can derive the morse code into text form to be:
```
.__ .... ...._ __... .... ...._ __... .... ____. _____ _.. .__ ..___ _____ .._ ____. .... __...
```
Which when put into an online [morse code translator](https://morsecode.world/international/translator.html) produces the text "WH47H47H90DW20U9H7" which is leet speak for "WHAT HATH GOD WROUGHT", with some formatting it produces the flag: **picoCTF{wh47_h47h_90d_w20u9h7)**

## transposition-trial
This challenge gives us a .txt file which containing a jumbled string of text which appears to include the flag:
```
heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V091B0AE}2
```
The clue for the challenge states that every block of 3 characters got scrambled around and that the first word is 3 letters long. With the first letters being "heT", I figured that this word would be unscrambled to "The", meaning that the transposition cipher key is (3, 1, 2).
To find the flag, this process must be replicated on every block of 3 characters in the text.
```
"heT" = The
"fl " = fl
"g a" = ag
"s i" = is
"icp" = pic
"CTo" = oCT
"{7F" = F{7
"4NR" = R4N
"P05" = 5P0
"1N5" = 51N
"_16" = 6_1
"_35" = 5_3
"P3X" = XP3
"51N" = N51
"3_V" = V3_
"091" = 109
"B0A" = AB0
"E}2" = 2E}
```
Putting these blocks all together, we get the text: "**The flag is picoCTF{7R4N5P051N6_15_3XP3N51V3_109AB02E}**"

## Vigenere
This challenge gave us a .txt file containing the following encrypted message:
```
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_f85729e7}
```
The clue gives us the key "CYLAB", which should produce the flag for us when we put it into an [online Vignere decryption tool](https://www.dcode.fr/vigenere-cipher).

![Vignere Cipher Tool](https://i.imgur.com/Uumbu6b.png)

This produces the flag: **picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_d85729g7}**

## ReadMyCert
This challenge gives us a .csr file, which is a certificate request. These can't be opened by default on Windows without installing OpenSSL, so I dragged the file into Kali Linux (which has OpenSSL pre-installed) on my VM to see the contents of the file.

![readmycert.csr](https://i.imgur.com/657ZQMV.png)

The flag is: **picoCTF{read_mycert_693f7c03}**

