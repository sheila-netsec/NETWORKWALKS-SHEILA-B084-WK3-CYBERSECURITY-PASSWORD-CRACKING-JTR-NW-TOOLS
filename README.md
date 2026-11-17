# Week 3 — Password Cracking (JTR & Networkwalks Tools)

**Author:** Sheila Chepkoech (B084)
**Program:** Cybersecurity & Ethical Hacking — Networkwalks Training Academy

## Overview

This repository documents Week 3's two project modules, both focused on **password cracking against an encrypted PDF file**, using two different toolchains to reach the same goal:

| Module | Folder | Tools |
|---|---|---|
| Module 1 | [`W3-PM1-JTR`](./W3-PM1-JTR) | John the Ripper (CLI) + Johnny (GUI) — installed locally on Windows |
| Module 2 | [`W3-PM2-NetworkWalks-Tools`](./W3-PM2-NetworkWalks-Tools) | Networkwalks Hash Calculator + Password Cracker — fully browser-based, no installs |

Each folder contains its own write-up and screenshots. See each module's README for full steps.

> ⚠️ **Scope & ethics note:** This was performed against a PDF provided specifically for this training lab, for educational purposes only. Password cracking tools and techniques should only ever be used on systems/files you own or are explicitly authorized to test.

## Key takeaway

Both modules recovered the same password (`good-luck`) from the same locked PDF, but Module 2 showed something Module 1 didn't surface as clearly: a small, 100-password built-in wordlist found **nothing**, while switching to a larger, more realistic wordlist (3,558 words) cracked it almost immediately. This reinforces that in a dictionary attack, **wordlist size and quality matter as much as the tool itself**.

## Skills demonstrated

- Understanding the difference between **encryption** (reversible) and **hashing** (one-way)
- Extracting crackable hashes from protected documents (`pdf2john` / `pdf2hashcat` format)
- Performing **dictionary attacks** using both a dedicated CLI/GUI tool (JTR + Johnny) and browser-based tooling
- Recognizing the limitations of small wordlists and the importance of wordlist size/quality in password auditing
- Practical reinforcement of why strong, unique passwords resist cracking far longer than common/weak ones

## References

- Networkwalks Training Academy — [networkwalks.com](https://www.networkwalks.com)
- John the Ripper documentation — [openwall.com/john](https://www.openwall.com/john/)
