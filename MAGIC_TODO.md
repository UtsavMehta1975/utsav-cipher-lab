# Magic Tool master checklist

Track the Cryptography Learning Website Enhancement (Magic Tool + detector). Kitchen catalog lives in [TODO.md](./TODO.md). Architecture: [ANALYSIS.md](./ANALYSIS.md).

## Status

- [x] **TASK 1** — Analyze site → [ANALYSIS.md](./ANALYSIS.md)
- [x] **TASK 2** — Magic Tool UI (ciphertext + optional key, Detect/Magic, confidence, suggestions, plaintext)
- [x] **TASK 3** — Strengthen detection engine (`detectAlgorithm` + CipherDetector; Base45 / Hex Content unwraps)
- [x] **TASK 4** — Integrate engine with Magic Tool UI
- [x] **TASK 5** — CyberChef-like Kitchen recipe/ops panel (Magic in Favourites + Recipe **Magic** button)
- [x] **TASK 6** — Detection → recipe auto-suggest (`Bake in kitchen` + status)
- [x] **TASK 7** — Test & debug (static / JSC smoke: Caesar, Base64, hex, ROT13; Bifid bake path)

## Constraints

- [x] Stay one HTML page (no React/Vue)
- [x] Client-side detection (no server required)
- [x] Match Guptlekh visual language
- [x] Kitchen ops stay in-page (pure JS + WebCrypto + CompressionStream) unless listed under TODO “Needs a library”

## Remaining gaps

- Modern ciphers without header/key still cannot be named (by design) — see TODO.md
- Library/server ops (ChaCha, PGP, Zip, images, HTTP request, exotic hashes, …) stay ghosts
- JWT Sign/Verify is HS* only in-page
- Zlib/Raw Deflate depends on browser `CompressionStream` support
