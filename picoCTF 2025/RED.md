# RED - Forensics - (03/13/2025)
```
RED, RED, RED, RED
Download the image: red.png
```
This challenge gives us `RED.png` which is just a red square in an image file. Because it's a png file, we can use zsteg to search the image for any steganography hidden in RED.png.<br>

![redzsteg](https://i.imgur.com/ocageux.png)<br>

The first line of text is a very heartfelt poem which was probably meant to be sent to someone else. But we aren't here for that, because there's a Base64 encoded string which we can decode in the next line!

![base64decoder](https://i.imgur.com/kaPMQTm.png)

The flag is: `picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}`

