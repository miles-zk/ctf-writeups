# Ph4nt0m 1ntrud3r - Forensics (03/13/2025)
```
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.
To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!
Find the PCAP file here Network Traffic PCAP file and try to get the flag.
```
This challenge gave us the pcap file `myNetworkTraffic.pcap` and instructed us to find the flag within it. As with all other challenges I've encountered with pcap files, Wireshark was the tool which we used to solve the challenge.

![image](https://github.com/user-attachments/assets/5b65d3f7-93a0-456e-a5dd-eb20e0f3a941)

In the pcap there were only 22 packets present, which gives us the luxury of being able to manually sift through the packets for data. What caught my eye in doing so was the base64-encoded strings located in the binaries of some of the packets.
```
Frame 1: bnRfdGg0dA== --> nt_th4t
Frame 8: YmhfNHJfMw== --> bh_4r_3
Frame 12: NmY0YTY2Ng== --> 6f4a666
Frame 13: XzM0c3lfdA== --> _34sy_t
Frame 17: ezF0X3c0cw== --> {1t_w4s
Frame 20: cGljb0NURg== --> picoCTF
```

These decoded strings together make up what appears to be a jumbled flag, which can be organized to be the actual flag: `picoCTF{1t_w4snt_th4t_34sy_tbh_4r_36f4a666}`
