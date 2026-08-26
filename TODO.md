# Guptlekh kitchen vs CyberChef

> **Magic Tool master checklist:** see [MAGIC_TODO.md](./MAGIC_TODO.md). Architecture notes: [ANALYSIS.md](./ANALYSIS.md).

This lab is **one HTML page**. It will never clone all ~500 CyberChef operations. Detect working comes first.

Kitchen catalog: **504** unique CyberChef names (Favourites duplicates some). **228** bake in this page (bright). **276** are ghosts (faded).

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
- Bifid (period) when decode looks English

**Kitchen (bakeable now, 228 ops)**

- Encodings: Hex, Hexdump (to **and** from), Binary, Octal, Decimal, Charcode, Base32/45/58/62/64/85/92, Modhex, BCD, HTML entities, URL, Unicode escapes / normalize / smart chars, Quoted-printable, MIME encoded-word, Punycode (domain names only), Hex Content (SNORT `|3d|` style), Braille, Swap endianness, Show Base64 offsets, PEM↔Hex, COBS, Caret/M-decode
- Classroom: ROT13 (+ brute), ROR13, ROT47 (+ brute), ROT8000, XOR (+ single-byte brute), Vigenère, Atbash, Affine, A1Z26, Rail Fence, Morse, Bacon, Bifid, Caesar Box, Cetacean, Substitute
- Crypto that can run here: AES-CBC (needs a key), HMAC, SHA-1/2, MD5, PBKDF2, HKDF, JWT Decode / Sign / Verify (HS256–HS512 only), TOTP / HOTP
- Compression: Gzip / Gunzip, Zlib Deflate / Inflate, Raw Deflate / Inflate (browser `CompressionStream` where supported; input may be hex)
- Checksums: Adler-32, Fletcher-8/16/32/64, Luhn, CRC-32, XOR checksum, Parity, TCP/IP checksum
- Arithmetic / logic / sets: OR/AND/NOT/ADD/SUB, Sum/Subtract/Multiply/Divide/MOD, Mean/Median/StdDev, bit shifts & rotates, Extended GCD, Modular Inverse / Exponentiation, set union/intersection/difference/symmetric difference
- Utils: case (snake/camel/kebab/alternating/all casings), reverse, whitespace / null / ANSI / diacritics, wrap/pad/table, split/filter/head/tail, drop/take / nth bytes, sort/shuffle/unique, find/replace, regex, expand alphabet, Hamming/Levenshtein, offset checker, Diff, Sleep, JSON tidy, CSV↔JSON, escape/unescape, Strip HTML / HTML To Text, Leet, NATO, Strings, Defang/Fang URL & IP, unit convert (data sizes), PRNG, Lorem, Numberwang, XKCD 4
- Extractors: IPs, emails, URLs, hashes, domains, dates, MAC addresses, file paths
- Networking-ish (pure text): Parse URI, Strip HTTP headers, Dechunk, Change IP format, Format MAC, NetBIOS name encode/decode, VarInt
- Date/time: From/To UNIX Timestamp, Windows Filetime ↔ UNIX, Get Time, Generate/Analyse UUID, Parse ObjectID timestamp, Parse colour, Parse UNIX permissions
- Metrics: entropy / frequency / IOC / chi-square, Analyse hash, Magic, Comment

---

## Needs a library or a server

Bring a JS library **you accept**, or a small server — these stay ghosts for now:

- ChaCha, Salsa20, XSalsa20, Rabbit, Blowfish, Twofish, DES / 3DES, RC4, SM4, TEA/XTEA, PRESENT, Ascon, GOST block, Fernet, LS47, CipherSaber
- PGP encrypt/decrypt/sign, RSA encrypt/decrypt, ECDSA, SM2, JWT with RSA/ECDSA
- Bzip2, LZMA, LZ4, Zip/Unzip, Tar, LZString
- Image / EXIF / QR / PDF / disassemble / YARA / charts
- HTTP request, DNS over HTTPS (need a network proxy; browsers block raw sockets)
- Exotic hashes not in WebCrypto (MD2/MD4/SHA-3/BLAKE/Whirlpool/GOST Hash/Argon2/Bcrypt/Scrypt/…)
- Heavy parsers (ASN.1/X.509 full, Protobuf schema, AMF, MessagePack, CBOR, YAML, Enigma/Bombe, …)

---

## Impossible without a key (or a header)

Random hex / Base64 of the same length **cannot** be named as AES vs ChaCha vs Salsa vs RSA ciphertext vs a hash. They all look like noise.

Detect will say **high entropy · modern crypto / PRNG** and list that family. It will **not** pick a winner.

Exceptions: a **header** (PEM, Fernet `gAAAAA…`, OpenSSL `Salted__`, JWT) or a **working key** you type in the optional key box.

Hashes are one-way. Analyse hash only matches **length**.
