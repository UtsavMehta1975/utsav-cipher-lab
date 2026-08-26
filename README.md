# Guptlekh

**गुप्तलेख** — secret writing, made visible.

A quiet night lab in one page. Paste a string you found. Guptlekh names what it can see. Then you bake it in the kitchen, or work it on a cipher disk.

---

## How to open it

- **On your computer:** open `index.html` in a browser. That is the whole lab.
- **On the web:** host this folder on **GitHub Pages** from the `main` branch. Typical address: [https://utsavmehta1975.github.io/utsav-cipher-lab/](https://utsavmehta1975.github.io/utsav-cipher-lab/)

No install. No login. Stay on this page and jump with **Read**, **Kitchen**, and **Work**.

---

## Three places

### 1. Read

Paste unknown text. Guptlekh tries to name it.

Reading starts as you type. Or press **Read this**.

### 2. Kitchen

A workbench like [CyberChef](https://gchq.github.io/CyberChef/): **operations**, **recipe**, **input**, **output**.

Stack steps. Bake. Copy the result.

### 3. Work

A spinning **cipher disk** plus a workshop.

Three classroom methods:

1. **Traditional Caesar** — every letter jumps the same distance.
2. **Modified Caesar** — a keyword gives a new shift for each letter (the path toward Vigenère).
3. **Monoalphabetic** — one mixed alphabet. A always becomes the same substitute.

Type on the left. Copy from the right. The disk follows.

---

## How Detect + optional key works

In **Read**:

1. Paste into **Unknown text**.
2. Optionally type a **Key**. Leave it empty to guess.
3. Watch the reading. Use a sample button if you want a known example: Caesar, nested, Base64, hex, ROT13, or a hash.

**Magic** peels encodings first (hex, Base64, Morse, and friends). Then it names a classroom cipher if the inner text reads as English.

If you already know the key, Detect tries that **first**:

- a **shift** from 0–25 (Caesar / ROT13)
- a **keyword** (Vigenère / modified Caesar, or a mixed alphabet)
- a repeating **XOR** key
- an **AES** passphrase, if the blob looks like hex ciphertext

You get:

- a best guess, a preview of the decoded text, and a short “why”
- **X-ray** — what Magic actually tried (shifts, encodings, XOR keys, depth)
- **Bake in kitchen** — load that recipe into Kitchen
- **Open on the bench** — drop it onto Work, if it is a classroom cipher
- **Other possibilities** under the main card

Kitchen also has **Magic**. Paste input first, then click Magic. It fills the recipe for you.

---

## What it can name vs what it cannot

**It can name** things with a look, a header, or readable English after a unwrap:

- encodings: Base64, hex, Morse, URL, HTML entities, and similar
- wrappers: PEM, JWT, Fernet (`gAAAAA…`), OpenSSL `Salted__`, bcrypt-style prefixes
- classroom ciphers: Caesar / ROT13, Vigenère, Atbash, Affine, Rail Fence, XOR (when it turns into English)
- hash **length families** (for example 32 hex chars → MD5-sized) — length is a hint, not a proof

**It cannot uniquely name AES vs ChaCha** from random-looking bits. Those (and DES, Blowfish, Salsa20, RSA ciphertext, and more) all look like noise unless there is a **header** or a **working key**.

Kitchen lists many CyberChef names. **Bright** ones bake here. **Faded** ones stay in the catalog. Click a faded name and the bench will say it cannot bake it yet.

AES **does** bake in Kitchen when you give a key (try **Try AES**). Detect will only open AES if you supply that kind of key.

---

## Tiny glossary

| Word | Meaning |
| --- | --- |
| **Cipher** | A rule that hides letters. |
| **Plaintext** | The readable message. |
| **Ciphertext** | The hidden message. |
| **Key** | The secret that sets the rule (a shift, a word, a passphrase). |
| **Encoding** | A writing of the same bytes in another alphabet (Base64, hex). Not a secret by itself. |
| **Bake** | Run the kitchen recipe: each step’s output feeds the next. |
| **Auto Bake** | Kitchen runs the recipe as you type. It is on by default. |
| **Magic** | Auto-unwrap encodings, then guess the classroom cipher. |
| **X-ray** | A list of what Detect actually tried. |
| **Cipher disk** | Two rings: outer = plaintext, inner = ciphertext. Drag or click to set the shift. |
| **Caesar** | One shift for every letter. Only 25 useful keys. |
| **Vigenère** | Repeating keyword shifts. Same idea as Modified Caesar here. |
| **Hash** | A fingerprint of data. You cannot turn it back into the original text. |
| **Entropy** | How “scrambled” the text looks. High often means hash, compression, or modern crypto. |

---

Guptlekh — paste, read, work, copy.
