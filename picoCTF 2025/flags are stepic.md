# flags are stepic - Forensics - (03/13/2025)
```
A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message
Additional details will be available after launching your challenge instance.
```
Upon launching the instance, we are given a website with *mostly* country flags.

![flags](https://miah.s-ul.eu/86CFF6aI)

Further down on the website there's a flag which isn't the flag for an actual country.

![upanzi](https://miah.s-ul.eu/rAv8FEqd)

After downloading this flag, we use the python stepic library (as the name of this challenge implies) to decode the challenge flag from the fake flag.
```
import stepic
from PIL import Image

# Path to the image
image_path = r"C:\Users\Miles\Desktop\picoCTF\upz.png"

# Open the image
try:
    img = Image.open(image_path)
    
    # Decode the hidden message
    decoded_data = stepic.decode(img)
    
    # Print the extracted message
    print("Decoded message:", decoded_data)
except Exception as e:
    print("Error:", e)
```
![flagstepic](https://miah.s-ul.eu/6jwDPkGP)

Flag: `picoCTF{fl4g_h45_fl4g1a2a9157}`
