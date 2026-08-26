# ANALYSIS.md — Guptlekh lab

## Tech stack

| Layer | Choice |
| --- | --- |
| App | Single static `index.html` (HTML + CSS + JS, no build step) |
| Fonts | Google Fonts (loaded in `<head>`) |
| Crypto | Browser `crypto.subtle` (AES-CBC, HMAC, SHA, PBKDF2, JWT HS*) |
| Compression | `CompressionStream` / `DecompressionStream` (gzip, deflate, deflate-raw where supported) |
| Hosting | GitHub Pages–ready (open the file or serve the folder) |

No React, Vue, npm, or backend.

## Files

| File | Role |
| --- | --- |
| `index.html` | Entire product: UI, Detect/Magic, Kitchen, Work (cipher disk), engines |
| `README.md` | How to open / use Read · Kitchen · Work |
| `TODO.md` | Kitchen vs CyberChef catalog (bakeable vs ghosts) |
| `MAGIC_TODO.md` | Master checklist for Magic Tool enhancement |
| `ANALYSIS.md` | This document |

## Page structure (one composition)

1. **Hero / Read (Magic Tool)** — paste unknown text + optional key; Detect/Magic names it; x-ray + Bake in kitchen  
2. **Kitchen** — CyberChef-like four panes: Operations · Recipe · Input · Output  
3. **Work** — spinning cipher disk + Traditional / Modified / Monoalphabetic workshop, logic steps, code, challenges  

Nav jumps: Read · Kitchen · Work · Learn.

## Crypto / detect surfaces

### Read / Magic Tool (`#read`)

- Input: `#detectInput` (ciphertext), `#detectKey` (optional hint)
- Trigger: `#detectBtn` (+ live debounce as you type)
- Engine: `CipherDetector.inspect(raw, hintKey)` → guesses + x-ray trace
- Public API: `window.detectAlgorithm(ciphertext, key?)` → normalized result object
- Actions: Copy · Bake in kitchen · Open on the bench

### Kitchen (`#kitchen`)

- Catalog: ~504 CyberChef names; ~228 implemented in `CHEF_IMPL` (bright); rest ghosts (libs/server)
- `ChefKitchen`: search ops, recipe stack, Auto Bake, Magic op (`CipherDetector` → `loadRecipe`)
- Detect → Kitchen: `CipherLab.openKitchenRecipe(guess)` fills input + recipe

### Work (`#lab` / `#work`)

- Methods: Traditional Caesar, Modified Caesar (keyword stream), Monoalphabetic
- `CipherEngine` for encrypt/decrypt; disk HUD; learn/logic/code boxes

## Detection capabilities (engine)

- Pattern / format: PEM, JWT, Fernet, OpenSSL `Salted__`, Punycode, etc.
- Encodings: Hex, Base64/32/58/85, Morse, URL, HTML entities, quoted-printable, Braille, …
- Classical: Caesar/ROT13 (26), ROT47, Vigenère (word list + hint), Atbash, Affine, Rail Fence, Bacon, …
- Key-assisted: shift, keyword, XOR, AES-CBC passphrase
- Metrics: Shannon entropy, IoC, chi-square; hash **length families** (not a proof)
- Limits: modern bulk ciphertext without header/key → “high entropy · modern crypto / PRNG” family, no false winner

## Design language

Quiet night-terminal bench (Guptlekh / गुप्तलेख): soft panels, mono accents, box labels, teal/sand accents — Magic Tool UI must stay inside that language (enhance Read, do not spawn a second app).
