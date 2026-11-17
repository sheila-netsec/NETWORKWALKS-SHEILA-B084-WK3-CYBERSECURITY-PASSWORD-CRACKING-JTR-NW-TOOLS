# Module 1 — Password Cracking with John the Ripper (JTR)

## Tools used
- [John the Ripper (jumbo build)](https://www.openwall.com/john/) — password cracking engine
- [Johnny](https://openwall.info/wiki/john/johnny) — GUI front-end for John the Ripper
- [onlinehashcrack.com](https://www.onlinehashcrack.com/) — PDF hash extractor

## Task
Crack the password of the provided locked PDF file (`My Locked PDF1.pdf`) using John the Ripper and the Johnny GUI, on Windows.

## Steps performed

1. Downloaded and extracted John the Ripper (`john-1.9.0-jumbo-1-win64`) — the key executable used is `run/john.exe`.
2. Downloaded and installed **Johnny**, the GUI front-end for John the Ripper.
3. In Johnny, went to **Settings → Browse** and pointed it to `john.exe`. Johnny confirmed: *"Detected John the Ripper 1.9.0-jumbo-1 OMP [cygwin 64-bit x86_64 AVX2 AC]"*.
4. Extracted the crackable hash from the locked PDF using the online PDF Hash Extractor tool — output starts with `$pdf$...`.
5. Pasted the hash into Notepad and saved it as `hash1.txt`.
6. In Johnny, used **Open password file → Open password file (PASSWD format)** and selected `hash1.txt`.
7. Clicked **Start new attack**. John ran through its default bundled wordlist (`password.lst`) and found a match.

## Result

```
Status: 100% (1/1: 1 cracked, 0 left) [format=PDF]
User: ?
Password: good-luck
```

The PDF was then opened and unlocked using password `good-luck`.

## Screenshots

See [`screenshots/`](./screenshots) for:
- Johnny linked to `john.exe` (Settings page, "Detected John the Ripper...")
- Hash extracted from the PDF via onlinehashcrack.com
- Johnny's Passwords tab showing the cracked password

## Notes / learnings

- Johnny requires John's full extracted folder (not just `john.exe` alone), since it depends on supporting files in the `run` directory.
- The hash extracted for a password-protected PDF follows the `pdf2john`/`pdf2hashcat`-compatible format (`$pdf$...`), which John can parse directly once saved in PASSWD format.
- John's default bundled wordlist (`password.lst`) is larger and more effective than a short list of just the "most common" passwords — it's what ultimately found the match.
