## morse-code - Medium - (02/25/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/280?category=2&difficulty=2&page=2)

In this challenge, we're given a .wav file that, as the name of the challenge entails, plays morse code when opened.
Upon opening the file in Audacity, we can start to break down the message being sent.

![Audacity Screenshot](https://i.imgur.com/twQGdKy.png)

Identifying each large bar as a -, each small bar as a ., and the larger spaces as a space, we can derive the morse code into text form to be:
```
.__ .... ...._ __... .... ...._ __... .... ____. _____ _.. .__ ..___ _____ .._ ____. .... __...
```
Which when put into an online [morse code translator](https://morsecode.world/international/translator.html) produces the text "WH47H47H90DW20U9H7" which is leet speak for "WHAT HATH GOD WROUGHT", with some formatting it produces the flag: **picoCTF{wh47_h47h_90d_w20u9h7)**
