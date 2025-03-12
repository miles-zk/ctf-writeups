## Serpentine - Medium - (02/28/2025)
[Link to challenge](https://play.picoctf.org/practice/challenge/251?category=5&difficulty=2&page=1)

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
