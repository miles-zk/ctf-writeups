# Forgotten Footprints - Forensics - (03/15/2025)

```
I didn't want anyone to find the flag, so I hid it away. Unfortunately, I seem to have misplaced it.
```

This given file of this challenge is `disk.img`, of which the scenario claims that the user has misplaced it. Mounting the disk image produces a directory with a bunch of text files containing random data.

I figured it was going to take too long to find the flag by searching the text files for any encoded strings (although looking back on it and seeing the writeups of others makes me realize it would've been quicker to search for various encoded variants of the flag format `UTCTF{`, but I digress). So I put it into [Autopsy](https://en.wikipedia.org/wiki/Autopsy_(software)) and began searching through the unallocated space in the disk image because of the hint saying they "misplaced the data."

After searching through 831 pages of empty Hex content, 832 shows a long sequence of hexadecimal values which could contain the flag.

![forgottenflag](https://i.imgur.com/cF05qtt.png)

Upon entering this massive string of hex values into [Cyberchef](https://gchq.github.io/CyberChef/) and decoding from Hex, the flag is produced.

![flag](https://i.imgur.com/9B7SF5E.png)

The flag is: `utflag{d3l3t3d_bu7_n0t_g0n3_4ever}`
