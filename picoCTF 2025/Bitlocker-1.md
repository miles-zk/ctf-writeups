# Bitlocker-1 - Forensics - (03/13/2025)
```
Jacky is not very knowledgable about the best security passwords and used a simple password to encrypt their BitLocker drive. See if you can break through the encryption!
Download the disk image here
```
This challenge gave us the dd file `bitlocker-1.dd` and our job is to find the password to the BitLocker drive. The scenario states that Jacky used a simple password to encrypt their drive, so I knew that this challenge would be one which involves brute forcing the password using John the Ripper or HashCat with a known wordlist such as [rockyou](https://en.wikipedia.org/wiki/RockYou).

After mounting the image and extracting the BitLocker hash from the image using the command <br>`bitlocker2john -i bitlocker-1.dd > bitlocker_hash.txt`

Then we loaded these hashes up into [John the Ripper](https://en.wikipedia.org/wiki/John_the_Ripper) and let it run for a while until it hit a password.<br>
`john --wordlist=rockyou.txt --format=bitlocker bitlocker_hash.txt`

After a while, it stumbled on the password to be 'jacqueline', which upon use gave us access to the files including `flag.txt.` which contained the flag.
`flag: picoCTF{us3_b3tt3r_p4ssw0rd5_pl5!_3242adb1}`
