# Crypto, Forensics, General Skills (02/28/2025)
This was the most productive night I had on Pico yet, having completed many medium difficulty challenges in the Cryptography, Forensics, and General Skills categories. It was a total of 12 challenges, but some of them were very simple, so I've narrowed this writeup down to the eight which were the most interesting to me. I also changed up my style a bit in this writeup, listing the category and difficulty in the headers along with each challenge. Additionally, I tried to be more descriptive with my thought processes in approaching these challenges.

Completed Challenges:\
[Eavesdrop](https://play.picoctf.org/practice/challenge/264?category=4&difficulty=2&page=2)\
[St3g0](https://play.picoctf.org/practice/challenge/305?category=4&difficulty=2&page=1)\
[Serpentine](https://play.picoctf.org/practice/challenge/251?category=5&difficulty=2&page=1)\
[Matryoshka Doll](https://play.picoctf.org/practice/challenge/129?category=4&difficulty=2&page=3)\
[hideme](https://play.picoctf.org/practice/challenge/350?category=4&difficulty=2&page=1)\
[Based](https://play.picoctf.org/practice/challenge/35?category=5&difficulty=2&page=2)\
[substitution-0](https://play.picoctf.org/practice/challenge/307?category=2&page=2)\
[PcapPoisoning](https://play.picoctf.org/practice/challenge/362?category=4&difficulty=2&page=1)


## Eavesdrop (Forensics - Medium)
This challenge gives us a .pcap file and instructs us to find the flag in it, with no hints being given directly in the description. Upon opening the file in wireshark, we see that the primary content of the pcap is a conversation between
`10.0.2.15` and `10.0.2.3` over TCP port 9001.

![PCAP Screenshot](https://i.imgur.com/qpJsCg7.png)

By right clicking on one of these conversational packets and selecting the 'Follow TCP Stream' option on Wireshark, we can see the contents of the conversation between the two hosts.

![Conversation Screenshot](https://i.imgur.com/S3nE0Jn.png)

This tells us that one of the users is transmitting an encrypted file over port 9002, which as stated in the screenshot, can be decrypted using OpenSSL using the command `openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123`. To find the conversation over port 9002, we can use the Wireshark filter `tcp.port == 9002`, and then follow that conversation.

![Salt](https://i.imgur.com/W0TcIqk.png)

By changing the 'show data' dropdown on this window to 'Raw' and then saving it as 'file.des3' as the OpenSSL command has it, I have everything I need to decrypt the file and find the flag: `picoCTF{nc(73115_411_0ee7267a}`

## St3g0 (Forensics - Medium)
This is a steganography challenge which gives us a .png file and instructs us to find the flag in it. During this challenge, I came across a very valuable resource for steganography challenges in [0xRick's blog](https://0xrick.github.io/lists/stego/) which lists a ton of resources for conducting stego. For this particular problem, Zsteg was the tool which saved the day; by running `zsteg -a pico.flag.png`, I was able to find the flag: `picoCTF{7h3r3_15_n0_5p00n_96ae0ac1}`

![Steg0Flag](https://i.imgur.com/eNsbgYc.png)

## Serpentine (General Skills - Medium)
This challenge gives us a Python script and instructs us to find the flag in it. Upon execution, the script opens a prompt window with three options: print encouragement, print flag, and quit.

![PythonScript](https://i.imgur.com/Tz5cN61.png)

When choosing option b to print the flag, the message "Oops! I must have misplaced the print_flag function! Check my source code!" is displayed. Upon checking the source code, I found two code snippets which jumped out at me:
```
def print_flag():
  flag = str_xor(flag_enc, 'enkidu')
  print(flag)
```
and
```
 elif choice == 'b':
      print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')
```
which meant that the print_flag() function was being unused. By replacing the print statement under chioce B with an execution of print_flag() and then running the script again, the flag is displayed: `picoCTF{7h3_r04d_l355_7r4v3l3d_ae0b80bd}`

![SerpentineFlag](https://i.imgur.com/7vEAj3g.png)

## Matryoshka doll (Forensics - Medium)
This challenge gives us a .jpg file which displays a Matryoshka doll when opened. This challenge can be quickly solved with the knowledge that a Matryoshka doll houses other identical dolls which progressively get smaller inside of it, which made me think that this file could also have functionality as either a .zip or .rar file housing other files. After converting the original file to .rar and opening it with WinRAR, my suspicion was proved to be correct.

![Dolls](https://i.imgur.com/x5j9WZe.png)

When I changed this image along with two more subsequent image files to .rar, I was greeted by a text file with the flag: `picoCTF{336cf6d51c9d9774fd37196c1d7320ff}`

![DollFlag](https://i.imgur.com/UvFsnfa.png)

## hideme (Forensics - Medium)
Another steganography challenge: this one gives us the scenario that a SOC analyst saw an image being sent back and forth between two people and wanted to investigate, giving us a png file.
Within the `cat` output of the file, I found this suspicious string:

![hidemeCat](https://i.imgur.com/m85mZZs.png)

This led me to believe that, once again, this flag was somehow embedded in the given file. By converting the image to .rar and opening it in WinRAR, I was able to find the flag embedded in a folder called secret under the name flag.png: `picoCTF{Hiddinng_An_imag3_within_@n_ima9e_85e04ab8}`

![hidemesecret](https://i.imgur.com/PzmJG5B.png)

## Based (General Skills - Medium)
This challenge involved an understanding on how different binary encodings worked. When netcatting into the challenge server, a 45 second timer would start under which we must convert multiple encoded strings to an english word. Each time we attempted this challenge a different encoded string would be given, so speed was key in completing this challenge. The encoded word would change upon every attempt, and with each attempt we would have to discern an ASCII word encoded with Binary, Decimal, and Hexadecimal in that order. 

![Completed Challenge](https://i.imgur.com/N6fFXmH.png)

The hint for this challenge encourages players to use Python to quickly convert the values, but I decided to use ChatGPT instead to save me some time, and I would recommend any other solvers to do so as well.

Flag: `picoCTF{learning_about_converting_values_00a975ff}`

## substitution-0 (Cryptography - Medium)
This challenge gave a ciphertext which has been encrypted using a substitution cipher. We are given the encrypted message along with the key located at the top of the document.
![substitution](https://i.imgur.com/kyEaBQj.png)

By using an [online substitution cipher](https://cryptii.com/pipes/alphabetical-substitution) and inserting the given values, we are able to find the flag: `picoCTF{5UB5717U710N_3V0LU710N_59533A2E}`

![substitutionFlag](https://i.imgur.com/yyrMNHI.png)

## PcapPoisoning (General Skills - Medium)
This challenge gives us a .pcap file with the description telling us that the flag is hiding inside of it. Just like in the **Eavesdrop** challenge, I started out by opening the pcap file in Wireshark to a very ugly sight: 1510 packets of FTP and TCP data.

![FTPCAP](https://i.imgur.com/Jh4y00w.png)

My intuition for this challenge was to search the frame for picoCTF in case the flag is written in plaintext within one of the packets, so I used the filter: `frame contains "picoCTF"` to check for this.

![frameContains](https://i.imgur.com/XqlOWVk.png)

With this result, I found the flag in plaintext located in the binary which after some light formatting would reveal the flag: `picoCTF{P64P_4N4L7S1S_SU55355FUL_31010c46}`
