# Magic Tool master checklist

Track the Cryptography Learning Website Enhancement (Magic Tool + detector). Kitchen catalog lives in [TODO.md](./TODO.md). Architecture: [ANALYSIS.md](./ANALYSIS.md).

## Status

- [x] **TASK 1** — Analyze site → [ANALYSIS.md](./ANALYSIS.md)
- [x] **TASK 2** — Magic Tool UI (ciphertext + optional key, Detect/Magic, confidence, suggestions, plaintext)
- [x] **TASK 3** — Strengthen detection engine (`detectAlgorithm` + CipherDetector; Base45 / Hex Content unwraps)
- [x] **TASK 4** — Integrate engine with Magic Tool UI
- [x] **TASK 5** — CyberChef-like Kitchen recipe/ops panel (Magic in Favourites + Recipe **Magic** button)
- [x] **TASK 6** — Detection → recipe auto-suggest (`Bake in kitchen` + status)
- [x] **TASK 7** — Test & debug (static checks; browser MCP flaky — open `index.html` / Pages to click-test)

## Constraints

- [x] Stay one HTML page (no React/Vue)
- [x] Client-side detection (no server required)
- [x] Match Guptlekh visual language
- [x] Kitchen ops stay in-page (no libs) unless listed under TODO “Needs a library”

## Remaining gaps

- Modern ciphers without header/key still cannot be named (by design) — see TODO.md
- Library/server ops (ChaCha, PGP, Zip, images, HTTP request, …) stay ghosts
- JWT Sign/Verify is HS* only in-page
- Zlib/Raw Deflate depends on browser `CompressionStream` support
- Many catalog ghosts remain (arithmetic sets, exotic hashes, multimedia) — prefer small high-value in-page batches over mega-dumps
