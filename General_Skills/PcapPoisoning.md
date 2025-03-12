## PcapPoisoning - Medium - (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/362?category=4&difficulty=2&page=1)

This challenge gives us a .pcap file with the description telling us that the flag is hiding inside of it. Just like in the **Eavesdrop** challenge, I started out by opening the pcap file in Wireshark to a very ugly sight: 1510 packets of mostly FTP and TCP data.

![FTPCAP](https://i.imgur.com/Jh4y00w.png)

My intuition for this challenge was to search the frame for picoCTF in case the flag is written in plaintext within one of the packets, so I used the filter: `frame contains "picoCTF"` to check for this.

![frameContains](https://i.imgur.com/XqlOWVk.png)

With this result, I found the flag in plaintext located within the binary of the packet, which after some light formatting would reveal the flag: `picoCTF{P64P_4N4L7S1S_SU55355FUL_31010c46}`
