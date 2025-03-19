## hideme - Medium - (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/350?category=4&difficulty=2&page=1)

Another steganography challenge: this one gives us the scenario that a SOC analyst saw an image being sent back and forth between two people and wanted to investigate, giving us a png file.
Within the `cat` output of the file, I found this suspicious string:

![hidemeCat](https://i.imgur.com/m85mZZs.png)

This led me to believe that, once again, this flag was somehow embedded in the given file. By converting the image to .rar and opening it in WinRAR, I was able to find the flag embedded in a folder called secret under the name flag.png: `picoCTF{Hiddinng_An_imag3_within_@n_ima9e_85e04ab8}`

![hidemesecret](https://i.imgur.com/PzmJG5B.png)
