## transposition-trial - Medium - (02/25/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/312?category=2&difficulty=2&page=1)

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
