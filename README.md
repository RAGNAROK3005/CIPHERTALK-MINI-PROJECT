# 🔒 CIPHERTALK-MINI-PROJECT

A modern, full-stack cipher application featuring encrypted communication with a sleek cyberpunk-inspired interface. CipherTalk implements **Caesar cipher** encryption/decryption with both a C backend and an interactive web frontend.

---

## 📋 Overview

**CipherTalk** is a mini project demonstrating cryptographic principles through a practical, user-friendly application. All encryption runs **100% offline** in your browser—your messages never leave your device. The project showcases:

- **Frontend**: Modern HTML/CSS/JavaScript with a neon cyber console UI
- **Backend**: C implementation of Caesar cipher logic
- **CGI Integration**: C-based CGI program for server-side cipher operations
- **Security**: Client-side encryption—zero data transmission to servers

---

## ✨ Features

### 🔐 **Zero Data Leaves**
All encryption runs locally in your browser. Your messages never touch a server—complete privacy guaranteed.

### 🧠 **C-Powered Logic**
The application mirrors a documented C backend (Caesar cipher) that you can compile and run yourself. JavaScript implementation matches the C backend behavior perfectly.

### ⚡ **Instant Cipher**
Tweak the shift key and watch your text transform character by character in real-time with a smooth, responsive UI.

### 🎨 **Cyberpunk UI**
- Neon cyan and purple gradient design
- Glass-morphism effects with blur and opacity
- Scanline overlay effects
- Smooth animations and transitions
- Fully responsive (mobile & desktop)

### 📱 **Responsive Design**
Works seamlessly on desktop, tablet, and mobile devices with adaptive layouts.

### 🔧 **Educational**
Perfect for learning cryptographic concepts, web development, and C programming.

---

## 🛠 Project Structure

```
CIPHERTALK-MINI-PROJECT/
├── README.md              # This file
├── index.html             # Main landing page
├── ciphertalk.html        # Complete single-file cipher console
├── cipher.c               # C implementation of Caesar cipher
├── cipher_cgi.c           # CGI wrapper for server-side execution
```

### File Descriptions

| File | Purpose |
|------|---------|
| `ciphertalk.html` | Complete interactive cipher console with HTML/CSS/JS—runs 100% in browser |
| `cipher.c` | Core Caesar cipher implementation in C with encrypt/decrypt functions |
| `cipher_cgi.c` | CGI program for server integration (C backend) |
| `index.html` | Landing/welcome page |

---

## 🚀 Getting Started

### Prerequisites

- **For the web interface**: Any modern browser (Chrome, Firefox, Safari, Edge)
- **For C backend**: GCC or compatible C compiler
- **Optional**: A web server with CGI support (for deploying cipher_cgi.c)

### Installation

#### Option 1: Use the Web Interface (No Installation Needed)

1. Clone the repository:
   ```bash
   git clone https://github.com/RAGNAROK3005/CIPHERTALK-MINI-PROJECT.git
   cd CIPHERTALK-MINI-PROJECT
   ```

2. Open `ciphertalk.html` in your browser:
   ```bash
   open ciphertalk.html    # macOS
   # or
   xdg-open ciphertalk.html # Linux
   # or simply double-click the file in Windows
   ```

#### Option 2: Compile and Run the C Backend

1. Compile `cipher.c`:
   ```bash
   gcc -o cipher cipher.c
   ```

2. Run the cipher:
   ```bash
   ./cipher encrypt 3 "HELLO"    # Output: KHOOR
   ./cipher decrypt 3 "KHOOR"    # Output: HELLO
   ```

#### Option 3: Compile CGI Program (For Web Servers)

1. Compile `cipher_cgi.c`:
   ```bash
   gcc -o cipher_cgi.cgi cipher_cgi.c
   ```

2. Copy to your web server's CGI directory (typically `/cgi-bin/`)
3. Make it executable:
   ```bash
   chmod +x cipher_cgi.cgi
   ```

---

## 📖 Usage

### Web Interface

1. **Open** `ciphertalk.html` in your browser
2. **Enter** your message in the input textarea
3. **Set** the shift key (1-25, default: 3)
4. **Click** "🔒 Encrypt" or "🔓 Decrypt"
5. **Copy** the result with the copy button

#### Example:
- **Input**: `Hello World`
- **Shift Key**: `3`
- **Encrypted**: `Khoor Zruog`

### Command Line (C Binary)

```bash
./cipher <mode> <shift> <text>
```

**Parameters:**
- `<mode>`: `encrypt` or `decrypt`
- `<shift>`: Number 1-25 (shift amount)
- `<text>`: Your message

**Examples:**
```bash
./cipher encrypt 5 "ATTACK AT DAWN"
# Output: FYYFHP FY IFBS

./cipher decrypt 5 "FYYFHP FY IFBS"
# Output: ATTACK AT DAWN
```

---

## 🔧 How It Works

### Caesar Cipher Algorithm

The Caesar cipher shifts each letter by a fixed number of positions in the alphabet:

```
Plain:  A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
Shift3: D E F G H I J K L M N O P Q R S T U V W X Y Z A B C
```

**Encryption**: `letter → (letter + shift) mod 26`  
**Decryption**: `letter → (letter - shift) mod 26`

### Key Features of Implementation

- **Handles both uppercase and lowercase** letters
- **Preserves non-alphabetic characters** (numbers, punctuation, spaces)
- **Normalizes shift values** (shift 27 = shift 1)
- **Handles negative shifts** for decryption
- **Zero-allocation for web version** (no memory concerns)

### C Code Overview

```c
void caesar_encrypt(char *text, int shift) {
    int s = normalize_shift(shift);
    for (size_t i = 0; text[i] != '\0'; i++) {
        unsigned char ch = (unsigned char) text[i];
        if (ch >= 'A' && ch <= 'Z') {
            text[i] = (char) (((ch - 'A' + s) % 26) + 'A');
        } else if (ch >= 'a' && ch <= 'z') {
            text[i] = (char) (((ch - 'a' + s) % 26) + 'a');
        }
    }
}
```

---

## 🎨 UI Features

### Interactive Console
- Real-time shift key adjustment
- Live input/output preview
- Syntax-highlighted output
- Loading spinner for visual feedback

### Design Elements
- **Color Scheme**: Dark cyberpunk aesthetic with neon accents
- **Primary Colors**: 
  - Cyan (`#3ddcff`)
  - Purple (`#b46bff`)
  - Pink (`#ff4dd2`)
  
### CSS Highlights
- Glass-morphism with backdrop blur
- Gradient backgrounds and text
- Scanline overlay effects
- Smooth transitions and animations
- Responsive grid layouts

---

## 🧪 Testing

### Test Cases

| Input | Shift | Mode | Expected Output |
|-------|-------|------|-----------------|
| HELLO | 3 | Encrypt | KHOOR |
| KHOOR | 3 | Decrypt | HELLO |
| abc123XYZ! | 1 | Encrypt | bcd123YZA! |
| The Quick Brown Fox | 5 | Encrypt | Ymj Fzrnf Gsvyp Yjc |

### Run Tests

1. **Web Console**: Use the browser's developer console for quick tests
2. **C Binary**: 
   ```bash
   ./cipher encrypt 3 "TEST"
   ./cipher decrypt 3 "WHVW"
   ```

---

## 📦 Technology Stack

| Technology | Purpose |
|-----------|---------|
| **HTML5** | Semantic markup & structure |
| **CSS3** | Modern styling with gradients, animations, glass-morphism |
| **JavaScript (ES6+)** | Caesar cipher logic, DOM manipulation, event handling |
| **C** | Backend cipher implementation & CGI integration |
| **GCC** | C compiler for building the backend |

---

## 🔒 Security Notes

### What This Is
- **Educational**: Demonstrates cryptographic concepts
- **Example Implementation**: Shows how basic ciphers work
- **Proof of Concept**: Illustrates client-side encryption principles

### What This Is NOT
- **Production-Ready**: Caesar cipher is easily breakable
- **For Real Security**: Use industry-standard encryption (AES, RSA, TLS)
- **Suitable for Sensitive Data**: This is for learning, not protecting real secrets

### Real-World Security
For actual secure communication, use:
- **TLS/HTTPS** for data in transit
- **AES-256** for symmetric encryption
- **RSA/ECDSA** for asymmetric operations
- **bcrypt/Argon2** for password hashing

---

## 🚀 Deployment

### Option 1: GitHub Pages
1. Enable GitHub Pages in repository settings
2. Choose `main` branch as source
3. Access your site at `https://RAGNAROK3005.github.io/CIPHERTALK-MINI-PROJECT/`

### Option 2: Traditional Web Server
1. Copy `ciphertalk.html` and `index.html` to your web server
2. Compile `cipher_cgi.c` for server-side operations
3. Configure CGI directory and permissions
4. Access via your domain

### Option 3: Local Development
```bash
# Simple Python HTTP server
python -m http.server 8000

# Then open: http://localhost:8000/ciphertalk.html
```

---

## 📝 License

This project is provided as-is for educational purposes. Feel free to fork, modify, and learn from it.

---

## 👨‍💻 Author

**RAGNAROK3005** - [GitHub Profile](https://github.com/RAGNAROK3005)

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. **Fork** this repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Potential Enhancements
- [ ] Support for additional cipher types (Vigenère, Substitution, etc.)
- [ ] Frequency analysis tool
- [ ] Brute-force decryption (try all shifts)
- [ ] Text file upload/download
- [ ] Multiple language support
- [ ] Dark/Light mode toggle
- [ ] Keyboard shortcuts
- [ ] Decryption hints system

---

## 📚 Resources & Learning

### Caesar Cipher
- [Wikipedia - Caesar Cipher](https://en.wikipedia.org/wiki/Caesar_cipher)
- [Khan Academy - Cryptography](https://www.khanacademy.org/computing/computer-science/cryptography)

### Web Development
- [MDN Web Docs - JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [CSS Tricks - CSS Reference](https://css-tricks.com/)

### C Programming
- [C Programming Guide](https://www.cprogramming.com/)
- [GCC Documentation](https://gcc.gnu.org/onlinedocs/)

---

## ⚠️ Troubleshooting

### Web Interface Not Working
- **Issue**: JavaScript disabled
- **Solution**: Enable JavaScript in browser settings

### C Binary Compilation Error
- **Issue**: `gcc: command not found`
- **Solution**: Install GCC:
  - **Ubuntu/Debian**: `sudo apt install build-essential`
  - **macOS**: `xcode-select --install`
  - **Windows**: Install MinGW or MSVC

### CGI Script Permission Denied
- **Issue**: `Permission denied` when running `.cgi`
- **Solution**: 
  ```bash
  chmod +x cipher_cgi.cgi
  chmod 755 cipher_cgi.cgi
  ```

---

## 📞 Support

Have questions or found an issue? 

- **GitHub Issues**: [Open an Issue](https://github.com/RAGNAROK3005/CIPHERTALK-MINI-PROJECT/issues)
- **Discussions**: Check existing issues first to avoid duplicates

---

## 🎯 Roadmap

- [x] Caesar cipher implementation
- [x] Web interface with modern UI
- [x] C backend integration
- [x] Documentation
- [ ] Additional cipher types
- [ ] Cryptanalysis tools
- [ ] Multi-user support
- [ ] Cloud deployment

---

**Happy Encrypting! 🔐**

*Last Updated: May 2026*
