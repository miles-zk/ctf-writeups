## Based - Medium - (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/35?category=5&difficulty=2&page=2)

This challenge involved an understanding on how different binary encodings worked. When netcatting into the challenge server, a 45 second timer would start under which we must convert multiple encoded strings to an english word. Each time we attempted this challenge a different encoded string would be given, so speed was key for success. The encoded word would change upon every attempt, and with each attempt we would have to discern an ASCII word encoded with Binary, Decimal, and Hexadecimal in that order. 

![Completed Challenge](https://i.imgur.com/N6fFXmH.png)

The hint for this challenge encourages players to use Python to quickly convert the values, but I decided to use ChatGPT instead to save me some time, and I would recommend any other solvers to do so as well.

Flag: `picoCTF{learning_about_converting_values_00a975ff}`
