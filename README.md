# file2bin

`file2bin` is a single-file web tool (`file2bin.html`) for converting files to and from `.bin` (hex), with optional browser-side encryption.

## Features

- Single-file app: HTML, CSS, and JavaScript are all in `file2bin.html`
- Local processing in the browser (no backend required)
- Two-way conversion:
  - file → `.bin` (hex)
  - `.bin` (hex) → file
- Optional encryption via Web Crypto API (`aes-256-gcm` + `pbkdf2`)
- Mobile-first layout (max content width: 600px)

## Requirements

- A modern browser with Web Crypto API support (Chrome, Edge, Safari, Firefox)

## Usage

### Option 1: Open directly

Open `file2bin.html` in your browser.

### Option 2: Serve locally

```bash
python3 -m http.server 8080
```

Then visit <http://localhost:8080/file2bin.html>.

## Notes

- Processing is done locally in your browser; files are not uploaded by this app.
- Use a strong password for encryption.
- If you forget the password, encrypted content cannot be recovered.

## Project Structure

```text
.
├── file2bin.html   # main app (runtime file)
├── DESIGN.md       # design reference document
├── LICENSE
└── README.md
```

## License

MIT License - see `LICENSE`
