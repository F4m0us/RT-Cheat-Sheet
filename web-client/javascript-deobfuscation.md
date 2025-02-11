# JavaScript Deobfuscation Cheat Sheet  
📌 *Inspired by the HTB Academy module*  

## 🔍 Viewing JavaScript Source Code  
- **View Page Source**: **`Ctrl + U`** (Windows/Linux) or **`Cmd + Option + U`** (Mac)  
- **Open Developer Tools**:  
  - **Chrome** / **Edge**: `F12` or `Ctrl + Shift + I`  
  - **Firefox**: `F12` or `Ctrl + Shift + I`  
  - **Safari**: `Cmd + Option + I` (Enable "Show Developer menu" in Preferences)  
- **Inspect JavaScript in DevTools**:  
  - Open the **Console** tab to test JavaScript code  
  - Use the **Sources** tab to locate and format JavaScript files  
- **Find JavaScript in Network Requests**:  
  - Open **DevTools** → **Network** → **JS** to see loaded scripts    
- **Download JavaScript Files**:  
  - Manually from the **Sources** tab in DevTools  
  - Use `wget` or `curl`:  
    ```sh
    wget https://example.com/script.js
    ```
    ```sh
    curl -O https://example.com/script.js
    ```
- **Use a Proxy to Intercept JavaScript**:  
  - [Burp Suite](https://portswigger.net/burp) – Inspect and modify JavaScript requests  
  - [mitmproxy](https://mitmproxy.org/) – Intercept & analyze JavaScript in HTTP/HTTPS traffic    

## ✨ Analyzing JavaScript Code
Use these tools to make minified or compressed JavaScript more readable:  

- [Prettier Playground](https://prettier.io/playground/) – Automatic code formatting  
- [JS Beautifier](https://beautifier.io/) – Beautifies and formats JavaScript code
- [Toptal Minifier](https://www.toptal.com/developers/javascript-minifier) – Minify/Beautify JavaScript
- [JSConsole](https://jsconsole.com/) – Execute JavaScript from an external console

## 🛠 Deobfuscation Tools  
These tools help reverse JavaScript obfuscation and restore original code:  

- [unPacker](https://matthewfl.com/unPacker.html)
- [Deobfuscate.io](https://deobfuscate.io/)  
- [Relative.im Deobfuscator](https://deobfuscate.relative.im/)  
- [dCode JavaScript Unobfuscator](https://www.dcode.fr/javascript-unobfuscator)  
- [de4js](https://lelinhtinh.github.io/de4js/)
- [Synchrony (GitHub)](https://github.com/relative/synchrony)

## 🎭 Common JavaScript Obfuscators  
Obfuscators transform JavaScript into an unreadable format. Here are some common ones:  

- [JS Obfuscator](https://beautifytools.com/javascript-obfuscator.php)  
- [Obfuscator.io](https://obfuscator.io/)  
- [JSFuck (Extreme Obfuscation)](https://jsfuck.com/)  
- [JJEncode](https://utf-8.jp/public/jjencode.html)  
- [AAEncode](https://utf-8.jp/public/aaencode.html)
