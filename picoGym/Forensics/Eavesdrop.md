## Eavesdrop - Medium (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/264?category=4&difficulty=2&page=2)

This challenge gives us a .pcap file and instructs us to find the flag in it, with no hints being given directly in the description. Upon opening the file in wireshark, we see that the primary content of the pcap is a conversation between
`10.0.2.15` and `10.0.2.3` over TCP port 9001.

![PCAP Screenshot](https://i.imgur.com/qpJsCg7.png)

By right clicking on one of these conversational packets and selecting the 'Follow TCP Stream' option on Wireshark, we can see the contents of the conversation between the two hosts.

![Conversation Screenshot](https://i.imgur.com/S3nE0Jn.png)

This tells us that one of the users is transmitting an encrypted file over port 9002, which as stated in the screenshot, can be decrypted using OpenSSL using the command `openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123`. To find the conversation over port 9002, we can use the Wireshark filter `tcp.port == 9002`, and then follow that conversation.

![Salt](https://i.imgur.com/W0TcIqk.png)

By changing the 'show data' dropdown on this window to 'Raw' and then saving it as 'file.des3' as the OpenSSL command has it, I have everything I need to decrypt the file and find the flag: `picoCTF{nc(73115_411_0ee7267a}`
