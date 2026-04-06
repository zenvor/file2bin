# file2bin

`file2bin` is a single-file web app (`file2bin.html`) that converts files to and from `.bin` (hex), with optional browser-side encryption.

Current UI language: Chinese (zh-CN).

## Features

- Single-file app: HTML, CSS, and JavaScript are all in `file2bin.html`
- Local processing in the browser (no backend required)
- Two-way conversion:
  - file → `.bin` (hex)
  - `.bin` (hex) → file
- Optional encryption via Web Crypto API (`aes-256-gcm` + `pbkdf2`)
- Mobile-first layout (max content width: 600px)

## Requirements

- A modern browser with Web Crypto API support
- Secure Context is required for encryption/decryption (`https://` or `http://localhost`)

## Quick Start

### Option 1: Open directly

Open `file2bin.html` in your browser.

> Note: On `file://`, encryption/decryption may be unavailable in some browsers because `crypto.subtle` requires a Secure Context.

### Option 2: Serve locally

```bash
python3 -m http.server 8080
```

Then visit <http://localhost:8080/file2bin.html>.

## Security & Privacy Notes

- File processing is local to your browser session.
- Use a strong password when enabling encryption.
- If you lose the password, encrypted data cannot be recovered.

## Limitations

- Very large files may consume significant browser memory.
- This project currently has no automated tests.

## Project Structure

```text
.
├── file2bin.html   # main app (runtime file)
├── README.md
├── .gitignore
└── LICENSE
```

## License

MIT License - see `LICENSE`
