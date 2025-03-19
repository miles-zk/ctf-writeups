## St3g0 - Medium - (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/305?category=4&difficulty=2&page=1)

This is a steganography challenge which gives us a .png file and instructs us to find the flag in it. During this challenge, I came across a very valuable resource for steganography challenges in [0xRick's blog](https://0xrick.github.io/lists/stego/) which lists a ton of resources for conducting stego. For this particular problem, Zsteg was the tool which saved the day; by running `zsteg -a pico.flag.png`, I was able to find the flag: `picoCTF{7h3r3_15_n0_5p00n_96ae0ac1}`

![Steg0Flag](https://i.imgur.com/eNsbgYc.png)
