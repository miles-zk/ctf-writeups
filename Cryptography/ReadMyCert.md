## ReadMyCert - Medium - (02/25/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/367?category=2&difficulty=2&page=1)

This challenge gives us a .csr file, which is a certificate request. These can't be opened by default on Windows without installing OpenSSL, so I dragged the file into Kali Linux (which has OpenSSL pre-installed) on my VM to see the contents of the file.

![readmycert.csr](https://i.imgur.com/657ZQMV.png)

The flag is: **picoCTF{read_mycert_693f7c03}**
