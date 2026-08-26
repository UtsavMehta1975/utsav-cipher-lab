# Guptlekh kitchen vs CyberChef

> **Magic Tool master checklist:** see [MAGIC_TODO.md](./MAGIC_TODO.md). Architecture notes: [ANALYSIS.md](./ANALYSIS.md).

This lab is **one HTML page**. It will never clone all ~500 CyberChef operations. Detect working comes first.

Kitchen catalog: **504** unique CyberChef names (Favourites duplicates some). **125** bake in this page (bright). **379** are ghosts (faded).

---

## Done (bakes in this page)

**Detect / Magic**

- Caesar / ROT13 (all 26 shifts, cheap `caesarShift`)
- Nested encodings then classical (Base64 of Caesar names Caesar)
- Hex, Base64, Morse, URL, HTML entities, quoted-printable, and similar unwraps
- Vigenère with a known keyword (`KEY` and a small word list)
- Hash **length families** (32 hex → MD5-sized, etc.) — length is not a proof
- Optional key field: shift, Vigenère keyword, XOR, AES-CBC passphrase
- X-ray of what was tried; **Bake in kitchen** loads the recipe
- Braille (six-dot) → **From Braille** when the paste looks like Braille

**Kitchen (bakeable now, 125 ops)**

- Encodings: Hex, Hexdump (to **and** from), Binary, Octal, Decimal, Charcode, Base32/45/58/62/64/85/92, HTML entities, URL, Unicode escapes, Quoted-printable, Punycode (domain names only), Hex Content (SNORT `|3d|` style), Braille
- Classroom: ROT13 (+ brute), ROT47 (+ brute), ROT8000, XOR (+ single-byte brute), Vigenère, Atbash, Affine, A1Z26, Rail Fence, Morse, Bacon, Substitute
- Crypto that can run here: AES-CBC (needs a key), HMAC, SHA-1/2, MD5, PBKDF2, JWT Decode / Sign / Verify (HS256–HS512 only)
- Compression: Gzip / Gunzip, Zlib Deflate / Inflate, Raw Deflate / Inflate (browser `CompressionStream` where supported; input may be hex)
- Utils: case, reverse, whitespace, split/head/tail, drop/take bytes, JSON tidy, extractors (IPs, emails, URLs, hashes, **domains**, **dates**), entropy / IOC / chi-square, Magic, Comment

---

## Needs a library or a server

Bring a JS library **you accept**, or a small server — these stay ghosts for now:

- ChaCha, Salsa20, XSalsa20, Rabbit, Blowfish, Twofish, DES / 3DES, RC4, SM4, TEA/XTEA
- PGP encrypt/decrypt/sign, RSA encrypt/decrypt, ECDSA, JWT with RSA/ECDSA
- Bzip2, LZMA, LZ4, Zip/Unzip, Tar
- Image / EXIF / QR / PDF / disassemble
- HTTP request, DNS over HTTPS (need a network proxy; browsers block raw sockets)

---

## Impossible without a key (or a header)

Random hex / Base64 of the same length **cannot** be named as AES vs ChaCha vs Salsa vs RSA ciphertext vs a hash. They all look like noise.

Detect will say **high entropy · modern crypto / PRNG** and list that family. It will **not** pick a winner.

Exceptions: a **header** (PEM, Fernet `gAAAAA…`, OpenSSL `Salted__`, JWT) or a **working key** you type in the optional key box.

Hashes are one-way. Analyse hash only matches **length**.
