# Event-Viewing - Forensics (03/13/2025)
```
One of the employees at your company has their computer infected by malware! Turns out every time they try to switch on the computer, it shuts down right after they log in. The story given by the employee is as follows:
They installed software using an installer they downloaded online
They ran the installed software but it seemed to do nothing
Now every time they bootup and login to their computer, a black command prompt screen quickly opens and closes and their computer shuts down instantly.
See if you can find evidence for the each of these events and retrieve the flag (split into 3 pieces) from the correct logs!
Download the Windows Log file here
```
This challenge gives us a Windows Log file and tells us 3 events which we should find in the event logs which could be related to the flag.

`1. They installed software using an installer they downloaded online`

To find this piece of the flag, I searched for EventIDs related to software installation. EventID 1033 was a hit for the installation of software called `Totally_Legit_Software` and the event log had a Base64 encoded string which when decoded produces a part of the flag.

![flagpiece1](https://i.imgur.com/jFUesAA.png)<br>
The base64 translates to: picoCTF{Ev3nt_vi3wv3r_

`2. They ran the installed software but it seemed to do nothing`

"It seemed to do nothing" is a red herring here based on what is said in the next sentence, with the description in part 3, I inferred that the software added itself in the startup apps, which might be reflected in a Windows Registry related EventID. The hit for this piece of the flag was located in an event with the ID of 4657, and contained another Base64 encoded string.<br>

![flagpiece2](https://i.imgur.com/myeDzfV.png)<br>
The base64 translates to: 1s_a_pr3tty_us3ful_

`3. Now every time they bootup and login to their computer, a black command prompt screen quickly opens and closes and their computer shuts down instantly.`

This one was obvious, we had to find an EventID related to system shutdown in some way. 1074 being the most common one for shutdowns meant I was likely to find the answer there, and I did.
![flagpiece3](https://i.imgur.com/DIy8Nnl.png)<br>
The base64 translates to: t00l_81ba3fe9}

Now, having all pieces of the flag, we just have to put it together: `picoCTF{Ev3nt_vi3wv3r_1s_a_pr3tty_us3ful_t00l_81ba3fe9}`
