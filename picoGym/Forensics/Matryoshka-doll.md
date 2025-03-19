## Matryoshka Doll - Medium - (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/129?category=4&difficulty=2&page=3)

This challenge gives us a .jpg file which displays a Matryoshka doll when opened. This challenge can be quickly solved with the knowledge that a Matryoshka doll houses other identical dolls which progressively get smaller inside of it, which made me think that this file could also have functionality as either a .zip or .rar file housing other files. After converting the original file to .rar and opening it with WinRAR, my suspicion was proved to be correct.

![Dolls](https://i.imgur.com/x5j9WZe.png)

When I changed this image along with two more subsequent image files to .rar, I was greeted by a text file with the flag: `picoCTF{336cf6d51c9d9774fd37196c1d7320ff}`

![DollFlag](https://i.imgur.com/UvFsnfa.png)
