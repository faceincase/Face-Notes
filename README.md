<div align="center">
  
# Face Notes v1.2
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

</div>

![daw](https://github.com/user-attachments/assets/dda7cfc2-2961-4d4a-abd4-85cecb97731d)

![image](https://github.com/user-attachments/assets/af9d048e-e937-4e0a-8ad7-2e24f4dd83d9)

<br>


## Storage (`.fnote`)
Effortlessly store hundreds or even thousands of notes, all within just a few megabytes.
<br>
File format for Face Notes is called `.fnote` (old: `.facenote`, may cause compatiblity issues, but should work.)
<br>
<br>
![image](https://github.com/user-attachments/assets/2b41fe33-1c5e-495e-9e7b-a438b9e44e45)

<br>



# How to use?

- Use on [`Github`](https://faceincase.github.io/Face-Notes/face_notes.html)
- Use locally:
  - Download `face_notes.html` file
  - Open `face_notes.html` file by double click or drag it to the browser.
  - Enjoy.

# Features
- CTRL + S to save your note in **`.fnote`** format.
- Drag **`.fnote`** file to open saved notes.

# Known issues:
- Notes were encoded using `.btoa()` and `.atob()` methods, which do not actually compress data and resulted in 33% increase of file size.
 - This has been changed. Compression removed and data is saved in plain text.
