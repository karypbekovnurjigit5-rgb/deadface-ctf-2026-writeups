# deadface-ctf-2026-writeups
Write-ups for challenges solved during **DEADFACE CTF 2026** (October 17–19, 2026).

**Team result:** Hit #1 in the middle of the competition, finished around top 50.

## Solved Challenges

| Challenge | Category | Points | Status |
|---------|----------|--------|--------|
| DOOM | Bonus | 25 | Solved |
| The Mark | OSINT | 350 | Solved |
| Info Leaks | Mobile | 25 | Solved |
| You Wouldn't Git It | OSINT | 125 | Solved |
| The Vibes Are Freaking Me Out | OSINT | 75 | Solved |
| Do People Still Fax in 2026? | Web / IDOR | 100 | Solved |
| Get That Bag | OSINT / Crypto | 405 | Solved |
| Second Shift | Crypto | 90 | Solved |
| No Holding Back | Mobile | 210 | Solved |
| Down the Rabbit Hole | Mobile | 10 | Solved |

## Write-ups

### 1. DOOM (Bonus – 25 pts)
Simple bonus task. Downloaded `DOOM.zip`, ran it with `gzdoom`, and found the flag painted on the wall at the end of the first level.

### 2. The Mark (OSINT – 350 pts)
Found a post on GhostTown forum from user HAVOC containing leaked emails of Optimus Academy employees. Matched `gabriel.santos@optimusacademy.com` with the lore and identified the full name **Santos Staudenmaier**.

**Flag:** `deadface{Santos_Staudenmaier}`

### 3. Info Leaks (Mobile – 25 pts)
Extracted the IPA file, went into `Payload/aurora-patient-portal.app`, and found the last user’s data in `Info.plist` / SQLite: **Mara Voss**, born **1988-04-17**.

### 4. You Wouldn't Git It (OSINT – 125 pts)
Found GitHub user `fr34ked0ut` and repository `HIPS`. Located a reversed + Base64 encoded string in the extension code. After reversing and decoding got the flag.

**Flag:** `deadface{A11_Th1s_Pr0mpt1ng_G3ts_M3_N0wh3r3!}`

### 5. The Vibes Are Freaking Me Out (OSINT – 75 pts)
Related to the same `HIPS` browser extension. It was using Unicode steganography to hide messages. Flag was found in the extension artifacts.

### 6. Do People Still Fax in 2026? (Web – 100 pts)
Authenticated as `john.smith`. Instead of falling for the SSRF rabbit hole, used **IDOR** by changing the document ID to `1009` and retrieved another user’s medical record containing the flag.

### 7. Get That Bag (OSINT / Crypto – 405 pts)
Used DoomScroll API to get encrypted messages, decoded Unicode (ternary), found references to Santos Staudenmaier and the OathNet leak. Salary data was located in the leaked information.

### 8. Second Shift (Crypto – 90 pts)
Compared plaintext and ciphertext from the archive, recovered the key (XOR / shift), and decrypted the second message.

### 9. No Holding Back (Mobile – 210 pts)
Reversed the APK with `jadx`, found credentials, then exploited **IDOR** on `/api/accounts/{id}/transactions` by enumerating IDs and found the flag in another user’s transactions.

### 10. Down the Rabbit Hole (Mobile – 10 pts)
Extracted the IPA and found a hidden Patient ID (`847261`) in resource files / image metadata.

**Flag:** `deadface{847261}`

---

## Notes

- Only challenges that were successfully solved and scored are included.
- Some challenges involved multi-step OSINT chains and creative steganography.
- Focus areas: OSINT, Mobile, Web (IDOR), and basic Crypto.

Feel free to reach out if you have questions.