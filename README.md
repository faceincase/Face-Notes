<div align="center">
  
# Face Notes v1.2
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<img src="https://github.com/user-attachments/assets/dda7cfc2-2961-4d4a-abd4-85cecb97731d" width=700>

</div>

# 🔮 Face Notes

🚨 Under development. 🚨

Simple Notes app built on the HTML5 & CSS3.

It's a tool designed to be easy and lightweight, tasks are stored using `.fnote` format for compact size.

There's some screenshots below, you can use it anywhere as `github.io` version or run it locally by downloading the `.HTML` file

## ✨ Use on [github](https://faceincase.github.io/Face-Notes/face_notes.html)
## ✨ Use locally:
- Download `face_notes.html` file
- Open `face_notes.html` file by double click or drag it to the browser.
- Enjoy.
# 🔮 Features
- **CTRL + S** to save your note in **`.fnotes`** format.
- Drag **`.fnotes`** file to open saved notes.

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



# Known issues:
- Notes were encoded using `.btoa()` and `.atob()` methods, which do not actually compress data and resulted in 33% increase of file size.
  - This has been changed. Compression removed and data is saved in plain text.

- This compression might work better, however it is not tested nor implemented yet:
```js
async function compressData(file_data) {
    // Convert the string into a Uint8Array
    const encoder = new TextEncoder();
    const dataBuffer = encoder.encode(file_data);
  
    // Use CompressionStream to compress
    const compressedStream = new CompressionStream('deflate');
    const writer = compressedStream.getWriter();
    writer.write(dataBuffer);
    writer.close();

    // Read the compressed data
    const compressedArray = [];
    const reader = compressedStream.getReader();
    while (true) {
        const { done, value } = await reader.read();
        if (done) break;
        compressedArray.push(value);
    }
  
    // Combine the chunks of compressed data
    return new Blob(compressedArray).arrayBuffer();
}

async function decompressData(compressedBuffer) {
    // Create a DecompressionStream to decompress
    const decompressedStream = new DecompressionStream('deflate');
    const writer = decompressedStream.getWriter();
  
    // Write the compressed buffer to decompression stream
    const compressedArray = new Uint8Array(compressedBuffer);
    writer.write(compressedArray);
    writer.close();

    // Read the decompressed data
    const decompressedArray = [];
    const reader = decompressedStream.getReader();
    while (true) {
        const { done, value } = await reader.read();
        if (done) break;
        decompressedArray.push(value);
    }

    // Combine the chunks of decompressed data
    const resultBuffer = await new Blob(decompressedArray).arrayBuffer();

    // Decode the result back to a string
    const decoder = new TextDecoder();
    return decoder.decode(resultBuffer);
}
```
