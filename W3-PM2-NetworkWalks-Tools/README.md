# Module 2 — Password Cracking with Networkwalks Tools

## Tools used
- [Networkwalks Hash Calculator](https://networkwalks.com/hash-calculator/) — extracts a crackable hash from a password-protected PDF, entirely in-browser
- [Networkwalks Password Cracker](https://networkwalks.com/password-cracker/) — dictionary attack tool, entirely in-browser

## Task
Recover the password of the same locked PDF file using only free, browser-based Networkwalks tools — no installation required.

## Steps performed

1. Opened the **Hash Calculator**, selected the **PDF** tab, and uploaded the locked PDF.
2. The tool detected the file was encrypted and extracted a crackable hash (`$pdf$4*4*128*-1028*1*16*...`, pdf2john/hashcat-compatible format).
3. Copied the full hash and pasted it into the **Password Cracker**.
4. Ran the attack using the **built-in list (100 passwords)** — result: **"Access Denied — Not cracked with this wordlist."**
5. Reused John the Ripper's own default wordlist from Module 1 (`password.lst`), renamed it to `password.txt`, and uploaded it via **Upload wordlist (.txt)** — giving 3,558 candidate passwords.
6. Re-ran the attack. At 97% progress (3,458/3,558 tried), the tool found a match.

## Result

```
[+] MATCH good-luck ✓
PASSWORD CRACKED SUCCESSFULLY: good-luck
```

Opening the PDF with password `good-luck` unlocked it and revealed the captured flag:

```
Flag: nw{cybersecurity_flag_captured_2608}
```

## Screenshots

See [`screenshots/`](./screenshots) for:
- Hash extracted via the Hash Calculator
- Built-in 100-word list exhausted with no match
- Larger wordlist uploaded and active (`password.txt`, 3,558 words)
- Successful crack and captured flag

## Notes / learnings

- The built-in 100-password list is intentionally small (meant for quick, "most common password" checks) and **was not sufficient** to crack this particular password.
- Reusing JTR's bundled `password.lst` from Module 1 (renamed to a `.txt` extension) worked as a larger, more realistic wordlist — this is a good example of how the *same* wordlist resource can power different cracking tools (CLI or browser-based).
- This mirrors real-world password auditing: short "top N common passwords" lists only catch the weakest passwords; broader wordlists (e.g. `rockyou.txt` or JTR's own lists) are needed to catch moderately weak ones.
